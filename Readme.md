# redichain-web-base-container

Base docker container for Redichain Web app


### Usage

This is used to be the base image of a Dockerfile looking more like this:


    FROM makevoid/redichain-web-base

    ADD Gemfile       .
    ADD Gemfile.lock  .


    RUN bundle install --without development --without test --jobs 8


    VOLUME /app/public/static/uploads

    ADD . /app

    EXPOSE 3000

    ENV DOCKER 1

    CMD bundle exec rackup -p 3000 -o 0.0.0.0


It is suggested to re-build yourself a container to always pre-install latest gems, it will speed up your future builds.
