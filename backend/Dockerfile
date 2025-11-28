# backend/Dockerfile
FROM node:18-alpine
WORKDIR /usr/src/app

# If you use npm ci vs install adjust accordingly
COPY package*.json ./
RUN npm ci --only=production

COPY . .
# If you need to build TS -> JS, modify accordingly:
# RUN npm run build

ENV NODE_ENV=production
ENV PORT=3000
EXPOSE 3000
CMD ["node", "server.js"]
