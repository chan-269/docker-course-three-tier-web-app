# Use the official MongoDB image from Docker Hub
FROM mongo:latest

# Set environment variables for MongoDB (optional)
# MongoDB has no equivalent to MySQL's user/password setup, but we can set the database name if needed
ENV MONGO_INITDB_DATABASE=quotesdb

# Optional: If you need an initialization script (for example, adding collections or documents)
# COPY init.js /docker-entrypoint-initdb.d/

# Expose the default MongoDB port (27017)
EXPOSE 27017
