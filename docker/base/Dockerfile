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
