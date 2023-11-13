# Use an official Ubuntu runtime as a base image
FROM ubuntu:20.04

# Install necessary dependencies
RUN apt-get update && \
    apt-get install -y \
    python3 \
    python3-pip \
    git

# Clone the Spectre API GitLab repo
RUN git clone https://gitlab.com/spectre.app/api.git /opt/spectre-api

# Set the working directory
WORKDIR /opt/spectre-api

# Create a virtual environment
RUN python3 -m venv /opt/spectre-api/venv

# Activate the virtual environment
ENV PATH="/opt/spectre-api/venv/bin:${PATH}"

# Install Python dependencies
COPY requirements.txt /opt/spectre-api/
RUN pip3 install -r requirements.txt

# Copy configuration file
COPY spectre-api-config.tmpl /opt/spectre-api/

# Expose any necessary ports
# EXPOSE ...

# Command to run the application (adjust as needed)
CMD ["python3", "app.py"]
