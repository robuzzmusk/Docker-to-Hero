FROM ubuntu:20.04

# Set environment variables to avoid interactive prompts during build
ENV DEBIAN_FRONTEND=noninteractive

WORKDIR /app

# Copy requirements.txt and other necessary files first to leverage Docker cache
COPY requirements.txt /app/

# Install dependencies
RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    pip3 install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY devops /app/devops

# Set the working directory to /app/devops
WORKDIR /app/devops

# Set the default command to run the Django application
ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]





