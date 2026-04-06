FROM        --platform=$TARGETOS/$TARGETARCH debian:bookworm-slim

LABEL       author="Michael Parker" maintainer="parker@pterodactyl.io"

LABEL       org.opencontainers.image.source="https://github.com/alttky567/pterodactyl-build"
LABEL       org.opencontainers.image.licenses=MIT

ENV         DEBIAN_FRONTEND=noninteractive

RUN         apt update && apt upgrade -y \
				&& apt install -y autoconf automake binutils build-essential clang cmake gcc g++ gdb libgcc-s1 libc++-dev libc6 git wget curl tar zip unzip xz-utils liblzo2-2 cabextract iproute2 net-tools netcat-openbsd telnet libatomic1 libsdl2-2.0-0 \
    			libffi-dev libfontconfig1 libicu72 icu-devtools libunwind8 libssl-dev libtool sqlite3 libsqlite3-dev libmariadb-dev locales ffmpeg gnupg2 apt-transport-https software-properties-common ca-certificates tzdata \
    			liblua5.4-0 libz-dev make ninja-build patch pkg-config python3 rapidjson-dev zlib1g-dev \
				&& update-locale lang=en_US.UTF-8 \
				&& dpkg-reconfigure --frontend noninteractive locales \
				&& useradd -m -d /home/container -s /bin/bash container

USER        container
ENV         USER=container HOME=/home/container
ENV         DEBIAN_FRONTEND noninteractive

WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
