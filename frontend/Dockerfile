# Stage 1: Build the production app
FROM node:18-alpine
 
WORKDIR /app
 
# Copy package files
COPY package*.json ./
 
# Install dependencies
RUN npm install
 
# Copy all application files
COPY . .
 
# Vite bakes VITE_* variables in at build time, so accept it here
ARG VITE_API_URL=http://localhost:5000
ENV VITE_API_URL=$VITE_API_URL
 
# Build the production application
RUN npm run build
 
# Stage 2: Serve the built files with nginx
FROM nginx:alpine
COPY --from=0 /app/dist /usr/share/nginx/html
 
# nginx default port
EXPOSE 80
 
# Start nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]