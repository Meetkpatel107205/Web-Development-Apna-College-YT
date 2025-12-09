# Base image
FROM node:18

# Set environment variables (optional, only if used in code)
ENV MONGO_DB_USERNAME=admin \
    MONGO_DB_PWD=qwerty

# Set working directory inside container
WORKDIR /testapp

# Copy package.json first for caching
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application
COPY . .

# Expose port your app uses
EXPOSE 5050

# Start the server
CMD ["node", "server.js"]

# ============================
# DOCKERFILE SYNTAX
# ============================

# FROM node:18
#   -> Specifies the base image your container will start from.
#   -> Examples: node, ubuntu, python, nginx, alpine, mongo.
#   -> This is always the FIRST instruction in a Dockerfile.

# WORKDIR /app
#   -> Sets the working directory inside the container.
#   -> All following commands (COPY, RUN, CMD) run inside this folder.

# COPY . .
#   -> Copies everything from your project folder to the container's working directory.
#   -> Syntax: COPY <source> <destination>
#   -> Example: COPY package.json /app/

# RUN npm install
#   -> Executes commands while building the image.
#   -> Used for installing dependencies or installing OS packages.
#   -> Examples:
#        RUN apt-get update && apt-get install -y python3
#        RUN pip install flask

# ENV KEY=value \
#     ANOTHER=value2
#   -> Sets environment variables inside the container.
#   -> Variables persist at runtime.
#   -> Multi-line ENV uses backslash "\".

# EXPOSE 3000
#   -> Documents the port your container listens on.
#   -> Does NOT publish ports automatically (docker run -p does that).
#   -> Example: EXPOSE 8080

# CMD ["node", "server.js"]
#   -> Default command executed when the container starts.
#   -> JSON array syntax is recommended.
#   -> Only ONE CMD is allowed (last one takes effect).

# ENTRYPOINT ["python3", "main.py"]
#   -> Optional: forces a specific executable to run.
#   -> CMD provides default arguments to ENTRYPOINT.
#   -> Example: ENTRYPOINT ["node"]

# Notes:
# - RUN = executes during image build
# - CMD = executes when the container starts
# - ENTRYPOINT = forces a main executable for the container