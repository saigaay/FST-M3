## BUILD PHASE
# Base image
FROM node:alpine as builder
# Switch workdir to '/usr/app'
WORKDIR /usr/app
# Copy package.json into
# the container
COPY package.json .
# Install all the deps
RUN npm install
# Copy the rest of the
# files into the container
COPY . .
# Build the production files
RUN npm run build
## RUN PHASE
# Base image
FROM node:alpine as prod
WORKDIR /usr/app
# Copy over the production files
COPY --from=builder usr/app .
RUN node /usr/app/dist/server.js