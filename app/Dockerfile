FROM node:18-alpine AS build

WORKDIR /usr/src/app

COPY package.json yarn.lock ./

RUN yarn install

COPY . .

RUN yarn run build && yarn cache clean

FROM node:18-alpine

WORKDIR /usr/src/app

COPY --from=build /usr/src/app/package.json ./
COPY --from=build /usr/src/app/node_modules ./node_modules

ARG port=3000

EXPOSE ${port}

CMD [ "yarn", "run", "start" ]