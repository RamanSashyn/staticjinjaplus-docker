FROM ubuntu:24.04

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3.12 \
    python3-pip \
    python3-venv \
    curl \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

ADD https://github.com/MrDave/StaticJinjaPlus/archive/refs/heads/main.tar.gz sjp.tar.gz

RUN tar xzf sjp.tar.gz --strip-components=1 && rm sjp.tar.gz \
    && python3 -m venv venv \
    && . venv/bin/activate \
    && pip install --no-cache-dir -r requirements.txt

ENV PATH="/app/venv/bin:$PATH"
CMD ["python3", "main.py"]