# docker build -t plunder.stercus.de/hosting/simulation:instructor -f Dockerfile.instructor .

### HINTS
### Sometimes you can get building errors related to cache handling.
### One of the following usually helps:
### (1) Use the '--no-cache' option
###     > docker build ... --no-cache
### (2) Purge the builder cache before and/or between builds
###     > docker builder prune
### (3) Re-open the terminal and/or Visual Studio Code
### (4) Remove the line containing 'rm -rf /var/lib/apt/lists/*'
###     from your extending Dockerfile (like this one)

ARG BASEIMAGE="accetto/ubuntu-vnc-xfce-g3"
ARG BASETAG="latest"

FROM ${BASEIMAGE}:${BASETAG}

### switch to the root user to be able to install new packages
USER 0

### update the apt cache and install your new packages
### e.g. vim editor
RUN \
    apt-get update \
    && apt-get install -y --no-install-recommends \
        vim libxtst6 \
    && apt-get -y autoremove \
    && rm -rf /var/lib/apt/lists/*

### add additional resources
ENV BUGASI=/var/bugasi
COPY ./assets/bg_bugasi.png $HOME/
COPY ./assets/FortFantastic.desktop $HOME/Desktop/
COPY ./assets/icon_ff.ico $BUGASI/
COPY ./assets/UbangeSafari.desktop $HOME/Desktop/
COPY ./assets/icon_us.ico $BUGASI/

### switch back to a non-root user
USER 1000
