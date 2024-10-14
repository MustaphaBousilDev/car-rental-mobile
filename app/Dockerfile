FROM node:17-alpine AS builder

# Create app directory
RUN mkdir -p /app
WORKDIR /app

# Install app dependencies by copying package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm ci

# Bundle app source
COPY . .

# Set arguments and env variables
ARG arg1
ARG arg2


ENV ARG1=${arg1}
ENV ARG2=${arg2}


# Build the application
RUN npm run build

# Remove unnecessary packages
RUN npm prune --production
