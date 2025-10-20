FROM node:20-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# Declare build argument
ARG VITE_API_URL

# Export it so Vite can pick it up at build time
ENV VITE_API_URL=$VITE_API_URL

# Build the React app
RUN npm run build

EXPOSE 5173
CMD ["npm", "run", "preview"]
