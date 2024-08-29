# Use a node image as the base image
FROM node:18-slim as build

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json first
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . /app

# Build the React application
RUN npm run build

# Use a smaller base image to serve the application
FROM node:18-slim

# Install `serve` globally
RUN npm install -g serve

# Set the working directory inside the container
WORKDIR /app

# Copy the built application from the build stage
COPY --from=build /app/build /app/build

# Expose the port that the application will run on
EXPOSE 3000

# Specify the command to serve the application
CMD ["serve", "-s", "build", "-l", "3000", "--single"]
