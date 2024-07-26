# Use a node image as a parent image
FROM node:18-slim

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build your React application
RUN npm run build

# Specify the command to run your React application
CMD ["npm", "start"]
