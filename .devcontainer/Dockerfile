# Use a base image with R pre-installed (e.g., rocker/r-ver)
FROM rocker/r-ver:latest

# Install system dependencies for R and RStudio
RUN apt-get update && apt-get install -y \
    sudo \
    gdebi-core \
    pandoc \
    pandoc-citeproc \
    libcurl4-gnutls-dev \
    libcairo2-dev \
    libxt-dev \
    libssl-dev \
    libssh2-1-dev \
    && rm -rf /var/lib/apt/lists/*

# Download and install RStudio Server
RUN wget -q https://download2.rstudio.org/server/bionic/amd64/rstudio-server-1.4.1106-amd64.deb \
    && gdebi -n rstudio-server-1.4.1106-amd64.deb \
    && rm rstudio-server-1.4.1106-amd64.deb

# Expose the port RStudio Server runs on
EXPOSE 8787

# Use init to handle system signals
ENTRYPOINT ["/usr/lib/rstudio-server/bin/rserver", "--server-daemonize=0"]
