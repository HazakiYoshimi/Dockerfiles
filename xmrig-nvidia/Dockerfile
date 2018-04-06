FROM nvidia/cuda
RUN apt-get update && \
      apt-get upgrade -y &&
      apt-get install git cmake libuv-dev \
      git clone https://github.com/HazakiYoshimi/xmrig-nvidia && \
      cd xmrig-nvidia && \
      mkdir build && \
      cmake -DWITH_CC_SERVER=OFF -DWITH_HTTPD=OFF . && \
      make -j$(nproc) && 
WORKDIR /xmrig-nvidia
ENTRYPOINT  ["./xmrig"]
