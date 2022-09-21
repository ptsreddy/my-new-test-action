FROM softonic/node-prune AS prune

FROM node:14.9-slim AS build
ENV NODE_ENV dev
WORKDIR /app
COPY --from=prune /go/bin/node-prune /usr/local/bin/
ADD . .
RUN npm install

FROM node:14.9-slim
ENV NODE_ENV dev
WORKDIR /app
COPY --from=build /app .
ADD . .
EXPOSE 8080
CMD ["node", "server.js"]
