FROM node:alpine as builder
WORKDIR /app
COPY ./package.json .
RUN npm install 
COPY . . 
CMD npm run build

FROM nginx
EXPOSE 80
COPY --from=builder /app/dist /usr/share/nginx/html
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf