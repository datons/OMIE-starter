FROM mambaorg/micromamba:latest

ENV LANG=C.UTF-8
ENV LC_ALL=C.UTF-8
ENV PATH /opt/conda/bin:$PATH

RUN micromamba shell init -s zsh

USER root

WORKDIR /workspace

COPY environment.yml ./

RUN micromamba install --file environment.yml --name base && \
    micromamba clean --all --yes

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    git \
    curl \
    zsh \
    && apt-get clean && rm -rf /var/lib/apt/lists/*


CMD ["zsh"]