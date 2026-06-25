# Use Node.js LTS version as the base layer
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package management files first (helps with caching speeds)
COPY package*.json ./
RUN npm install

# Copy the rest of your backend source code
COPY . .

# Expose the port your backend code listens on (usually 5000 or 8080)
EXPOSE 5000

# Start the Node application
CMD ["npm", "start"]