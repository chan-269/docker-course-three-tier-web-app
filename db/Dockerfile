# Use the official MongoDB image from Docker Hub
FROM mongo:latest

# Set environment variables for MongoDB initialization (optional)
# The default MongoDB image allows the setting of the initial database
ENV MONGO_INITDB_DATABASE=quotesdb

# Optional: If you have an initialization script (e.g., for creating collections or adding sample data),
# you can copy it to the appropriate directory in the container.
# COPY init.js /docker-entrypoint-initdb.d/

# Expose the default MongoDB port (27017)
EXPOSE 27017
