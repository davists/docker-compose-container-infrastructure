FROM node:carbon

MAINTAINER Davi dos Santos

# Install PM2
RUN npm install -g pm2

# Define working directory
WORKDIR /usr/src/app

ADD . /usr/src/app

#RUN npm install

# Expose port
EXPOSE 3000

# Run app
CMD pm2 start --no-daemon process.json
