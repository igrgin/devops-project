FROM python:3.8-slim

# Create a non-root user and group
RUN groupadd -r appgroup && useradd -r -g appgroup appuser

# Set the working directory
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . .

# Update packages and install dependencies
RUN apt-get update && apt-get install -y gcc \
    && pip install --upgrade pip \
    && pip install -r requirements.txt

# Change ownership of the /app directory to the non-root user
RUN chown -R appuser:appgroup /app

# Switch to the non-root user
USER appuser

# Expose port 5000 for the Flask app
EXPOSE 5000

# Command to run the Flask app
CMD ["python", "app.py"]

