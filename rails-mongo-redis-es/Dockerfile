FROM ruby:latest

# add the Node.js package source
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash -
# install the CLI mongo client and nodejs
RUN apt-get update && apt-get install -yq build-essential mongodb-clients nodejs
# install phantomjs. --unsafe-perm is a work-around for a Node.js 8.x + phantomjs bug
RUN npm install -g phantomjs-prebuilt --unsafe-perm
# cleanup the apt cache
RUN apt-get autoremove -yq && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# use /var/app as our working directory
ENV RAILS_APP_PATH /var/app
RUN mkdir $RAILS_APP_PATH
WORKDIR $RAILS_APP_PATH

# copy the Gemfile into the container
COPY Gemfile $RAILS_APP_PATH/Gemfile
COPY Gemfile.lock $RAILS_APP_PATH/Gemfile.lock

# install the gems (re-run `docker-compose build` when the Gemfile is changed)
ENV BUNDLE_PATH /bundler
RUN bundle install

ENV WEB_CONSOLE_IP '172.18.0.0/12'

RUN mongo --version
RUN nodejs --version
RUN npm --version
RUN phantomjs -v
RUN rails --version
RUN ruby -v
