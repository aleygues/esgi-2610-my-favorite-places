FROM node:24-alpine3.24

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY tsconfig*.json ./
COPY vite.config.ts ./
COPY public ./public
COPY index.html ./
COPY src ./src

RUN npm run build

CMD ["npx", "serve", "dist"]