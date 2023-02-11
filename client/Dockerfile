FROM node

# Set the working directory
WORKDIR .

# Copy the package.json and package-lock.json
COPY package*.json ./

# Install the dependencies
RUN npm install

# Copy the rest of the application's files
COPY . .

# Build the application
RUN npm run build

# Expose the port
EXPOSE 4200

# Start the application
CMD ["npm", "start"]