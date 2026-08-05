FROM ubuntu:24.04

# Prevent interactive prompts during apt installations
ENV DEBIAN_FRONTEND=noninteractive
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8

# Install Ruby, Bundler, and build dependencies
RUN apt-get update && apt-get install -y \
    ruby-full \
    ruby-bundler \
    build-essential \
    zlib1g-dev \
    libyaml-dev \
    git \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory inside the container
WORKDIR /site

# Copy only the Gemfile (and Gemfile.lock if it exists) into the container
COPY Gemfile* ./

# Install the gems directly into the Docker image
RUN bundle install

# Expose Jekyll's default port (4000) and LiveReload port (35729)
EXPOSE 4000 35729