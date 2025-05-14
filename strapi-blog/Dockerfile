# Use the official Node.js runtime as the base image
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Clear npm cache and install dependencies
# Use npm install instead of npm ci to handle lock file issues
RUN npm cache clean --force && \
    npm install --omit=dev

# Copy the entire application code
COPY . .

# Create necessary directories and set permissions
RUN mkdir -p /app/public/uploads && \
    chown -R node:node /app && \
    chmod -R 755 /app

# Switch to non-root user for security
USER node

# Build the application
RUN npm run build

# Expose the port Strapi will run on
EXPOSE 1337

# Set environment to production
ENV NODE_ENV=production

# Start the application
CMD ["npm", "run", "start"]