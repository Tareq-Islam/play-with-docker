FROM node:latest as build-stage
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
RUN npm run aot
RUN npm run production

FROM nginx:latest as production-stage

COPY --from=build-stage /app/dist/hello-world/browser /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
