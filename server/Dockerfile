FROM node:latest as be
WORKDIR /usr/app

# Install dependencies and build the project.
COPY package.json package-lock.json ./
RUN npm install
COPY . .
RUN npm run build

# Run the web service on container startup.
CMD ["node", "dist/server.js"]


#docker build -t be .    