# Stage 1
FROM node:22 AS backend-builder

# setup the working dir
WORKDIR /app

#code 
COPY . .

RUN npm i

# Stage 2
FROM node:22-slim

# setup the working dir
WORKDIR /app

# copy the above stage as compressed
COPY --from=backend-builder /app .

COPY .env.sample .env

# Port
EXPOSE 5000

# App
CMD ["npm", "start"]

