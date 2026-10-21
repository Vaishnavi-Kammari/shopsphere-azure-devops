
# Stage 1: Build the React application
FROM node:22-alpine AS builder

WORKDIR /app

# Copy dependency manifests first for better layer caching
COPY package*.json ./
RUN npm ci

# Copy the frontend source and Vite configuration
COPY . .

ARG VITE_API_BASE_URL=/api
ENV VITE_API_BASE_URL=$VITE_API_BASE_URL

# Generate production files in /app/dist
RUN npm run build

# Stage 2: Serve the static frontend
FROM nginx:alpine

# Remove the default Nginx website
RUN rm -rf /usr/share/nginx/html/*

# Add our Nginx configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copy the built React application
COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
