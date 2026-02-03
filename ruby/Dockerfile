ARG RUBY_VERSION=3.3.5
FROM ruby:${RUBY_VERSION}-slim

RUN apt-get update -qq && \
    apt-get install -y --no-install-recommends build-essential git && \
    rm -rf /var/lib/apt/lists/*
