FROM node:24-alpine3.24 AS deps

WORKDIR /app

COPY package*.json ./
RUN npm install

FROM node:24-alpine3.24 AS builder

WORKDIR /app

COPY --from=deps /app/node_modules ./node_modules
COPY src ./src
COPY tsconfig.json ./
COPY package.json ./

RUN npm run build

CMD ["node", "dist/index.js"]

FROM node:24-alpine3.24 AS main

WORKDIR /app

COPY --from=builder /app/dist ./dist
COPY package.json ./

RUN npm install --omit=dev

CMD ["node", "dist/index.js"]