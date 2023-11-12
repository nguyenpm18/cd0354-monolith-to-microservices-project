## Build
FROM node:16.20.2 AS build
# Install Ionic CLI
RUN npm install -g @ionic/cli@6
## Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
RUN npm i -f
# Bundle app source
COPY . .
RUN ionic build
## Run
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=build /usr/src/app/www /usr/share/nginx/html