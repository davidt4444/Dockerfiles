FROM fedora:latest
VOLUME /tmp
WORKDIR /root
COPY . .
RUN dnf update
RUN dnf config-manager addrepo --from-repofile=https://developer.download.nvidia.com/compute/cuda/repos/fedora41/$(uname -m)/cuda-fedora41.repo
RUN dnf clean all
RUN dnf module disable nvidia-driver
RUN dnf config-manager setopt cuda-fedora41-$(uname -m).exclude=nvidia-driver,nvidia-modprobe,nvidia-persistenced,nvidia-settings,nvidia-libXNVCtrl,nvidia-xconfig
RUN dnf -y install cuda-toolkit
# These two need to be done when you first load the container to be able to call nvcc
# RUN find /usr -name nvcc|sed 's/\/usr/export PATH="\/usr/' |sed 's/$/:$PATH"\n/' >> ~/.bashrc
# RUN source ~/.bashrc


