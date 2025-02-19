FROM node:16 as build

WORKDIR /usr/local/app
COPY package*.json ./

RUN npm ci

COPY . .
RUN npm run build
 
FROM nginx:latest as production

COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /usr/local/app/dist/bobapp /usr/share/nginx/html

EXPOSE 80