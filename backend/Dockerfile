# Use a pinned LTS version for security
FROM node:18-alpine

# Create app directory
WORKDIR /app

# Add a non-root user and switch to it
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser

# Copy only required files first to leverage caching
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy the rest of the application code
COPY . .

# Expose the backend port
EXPOSE 9000

# (Optional) Add container healthcheck
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
  CMD wget -qO- http://localhost:9000/health || exit 1

# Start the app
CMD ["npm", "start"]
