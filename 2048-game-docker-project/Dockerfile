#stage 1 : Production Stage ( final image)
FROM ngnix:alpine

#set working directory inside the ngnix
WORKDIR /usr/share/ngnix/html

# copy the built/static files from the build stage
COPY . .

# Expose the default Ngnix port
EXPOSE 80

# start the Nginix server
CMD [ "ngnix", "g", "daemon off;" ]




