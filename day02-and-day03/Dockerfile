FROM node:25-alpine3.21 AS installer

WORKDIR /app

COPY package*.json .

RUN npm install --legacy-peer-deps

COPY . .

RUN npm run build


FROM nginx:latest AS deployer

COPY --from=installer /app/dist /usr/share/nginx/html

EXPOSE 80

ENTRYPOINT ["nginx", "-g", "daemon off;"]

