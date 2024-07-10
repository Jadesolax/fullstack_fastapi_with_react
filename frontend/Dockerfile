# Use the official Node.js image with version 16
FROM node:16

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application files
COPY . .

# Build the application
RUN npm run build

# Install serve to serve the build
RUN npm install -g serve

# Set the environment variable for the API URL
ARG VITE_API_URL
ENV VITE_API_URL=$VITE_API_URL

# Expose port 3000
EXPOSE 3000

# Serve the built application
CMD ["serve", "-s", "dist", "-l", "3000"]
