## Build
FROM node:16 AS ionic

RUN npm install -g @ionic/cli
WORKDIR /usr/src/app
COPY package*.json ./

RUN npm install -f
COPY . .
RUN NODE_OPTIONS=--openssl-legacy-provider && ionic build
FROM nginx:alpine
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html
