FROM node:latest

# install the postgres client dependencies
RUN apt-get update && apt-get install -yq build-essential libpq-dev
# cleanup the apt cache
RUN apt-get autoremove -yq && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# install bower, mocha globally
ENV NPM_CONFIG_PREFIX=/home/node/.npm-global
ENV PATH=$PATH:/home/node/.npm-global/bin
RUN npm install -g bower mocha

# use /var/app as our working directory
WORKDIR /var/app
RUN chown node /var/app

# switch to non-root user for application packages
USER node

# install the npm packages (re-run `docker-compose build` when package.json is changed)
COPY package.json .
RUN npm install --quiet

# install the bower packages (re-run `docker-compose build` when bower.json is changed)
COPY bower.json .
RUN bower install --quiet
