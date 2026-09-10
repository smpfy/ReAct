FROM mcr.microsoft.com/devcontainers/base:ubuntu22.04
RUN apt-get update && apt-get install -y --no-install-recommends \
    cmake \
    build-essential \
    libgl1 \
    libglib2.0-0 \
    libxcb1 \
    7zip \
    && rm -rf /var/lib/apt/lists/*
COPY ./alfworld-assets /tmp/alfworld-assets 
ENV ALFWORLD_DATA="/home/vscode/.cache/alfworld"
RUN mkdir -p "${ALFWORLD_DATA}/logic" && \
    mv /tmp/alfworld-assets/alfred.pddl /tmp/alfworld-assets/alfred.twl2 -t "${ALFWORLD_DATA}/logic" && \
    7zz x /tmp/alfworld-assets/json_2.1.1_json.7z -o"${ALFWORLD_DATA}/json_2.1.1" && \
    7zz x /tmp/alfworld-assets/json_2.1.1_pddl.7z -o"${ALFWORLD_DATA}/json_2.1.1" && \
    7zz x /tmp/alfworld-assets/json_2.1.1_tw-pddl.zip.old.7z -o"${ALFWORLD_DATA}/json_2.1.1" && \
    rm -rf /tmp/alfworld-assets
USER vscode
RUN curl -LsSf https://astral.sh/uv/0.12.7/install.sh | sh