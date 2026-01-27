# Use a slim Python image
FROM python:3.11-slim

# Install system dependencies (Graphviz is required for diagrams)
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    graphviz \
    git \
    && rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /app

# Copy the current directory (which contains the diagrams library source and our server code)
COPY . /app

# Install the diagrams library from source (current dir) and other requirements
# We install 'mcp' explicitly as it might not be in the local repo's requirements
RUN pip install --no-cache-dir . mcp

# Create an output directory for persistence if volume is mounted
RUN mkdir -p /app/output

# Run the MCP server using absolute path
CMD ["python", "/app/src/server.py"]
