# Specify which base image we want to build
FROM node:8

# Copy yarn.lock from local directory to working directory
COPY yarn.lock /yarn.lock

# Copy package.json from local directory to working directory
COPY package.json /package.json

# Set node_modules to root directory of container
ENV NODE_PATH=/node_modules

# Set path to node modules
ENV PATH=$PATH:/node_modules/.bin

# Execute command
RUN yarn

# Set directory as the working directory for RUN, COPY, CMD and etc commands 
WORKDIR /app

# Copy entire local directory to working directory
COPY . /app

# Expose port on which container will listen for
EXPOSE 4000

# Set default command to execute container
CMD yarn start