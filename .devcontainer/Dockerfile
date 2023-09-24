FROM nvidia/cuda:12.1.0-devel-ubuntu22.04

ARG DEBIAN_FRONTEND=noninteractive

RUN --mount=type=cache,target=/var/cache/apt \
    apt-get update && \
    apt-get install -y  bash \
                        build-essential \
                        git \
                        curl \
                        wget \
                        zsh \
                        ca-certificates \
                        python3.10 \
                        python3-pip && \
    ln -s /usr/bin/python3.10 /usr/bin/python && \
    pip install --upgrade pip

# pip install
COPY .devcontainer/requirements.txt /workspace/requirements.txt
RUN  --mount=type=cache,target=/root/.cache/pip python -m pip install -r /workspace/requirements.txt

# # instal conda 
# RUN mkdir /root/miniconda3 && \
#     wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /root/miniconda3/miniconda.sh && \
#     bash /root/miniconda3/miniconda.sh -b -u -p /root/miniconda3 && \
#     rm -rf /root/miniconda3/miniconda.sh 

# COPY .devcontainer/environment.yml /workspace/environment.yml
# RUN --mount=type=cache,target=/root/miniconda3/pkgs \
#     /root/miniconda3/bin/conda env create -f /workspace/environment.yml


# zsh plugin
ENV SHELL /bin/zsh
COPY .devcontainer/zsh-plugins/.p10k.zsh .devcontainer/zsh-plugins/ohmyzsh.sh /root/
RUN chmod +x /root/ohmyzsh.sh && sh -c /root/ohmyzsh.sh
