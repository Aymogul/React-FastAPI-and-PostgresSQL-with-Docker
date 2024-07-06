# Use the Node.js 16 image
FROM node:16-alpine

# Set the working directory
WORKDIR /app/frontend

# Copy package.json and package-lock.json (if exists)
COPY package*.json ./

# Configure npm to use a different registry
RUN npm config set registry https://registry.npmjs.org/

# Install npm packages
RUN npm install --silent

# Copy the rest of the application
COPY . .

# Build the application
RUN npm run build

# Expose the port
EXPOSE 3000

# Start the application
CMD ["npm", "start"]