FROM node:18 AS build

WORKDIR /app
COPY . ./
RUN npm install && npm run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

# Override default config to ensure it listens on port 8080
RUN echo 'server { listen 8080; root /usr/share/nginx/html; index index.html; try_files $uri /index.html; }' > /etc/nginx/conf.d/default.conf

EXPOSE 8080
CMD ["nginx", "-g", "daemon off;"]
