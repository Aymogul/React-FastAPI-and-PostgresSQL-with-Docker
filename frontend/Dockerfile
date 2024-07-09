# Use a more recent Node.js runtime as a parent image
FROM node:18-alpine

# Set the working directory in the container
WORKDIR /app

# Copy the package.json and package-lock.json files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code into the container
COPY . .

# Expose the port that the app runs on
EXPOSE 5173

# Command to run the development server with --host
CMD ["npm", "run", "dev", "--", "--host"]