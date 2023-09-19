FROM mcr.microsoft.com/devcontainers/cpp:1-debian-11

ARG REINSTALL_CMAKE_VERSION_FROM_SOURCE="3.27.4"

# Optionally install the cmake for vcpkg
COPY ./reinstall-cmake.sh /tmp/

RUN if [ "${REINSTALL_CMAKE_VERSION_FROM_SOURCE}" != "none" ]; then \
        chmod +x /tmp/reinstall-cmake.sh && /tmp/reinstall-cmake.sh ${REINSTALL_CMAKE_VERSION_FROM_SOURCE}; \
    fi \
    && rm -f /tmp/reinstall-cmake.sh

RUN \
  sudo apt-get update && \
  export DEBIAN_FRONTEND=noninteractive && \
  sudo apt-get -y install --no-install-recommends g++ \
  cmake \
  ninja-build \
  libsdl2-dev \
  libpng-dev \
  libjpeg-dev \
  libgl1-mesa-dev \
  libglew-dev \
  libopenal-dev \
  libmad0-dev \
  uuid-dev 