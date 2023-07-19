FROM node:16-buster-slim

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      libx11-xcb1 \
      libxrandr2 \
      libxcb1 \
      libxcomposite1 \
      libxcursor1 \
      libxdamage1 \
      libxfixes3 \
      libxi6 \
      libxrender1 \
      libxss1 \
      libxtst6 \
      libnss3 \
      libnspr4 \
      libatk1.0-0 \
      libatk-bridge2.0-0 \
      libatspi2.0-0 \
      libgdk-pixbuf2.0-0 \
      libgtk-3-0 \
      libpango-1.0-0 \
      libcairo2 \
      libxcomposite1 \
      xkb-data \
      libxshmfence1

WORKDIR /app
COPY . /app

RUN npm install && npm run build
RUN npm install -g @marp-team/marp-cli
