FROM ubuntu:20.04

# url of .zip file
ARG zip_url=https://github.com/eficode-academy/devops-academy-whale/archive/refs/heads/master.zip

RUN apt-get update && apt-get install -y \
    wget \
    unzip \
    ruby \
 && rm -rf /var/lib/apt/lists/* \
    /tmp/devops-academy-handins-public-master \
 && wget --output-document /tmp/repo.zip ${zip_url} \
 && unzip /tmp/repo.zip -d /tmp/ \
 && mkdir /lolcat \
 && mv /tmp/devops-academy-whale-master/whale.txt /lolcat/whale.txt \
 && gem install lolcat \
 && lolcat --seed=123 --force /lolcat/whale.txt > /lolcat/color_whale.txt \
 && rm /lolcat/whale.txt \
 && yes | gem uninstall lolcat \
 && gem cleanup \
 && apt-get autoremove -y \
 && apt-get remove -y \
    wget \
    unzip \
    ruby

ENTRYPOINT ["cat", "/lolcat/color_whale.txt"]
