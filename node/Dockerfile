ARG NODE_VERSION=20
FROM node:${NODE_VERSION}-slim

# Native module build deps (better-sqlite3, onnxruntime, etc.)
RUN apt-get update && \
    apt-get install -y --no-install-recommends python3 make g++ && \
    rm -rf /var/lib/apt/lists/*
