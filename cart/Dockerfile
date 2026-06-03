## Build stage

FROM    node:18-alpine as build
WORKDIR /opt/app
COPY    package.json ./
RUN     npm install --silent
COPY    . .  

## Run stage
FROM gcr.io/distroless/nodejs18-debian12
ENV INSTANA_AUTO_PROFILE true
WORKDIR /opt/app
COPY --from=build /opt/app /opt/app
EXPOSE  8080    
CMD     ["server.js"]

