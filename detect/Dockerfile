# setting up RaspberryPi 3 for use with Pico
FROM balenalib/rpi-raspbian:latest

# Update
RUN apt-get update

# Install basics
RUN apt-get install -y git cmake python3-dev gcc-arm-none-eabi build-essential libnewlib-arm-none-eabi libstdc++-arm-none-eabi-newlib pkg-config libasound2

# Make folder where to store project
RUN mkdir /pico_detect

WORKDIR /pico_detect

# We need to override the 64-bit vscode.deb check (for now), and stay with 32-bit.  So we end up overwriting theirs with our own.
RUN git clone https://github.com/raspberrypi/pico-setup.git
COPY pico_setup.sh pico-setup/pico_setup.sh
RUN chmod +x pico-setup/pico_setup.sh && cd pico-setup && /bin/bash -e pico_setup.sh

# get drivers from ArduCAM and building tflite example from source
RUN git clone https://github.com/ArduCAM/RPI-Pico-Cam.git

RUN export PICO_SDK_PATH=/pico_detect/pico-setup/pico/pico-sdk && cd RPI-Pico-Cam/tflmicro && mkdir build && cd build && cmake .. && make

RUN echo "Great, the PicoDetect example is ready."

CMD /bin/bash
