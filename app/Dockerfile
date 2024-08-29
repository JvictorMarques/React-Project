# Etapa de build
FROM node:18-alpine AS build

WORKDIR /usr/src/app

COPY package.json yarn.lock ./

RUN yarn install --frozen-lockfile

COPY . .

RUN yarn run build && yarn cache clean

# Etapa de produção
FROM node:18-alpine AS prod

WORKDIR /usr/src/app

COPY --from=build /usr/src/app/package.json ./
COPY --from=build /usr/src/app/build ./build
COPY --from=build /usr/src/app/node_modules ./node_modules

EXPOSE 3000

CMD [ "yarn", "run", "start" ]