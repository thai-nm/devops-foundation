FROM node:16-alpine3.17 AS build
COPY . .
RUN npm install
RUN npm run build


FROM nginx:1.22 AS deploy
WORKDIR /app
COPY --from=build dist /app/
COPY nginx.conf /etc/nginx/nginx.conf
CMD [ "nginx", "-g", "daemon off;" ]