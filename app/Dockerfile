FROM node:18-alpine

# Set working directory
WORKDIR /usr/src/app

# Copy application configuration and source code
COPY package.json ./
COPY index.js ./

# Expose the application port
EXPOSE 3000

# Run the application as the non-root 'node' user
USER node

# Start the application
CMD ["npm", "start"]
