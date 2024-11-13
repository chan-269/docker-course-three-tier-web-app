
FROM python:3.11-slim

WORKDIR /api

# Install necessary dependencies (no Mongo, but some basic packages)
RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y gcc pkg-config libssl-dev libcurl4-openssl-dev libsasl2-dev \
    && rm -rf /var/lib/apt/lists/*

# Copy the Python dependencies file first to leverage Docker cache layers
COPY requirements.txt ./ 

# Copy the application code
COPY . .

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Expose the port that your app will run on
EXPOSE 5001

# Set the default command to run the app (update to match your application entry point)
CMD ["python", "api.py"]
