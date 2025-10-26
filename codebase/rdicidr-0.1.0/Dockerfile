FROM node:15 AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM node:15-alpine

WORKDIR /app

COPY --from=builder /app/build ./build

RUN npm install -g serve

ENTRYPOINT ["serve", "-s", "build", "-l", "8080"]
