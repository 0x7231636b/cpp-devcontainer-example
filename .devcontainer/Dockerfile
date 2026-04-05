FROM debian:trixie

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    # C++ toolchain
    gcc-14 g++-14 \
    cmake ninja-build \
    make \
    pkg-config \
    # Qt 6
    qt6-base-dev \
    qt6-tools-dev \
    qt6-l10n-tools \
    libqt6core6t64 \
    # buildroot host dependencies
    bison \
    flex \
    libssl-dev \
    libncurses-dev \
    bc \
    rsync \
    unzip \
    cpio \
    file \
    # vcpkg dependencies
    git \
    curl \
    wget \
    zip \
    tar \
    # dev utilities
    gdb \
    valgrind \
    uncrustify \
    clang-format \
    clang-tidy \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/* \
    # Set GCC 14 as the default compiler
    && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-14 100 \
    && update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-14 100 \
    && update-alternatives --install /usr/bin/cc cc /usr/bin/gcc-14 100 \
    && update-alternatives --install /usr/bin/c++ c++ /usr/bin/g++-14 100 \
    # Install vcpkg
    && git clone https://github.com/microsoft/vcpkg /opt/vcpkg \
    && /opt/vcpkg/bootstrap-vcpkg.sh -disableMetrics \
    # Install buildroot
    && git clone https://gitlab.com/buildroot.org/buildroot.git /opt/buildroot

ENV VCPKG_ROOT=/opt/vcpkg \
    BUILDROOT_ROOT=/opt/buildroot \
    PATH="${PATH}:/opt/vcpkg:/opt/buildroot"
