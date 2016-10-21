FROM hermanzdosilovic/judge0-base

RUN apt-get update && apt-get install -y \
  libpq-dev

RUN echo "gem: --no-document" > /root/.gemrc && gem install \
  rails:5.0 \
  bundler \
  pg

EXPOSE 3000

COPY . /usr/src/api
WORKDIR /usr/src/api
RUN bundle

CMD rm -f tmp/pids/server.pid && \
  rails db:create db:migrate && \
  rails s -b 0.0.0.0
