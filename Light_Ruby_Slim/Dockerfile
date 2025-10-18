#--- Ruby Slim

FROM ruby:3.1-slim

LABEL maintainer="github.com/litio7" \
      description="Ruby Slim Lightweight"

#--- Dependencies

RUN apt-get update && apt-get install -y \
    build-essential git nodejs npm \
    libffi-dev libgdbm-dev libncurses5-dev libsqlite3-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

#--- GitPage

WORKDIR /root/jekyll-theme-chirpy

RUN git clone https://github.com/cotes2020/jekyll-theme-chirpy.git /root/jekyll-theme-chirpy && \
    git config --global user.email "build@example.com" && \
    git config --global user.name "Litio7"

#--- Gems

RUN gem install bundler jekyll && \
    ./tools/init.sh && \
    bundle install

#--- Server

EXPOSE 4000

CMD ["bundle", "exec", "jekyll", "serve", "--watch", "--host", "0.0.0.0"]
