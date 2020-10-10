# Using image from npm

FROM node:alpine AS builder

# Bundle everything inside an application folder

WORKDIR /app

# Copy every file of our local application folder towards the bundle folder inside the Docker container

COPY . .

# Delete node_modules, install dependencies with exact version according to package_lock.json AND build the application

RUN npm ci && npm run build

# Web server for displaying the application. Using Nginx (engine x) to display the static content of the dist folder.

FROM nginx:alpine

# Copies the static application files inside the dist folder into the HTML folder that the web server will serve

COPY --from=builder /app/dist/app /usr/share/nginx/html

# Application will be running at exposed port

EXPOSE 80