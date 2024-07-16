# Stage 1: Build Stage
FROM node:20.15.1 AS build-stage

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY frontend/package*.json ./

# Install dependencies
RUN npm install

# Copy all files
COPY . .

# Build the application
RUN npm run build --verbose

# Stage 2: Production Stage
FROM nginx:stable-alpine AS production-stage

# Copy built assets from build-stage
COPY --from=build-stage /app/dist /usr/share/nginx/html

# Copy custom nginx configuration if you have one
# COPY nginx.conf /etc/nginx/nginx.conf

# Expose port
EXPOSE 80

# Start nginx server
CMD ["nginx", "-g", "daemon off;"]






#--------------SINGLE STAGE BUILD-------------------------------

# # Use the official Node.js image with version 16
# FROM node:16

# # Set the working directory
# WORKDIR /app

# # Copy package.json and package-lock.json files
# COPY package*.json ./

# # Install dependencies
# RUN npm install

# # Copy the rest of the application files
# COPY . .

# # Build the application
# RUN npm run build

# # Install serve to serve the build
# RUN npm install -g serve

# # Set the environment variable for the API URL
# ARG VITE_API_URL
# ENV VITE_API_URL=$VITE_API_URL

# # Expose port 3000
# EXPOSE 3000

# # Serve the built application
# CMD ["serve", "-s", "dist", "-l", "3000"]
