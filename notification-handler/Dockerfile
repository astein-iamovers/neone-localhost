# Use Python image
FROM python:3.9-slim

# Set the working directory
WORKDIR /app

# Copy the current directory contents into the container
COPY . .

# Install dependencies
RUN pip install flask

# Expose the Flask app port
EXPOSE 5000

# Run the application
CMD ["python", "app.py"]
