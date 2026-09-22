FROM node:26-alpine AS builder

WORKDIR /app

COPY package.json pnpm-lock.yaml .npmrc ./

RUN npm install -g pnpm@10.15.0

RUN pnpm install

COPY . .

FROM node:26-alpine AS runtime

WORKDIR /app

COPY package.json pnpm-lock.yaml .npmrc ./

RUN npm install -g pnpm@10.15.0

RUN pnpm install --prod

COPY --from=builder /app .

EXPOSE 5000

CMD ["node", "src/index.js"]
