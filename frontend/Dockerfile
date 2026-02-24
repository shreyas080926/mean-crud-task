# Stage 1: Build Angular App
FROM node:18-alpine AS build

# Set working directory
WORKDIR /app

# Set memory limit for build
ENV NODE_OPTIONS="--max_old_space_size=4096"

# Copy package files
COPY package.json package-lock.json* ./

# Install dependencies
RUN npm install --legacy-peer-deps

# Copy all project files (angular.json, tsconfig, src, etc.)
COPY . .

# Build Angular in production mode
RUN npx ng build --configuration production

# Stage 2: Serve with Nginx
FROM nginx:alpine

# Copy the Nginx configuration
COPY nginx/nginx.conf /etc/nginx/conf.d/default.conf

# Copy Angular build output to Nginx web root
COPY --from=build /app/dist/angular-15-crud /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
