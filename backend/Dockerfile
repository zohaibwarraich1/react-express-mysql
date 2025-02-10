FROM node:latest AS build

WORKDIR /app

COPY ./package*.json ./

RUN npm install

COPY ./ ./

FROM node:alpine

WORKDIR /app

COPY --from=build /app /app

EXPOSE 5000

CMD ["npm","start"]

