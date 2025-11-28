# frontend/Dockerfile
# Build stage
FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
ARG NG_ENV=production
ENV NODE_ENV=$NG_ENV
RUN npm run build -- --configuration=production

# Production stage - nginx serves built files
FROM nginx:1.23-alpine
COPY --from=build /app/dist /usr/share/nginx/html
# Remove default conf and copy our frontend-only config (optional)
#RUN rm /etc/nginx/conf.d/default.conf
#COPY nginx-frontend.conf /etc/nginx/conf.d/frontend.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
