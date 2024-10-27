#syntax=docker/dockerfile:1

FROM mcr.microsoft.com/devcontainers/python:3.12

ARG USERNAME="vscode"
ARG POETRY_VERSION="1.8.3"

USER "${USERNAME}"

RUN sudo apt-get update && sudo apt-get upgrade -y
    
WORKDIR /app

# Instale o Poetry usando pip
RUN pipx install poetry=="${POETRY_VERSION}"

# Instale o plugin de exportação do Poetry
RUN pipx inject poetry poetry-plugin-export

# Copie os arquivos de configuração do Poetry para o contêiner
COPY ./pyproject.toml ./poetry.lock* /app/

# Instale as dependências do projeto
RUN poetry install --with graficos

# Defina a variável de ambiente PYTHONPATH
ENV PYTHONPATH=/app