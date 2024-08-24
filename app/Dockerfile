FROM node:18-alpine AS build

WORKDIR usr/src/app .

COPY package.json yarn.lock ./

RUN yarn install

COPY . .

RUN yarn run build

FROM node:18-alpine

WORKDIR usr/src/app .

COPY --from=build /usr/src/app ./package.json
COPY --from=build /usr/src/app ./node_modules

EXPOSE 3000

CMD [ "yarn", "run", "start" ]