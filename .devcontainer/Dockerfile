FROM zeek/zeek:8.0 AS dist

FROM mcr.microsoft.com/vscode/devcontainers/base:1-bookworm

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# hadolint ignore=DL3008
RUN apt-get -q update \
 && apt-get install -q -y --no-install-recommends \
     ca-certificates \
     cmake \
     libmaxminddb0 \
     libnode108 \
     libpython3.11 \
     libpcap0.8 \
     libpcap0.8-dev \
     libssl3 \
     libuv1 \
     libz1 \
     libzmq5 \
     pipx \
     python3-git \
     python3-minimal \
     python3-dev \
     python3-semantic-version \
     python3-websocket \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

# Copy over Zeek installation from build
COPY --from=dist /usr/local/zeek /usr/local/zeek
ENV PATH="/usr/local/zeek/bin:${PATH}"
ENV PYTHONPATH="/usr/local/zeek/lib/zeek/python"

ENV PATH="/root/.local/bin:${PATH}"
# hadolint ignore=DL3013
RUN pipx install zeekscript
