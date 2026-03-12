FROM python:3.11-slim

# Install necessary system packages and Chromium
RUN apt-get update && apt-get install -y \
    wget \
    gnupg \
    ca-certificates \
    apt-transport-https \
    chromium \
    chromium-driver \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# Ensure downloads directory exists
RUN mkdir -p downloads

ENV PYTHONUNBUFFERED=1
# Tell the app it's in a Docker environment
ENV DOCKER_CONTAINER=true

EXPOSE 8000

# Run the application
CMD ["python", "main.py"]
