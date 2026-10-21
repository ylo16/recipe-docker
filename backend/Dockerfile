# Use Node.js base image
FROM node:18-alpine
 
# Set working directory inside container
WORKDIR /app
 
# Copy package files first (for better layer caching)
COPY package*.json ./
 
# Install dependencies
RUN npm install
 
# Copy application code
COPY . .
 
# Create directory for the SQLite database file
RUN mkdir -p /app/data
 
# Document the port the backend runs on
EXPOSE 5000
 
# Start the application
CMD ["npm", "start"]