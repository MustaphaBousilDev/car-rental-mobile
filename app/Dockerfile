# Stage 1: Build the Ionic app
FROM node:20 AS build-stage

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json (if available)
COPY package*.json ./

# Install dependencies
RUN npm install -g @ionic/cli
RUN npm install

# Copy the rest of the app's source code
COPY . .

# Build the Ionic Angular app for production
RUN ionic build --prod

# Stage 2: Serve the app using a simple web server (nginx in this case)
FROM nginx:alpine AS production-stage

# Copy the build output to the nginx html folder
COPY --from=build-stage /app/www /usr/share/nginx/html

# Expose the port NGINX will use
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
