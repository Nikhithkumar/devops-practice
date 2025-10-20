FROM node:20-alpine
# Use the official Node.js 20 image based on Alpine Linux for a small
# and secure base image. Alpine keeps the image size small which is
# helpful for faster builds and deployments.

WORKDIR /app
# Set the working directory inside the container to /app. All subsequent
# commands (COPY, RUN, CMD, etc.) will be relative to this directory.

# Copy package.json and package-lock.json (if present). Using the
# wildcard pattern `package*.json` ensures both files are copied when
# available. This is done before copying the full source to take
# advantage of Docker layer caching for npm install.
COPY package*.json ./

RUN npm install
# Install production and development dependencies defined in package.json.
# Because package.json was copied in the previous step, Docker can cache
# this layer unless package.json changes, which speeds up rebuilds.

# Copy the rest of the application source code into the container.
# This includes server.js, controllers, models, routes, and any other
# files needed to run the server.
COPY  . .

EXPOSE 5000
# Document the port the application listens on. This does not publish the
# port by itself but serves as metadata; use `-p 5000:5000` with `docker run`
# to map it to the host.

CMD ["node", "server.js"]
# Start the Node.js application by running server.js. Use this as the
# container's default command when it is started.