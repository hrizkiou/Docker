FROM ruby:2.5.1
RUN apt-get update && apt upgrade -y && apt install -y ruby-dev build-essential nodejs sqlite3 git
RUN gem install rails:5.2.0
ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app
ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed
