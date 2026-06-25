FROM node:18-alpine AS base

WORKDIR /app/streamingService

COPY streamingService/package*.json ./
RUN npm install --production

COPY package*.json ./
ENV NODE_ENV=production
EXPOSE 3002

CMD ["npm", "run", "start"]
