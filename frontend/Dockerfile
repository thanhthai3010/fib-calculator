FROM node:alpine as builder
WORKDIR "/app"
COPY ./package.json .
RUN npm install
COPY . .
RUN npm run build

# Create new image
FROM nginx
EXPOSE 3000
COPY ./nginx/default.cnf /etc/nginx/conf.d/default.cnf
COPY --from=builder /app/build /usr/share/nginx/html