FROM node:16 AS builder
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build


FROM nginx:alpine
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d 
WORKDIR /usr/share/nginx/html
COPY --from=builder /app/build .
CMD ["nginx", "-g", "daemon off;"]