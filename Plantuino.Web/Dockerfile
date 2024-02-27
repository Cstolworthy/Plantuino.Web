FROM node:18-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm ci
FROM build as copy
COPY . ./
RUN npm run build

FROM node:18-alpine
WORKDIR /usr/app
COPY --from=build /app/src/dist/PROJECT_NAME/server ./
CMD node server.mjs
EXPOSE 4000