FROM python:3.6.3-jessie

RUN apt-get update && apt-get -y dist-upgrade \
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        libmecab-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN pip --no-cache-dir install --upgrade setuptools pip && \
    pip --no-cache-dir install \
        jupyter \
        mecab-python3

RUN mkdir -p /jupyter/work
WORKDIR /jupyter
EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--allow-root", "--no-browser"]
