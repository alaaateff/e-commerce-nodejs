ARG image_version=lts-alpine3.23
FROM node:${image_version} AS base
WORKDIR /docker
COPY "app/e-commerce-nodejs/package.json" ./
COPY "app/e-commerce-nodejs/package-lock.json" ./
COPY "app/e-commerce-nodejs/package-lock.json" ./
#COPY "app/e-commerce-nodejs/E-Commerce Node.js API.postman_collection.json" ./
RUN npm install
COPY "app/e-commerce-nodejs/Controllers" ./Controllers
COPY "app/e-commerce-nodejs/Database" ./Database
COPY "app/e-commerce-nodejs/Middlewares" ./Middlewares
COPY "app/e-commerce-nodejs/Models" ./Models
COPY "app/e-commerce-nodejs/public" ./public
COPY "app/e-commerce-nodejs/Routes" ./Routes
COPY "app/e-commerce-nodejs/Utils" ./Utils
COPY "app/e-commerce-nodejs/.env.example" ./
COPY "app/e-commerce-nodejs/server.js" ./
CMD ["npm" , "start"]
