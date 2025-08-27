FROM zeek/zeek:8.0 AS dist

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# hadolint ignore=DL3008
RUN apt-get -q update \
 && apt-get install -q -y --no-install-recommends \
     cmake \
     g++ \
     libpcap0.8-dev \
     pipx \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

ENV PATH="/root/.local/bin:${PATH}"
# hadolint ignore=DL3013
RUN pipx install zeekscript
