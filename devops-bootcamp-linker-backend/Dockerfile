# ---- Build stage ----
FROM node:slim AS builder
#RUN mkdir app
WORKDIR /app

RUN apt-get update && apt-get install -y python3 build-essential \
    && rm -rf /var/lib/apt/lists/*

COPY package*.json ./
RUN npm ci

COPY . . 

#Generate prisma client
RUN npx prisma generate

RUN npm run build


# ---- Production stage ----
FROM node:slim AS runner
WORKDIR /app

RUN apt-get update && apt-get install -y openssl curl \
    && rm -rf /var/lib/apt/lists/*

COPY --from=builder /app/node_modules /app/node_modules
COPY --from=builder /app/dist ./dist

#USER node

EXPOSE 3001
CMD ["node", "dist/main.js"]
