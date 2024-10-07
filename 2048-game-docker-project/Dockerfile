# stage1 : Build stage
FROM ubuntu:20.04 AS build

# Install node.js and 
RUN apt-get update && apt-get install -y curl 
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs

# verify installation of node and npm
RUN node -v && npm -v

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
COPY --from=build /2048-app/build/ .

# Expose the default Ngnix port
EXPOSE 80

# start the Nginix server
CMD [ "ngnix", "g", "daemon off;" ]




