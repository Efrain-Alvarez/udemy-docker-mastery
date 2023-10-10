# use this empty Dockerfile to build your assignment

#you should use the `node` official image, with the alpine 6.x branch (`node:6-alpine`)
#all images must have a from, using the offical image and specified version
FROM node:6-alpine

#This app listens on port 3000, but the container should listen on port 80 of the Docker host, so it will respond to [http://localhost:80](http://localhost:80) on your computer
#exposes port 3000 per the instructions, later will need to publish port 80 for local host
EXPOSE 3000 

#Then it should use the alpine package manager to install tini: `apk add --no-cache tini`.
#set of run commands 
#install of appilcation tini
RUN  apk add --no-cashe tini 
#create directory for app files 
RUN mkdir -p /usr/src/app

#Then it should create directory /usr/src/app for app files with `mkdir -p /usr/src/app`, or with the Dockerfile command `WORKDIR /usr/src/app`.
WORKDIR /usr/src/app
#Node.js uses a "package manager", so it needs to copy in package.json file.
COPY package.json package.json

#Then it needs to run 'npm install' to install dependencies from that file.
#To keep it clean and small, run `npm cache clean --force` after the above, in the same RUN command.
#install nmp and clean up, best practice is to have the install and the clean up on the same line

RUN npm install 
#Then it needs to copy in all files from current directory into the image.
#this copys everything in the current directory on host to current working directory in the image
COPY . .

#Then it needs to start the container with the command `/sbin/tini -- node ./bin/www`. Be sure to use JSON array syntax for CMD. (`CMD [ "something", "something" ]`)
CMD [ "/sbin/tini","--","node","./bin/www" ]
# NOTE: The instructions are now in the README.md file in this directory.
