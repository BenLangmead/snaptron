# Use an official Python runtime as a base image
FROM debian

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
ADD . /app

# Install basics
RUN apt-get update && apt-get install -y \
    python2.7 \
    python-dev \
    python-pip \
    tabix \
    sqlite3 \
    curl \
    wget \
    openjdk-7-jdk \
    ant

# Install any needed packages specified in requirements.txt
RUN pip install -r requirements.txt

# Install PyLucene
RUN sh docker_install_pylucene.sh

# Get data and install indexes 
RUN sh docker_deploy_snaptron.sh srav1 1

# Make Snaptron ports visible outside this container
EXPOSE 1555 1556 1557 1558 1580

# Run Snaptron server as daemon
RUN python srav1_snaptron_server
