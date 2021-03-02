# setting up RaspberryPi 4 for use with Pico
FROM balenalib/raspberrypi4-64-ubuntu:latest

# Update
RUN apt-get update

# Install basics
RUN apt-get install -y git 

# Make folder where to store project
RUN mkdir /pico_detect

WORKDIR /pico_detect

# Get pico setup script from Raspberry Pi
RUN git clone https://github.com/raspberrypi/pico-setup.git

# running the setup script 
RUN chmod +x pico-setup/pico_setup.sh

# get drivers from ArduCAM and building tflite example from source
RUN git clone https://github.com/ArduCAM/RPI-Pico-Cam.git

RUN cd RPI-Pico-Cam/tflmicro

RUN mkdir build 

RUN cd build 

# ensuring we have cmake 
RUN snap install cmake

RUN cmake ..

RUN make

echo "great, the PicoDetect example is ready, rebooting in 5 seconds."

RUN sleep 10 

#sudo reboot at the end for changes to take effect
RUN reboot
