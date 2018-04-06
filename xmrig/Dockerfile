FROM alpine:latest
RUN adduser -S -D -H -h /xmrig xminer
RUN apk --no-cache upgrade && \
      apk --no-cache add \
      git \
      cmake \
      libuv-dev \
      build-base && \
      git clone https://github.com/HazakiYoshimi/xmrig && \
      cd xmrig && \
      sed -i -e 's/constexpr const int kDonateLevel = 5;/constexpr const int kDonateLevel = 0;/g' src/donate.h && \
      mkdir build && \
      cmake -DWITH_CC_SERVER=OFF -DWITH_HTTPD=OFF . && \
      make -j$(nproc) && \
      apk del \
        build-base \
        cmake \
        git
USER xminer
WORKDIR /xmrig
ENTRYPOINT  ["./xmrig"]
