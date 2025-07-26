FROM node:18-alpine

WORKDIR /app

# Copy dependency files first
COPY package*.json ./

# Install dependencies as root
RUN npm install --production

# Copy the rest of the code
COPY . .

# Create and switch to non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup && \
    chown -R appuser:appgroup /app
USER appuser

EXPOSE 9000

HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
  CMD wget -qO- http://localhost:9000/health || exit 1

CMD ["npm", "start"]
