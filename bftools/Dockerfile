FROM openjdk:16-slim-buster

RUN apt-get update && apt-get install -y \
    curl \
    unzip \
    && rm -rf /var/lib/apt/lists/*

RUN curl -o bftools.zip $(curl -Ls -o /dev/null -w %{url_effective} http://downloads.openmicroscopy.org/latest/bio-formats)/artifacts/bftools.zip \
    && unzip -d /opt bftools.zip \
    && rm bftools.zip \
    && chmod a+rx /opt/bftools/* \
    && useradd -m bf

USER bf
RUN echo 'export PATH=/opt/bftools:$PATH' >> /home/bf/.bashrc

ENV HOME /home/bf
WORKDIR /home/bf

CMD bash
