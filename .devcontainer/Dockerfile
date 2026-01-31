FROM mcr.microsoft.com/devcontainers/python:0-3.11

ENV PYTHONUNBUFFERED=1

# Fix: remove broken Yarn repo that breaks apt-get update (missing GPG key)
RUN rm -f /etc/apt/sources.list.d/yarn.list \
    && rm -f /etc/apt/trusted.gpg.d/yarn.gpg \
    && rm -f /usr/share/keyrings/yarn.gpg

# Install OS deps (psql client)
RUN apt-get update \
  && export DEBIAN_FRONTEND=noninteractive \
  && apt-get install -y --no-install-recommends \
     ca-certificates curl gnupg \
     postgresql-client-16 \
  && rm -rf /var/lib/apt/lists/*