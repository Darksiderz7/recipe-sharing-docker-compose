# Use a lightweight Node.js 18 image
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package files into the container
COPY package*.json ./

# Install the backend dependencies
RUN npm install

# Copy the remaining backend files
COPY . .

# Create a directory for the SQLite database
RUN mkdir -p /app/data

# Expose the backend port
EXPOSE 5000

# Start the backend application
CMD ["npm", "start"]