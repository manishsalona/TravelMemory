# Stage 1: Build the React application
FROM node:18-alpine AS build

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy the entire app to the container
COPY . .

# Build the React app for production
RUN npm run build

# Stage 2: Serve the React app with Node.js
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy the build from the previous stage
COPY --from=build /app/build /app/build

# Install production dependencies
COPY package*.json ./
RUN npm install --production

# Expose port 3001
EXPOSE 3001

# Start the application
CMD ["npm", "start"]
