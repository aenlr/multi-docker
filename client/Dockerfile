FROM node:alpine AS builder

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY public public
COPY src src
RUN npm run build

FROM nginx:latest
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/
COPY --from=builder /app/build /usr/share/nginx/html
