# Etapa 1: Build da aplicação React com Vite
FROM node:18-alpine AS build
WORKDIR /app

COPY package.json yarn.lock ./
RUN yarn install

COPY . .
RUN yarn build


FROM nginx:alpine AS final

COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]