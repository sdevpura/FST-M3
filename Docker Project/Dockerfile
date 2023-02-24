# --------BUILD PHASE-----
# Base Image
FROM node:16-alpine as builder

# Change workdir to '/usr/app'
WORKDIR /usr/app

# Copy package.json into the
# container
COPY package.json .

# Install dependencies
RUN npm install

# Copy the rest of the files
# into the container
COPY . .

# Run this
RUN npm run build

# -----------RUN PHASE-----
# Base Image
FROM node:16-alpine

# Change workdir to '/usr/app'
WORKDIR /usr/app

# Copy package.json into the
# container
COPY package.json .

# Install dependencies
RUN npm install

# Copy the rest of the files
# into the container
COPY --from=builder /usr/app/dist /usr/app

# Run this
CMD ["node", "server.js"]