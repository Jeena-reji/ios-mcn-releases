# Use Alpine Linux as a lightweight base image
FROM alpine:latest

# Set the working directory
WORKDIR /

# Create necessary directories
RUN mkdir -p /Sphinx/build

# Install dependencies: Python, Pip, Make, and Git
RUN apk add --no-cache python3 py3-pip make git

# Install Sphinx and required packages
RUN pip3 install git+https://github.com/sphinx-doc/sphinx --break-system-packages && \
    pip3 install sphinx-autobuild --break-system-packages

# Add the documentation dependencies file
ADD ./documentation/requirements-docs.txt /Sphinx

# Install the required Python dependencies for Sphinx
RUN pip3 install -r /Sphinx/requirements-docs.txt --break-system-packages

# Run the Sphinx autobuild server to generate & serve the docs
CMD sphinx-autobuild -b html -n --host 0.0.0.0 --port 80 /Sphinx/source /Sphinx/build
