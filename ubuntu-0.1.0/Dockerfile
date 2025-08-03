FROM ubuntu:24.04

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3.12 \
    python3-pip \
    python3-venv \
    curl \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

ARG VERSION=0.1.0
ARG HASH=sha256:3555bcfd670e134e8360ad934cb5bad1bbe2a7dad24ba7cafa0a3bb8b23c6444
ADD --checksum=${HASH} https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/${VERSION}.tar.gz sjp.tar.gz

RUN tar xzf sjp.tar.gz --strip-components=1 && rm sjp.tar.gz \
    && python3 -m venv venv \
    && . venv/bin/activate \
    && pip install --no-cache-dir -r requirements.txt

ENV PATH="/app/venv/bin:$PATH"
CMD ["python3", "main.py"]