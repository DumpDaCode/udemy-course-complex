FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json .
RUN npm install 
COPY . . 
RUN npm run build
RUN ls

FROM nginx
EXPOSE 80
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html