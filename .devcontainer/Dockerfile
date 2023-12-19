FROM mcr.microsoft.com/devcontainers/cpp:ubuntu-22.04

ARG REINSTALL_CMAKE_VERSION_FROM_SOURCE="3.28.1"

# Optionally install the cmake for vcpkg
COPY ./reinstall-cmake.sh /tmp/

RUN if [ "${REINSTALL_CMAKE_VERSION_FROM_SOURCE}" != "none" ]; then \
        chmod +x /tmp/reinstall-cmake.sh && /tmp/reinstall-cmake.sh ${REINSTALL_CMAKE_VERSION_FROM_SOURCE}; \
    fi \
    && rm -f /tmp/reinstall-cmake.sh

# [Optional] Uncomment this section to install additional packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends python-is-python3

# Add ./bin to PATH
ENV PATH="./bin:${PATH}"

# Install CPM.cmake https://github.com/cpm-cmake/CPM.cmake
#RUN mkdir -p cmake
#RUN wget -O cmake/CPM.cmake https://github.com/cpm-cmake/CPM.cmake/releases/latest/download/get_cpm.cmake
