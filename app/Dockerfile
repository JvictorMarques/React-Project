FROM node:18-alpine AS build

WORKDIR /usr/src/app

COPY package.json yarn.lock ./

RUN yarn

COPY . .

RUN yarn run build && yarn cache clean

FROM node:18-alpine AS prod

WORKDIR /usr/src/app

# COPY --from=build /usr/src/app/package.json ./
# COPY --from=build /usr/src/app/node_modules ./node_modules
COPY . .

EXPOSE 3000

CMD [ "yarn", "run", "start" ]