# Use Node.js to build the frontend
FROM node:18-alpine

# Set the working directory
WORKDIR /app

# Copy the package files
COPY package*.json ./

# Install frontend dependencies
RUN npm install

ARG VITE_API_URL
ENV VITE_API_URL=$VITE_API_URL

# Copy the frontend application files
COPY . .

# Build the production application
RUN npm run build

# Use nginx to serve the built application
FROM nginx:alpine

# Copy the production build into nginx
COPY --from=0 /app/dist /usr/share/nginx/html

# Expose the nginx port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
