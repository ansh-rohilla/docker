FROM node:18-alpine AS installer
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:alpine AS deployer
COPY --from=installer /app/build /usr/share/nginx/html
EXPOSE 80