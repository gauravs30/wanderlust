# ------------- Stage 1: Build Stage ----------
FROM node:22 AS frontend-builder

# Set the working directory to /app
WORKDIR /app

# Copy the package.json and package-lock.json for dependency installation
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# ------------- Stage 2: Final Stage ----------
FROM node:22-slim

# Set the working directory to /app
WORKDIR /app

# Copy built assets and dependencies from frontend-builder stage
COPY --from=frontend-builder /app .

# Copy the .env.sample file to .env.local
COPY .env.sample .env.local

# Expose port 5173 for the Node.js app
EXPOSE 5173

# Define the default cmd to run app in dev
CMD ["npm", "run", "dev", "--", "--host"]

