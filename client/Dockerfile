FROM node:latest AS fe

WORKDIR /usr/src/app
COPY package.json package-lock.json ./

# Install dependencies and copy them to the container
RUN npm install
COPY . .

# Build the Angular application for production
RUN npm run build --prod

# Configure the nginx web server
FROM nginx:latest
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=fe /usr/src/app/dist/client /usr/share/nginx/html

# Run the web service on container startup.
CMD ["nginx", "-g", "daemon off;"]



#docker build -t fe .    