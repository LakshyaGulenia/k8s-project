# Use the official Python base image for simplicity
FROM python:3.12-slim

# Set the working directory inside the container
WORKDIR /app

# Copy application files and requirements
COPY requirements.txt /app
COPY devops /app

# Install system dependencies and Python dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends gcc libpq-dev && \
    pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir -r requirements.txt && \
    apt-get remove -y gcc && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/* && \
    cd devops
# Set the entry point and default command
ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]

