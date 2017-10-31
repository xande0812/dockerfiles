FROM python:3.6.3-jessie

RUN apt-get update && apt-get -y dist-upgrade \
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        mecab \
        libmecab-dev \
        mecab-ipadic-utf8 \
        git \
        make \
        curl \
        xz-utils \
        file \
        unzip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /tmp
RUN git clone --depth 1 https://github.com/neologd/mecab-ipadic-neologd.git \
    && cd mecab-ipadic-neologd \
    && mkdir $(mecab-config --dicdir) \
    && ./bin/install-mecab-ipadic-neologd -n -y \
    && rm -rf mecab-ipadic-neologd

RUN pip --no-cache-dir install --upgrade setuptools pip && \
    pip --no-cache-dir install \
        numpy \
        jupyter \
        mecab-python3 \
        gensim \
        scikit-learn \
        chainer \
        polyglot

RUN wget -qO- -O tmp.zip 'http://gensen.dl.itc.u-tokyo.ac.jp/soft/pytermextract-0_12b.zip' \
    && unzip tmp.zip -d termextract \
    && rm tmp.zip \
    && cd termextract && python setup.py install

RUN mkdir -p /jupyter/work
WORKDIR /jupyter
EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--allow-root", "--no-browser"]
