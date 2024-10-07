# stage1 : Build stage
FROM node:18-alpine AS build

# set working directory inside the build container
WORKDIR /2048-app

# copy the game source files into the container
COPY . /2048-app/

RUN npm install
RUN npm run build

#stage 2 : Production Stage ( final image)
FROM ngnix:alpine

#set working directory inside the ngnix
WORKDIR /usr/share/ngnix/html

# copy the built/static files from the build stage
COPY --from=build /2048-app/ .

# Expose the default Ngnix port
EXPOSE 80

# start the Nginix server
CMD [ "ngnix", "g", "daemon off;" ]




