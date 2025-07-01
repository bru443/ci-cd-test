FROM node:18 AS build

WORKDIR /app
COPY frontend/ ./
RUN npm install && npm run build

# Serve build with a lightweight HTTP server
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
