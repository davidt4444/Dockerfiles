FROM fedora:latest
VOLUME /tmp
WORKDIR /root
COPY . .
RUN dnf -y update
RUN dnf -y config-manager addrepo --from-repofile=https://developer.download.nvidia.com/compute/cuda/repos/fedora41/$(uname -m)/cuda-fedora41.repo
RUN dnf -y clean all
RUN dnf -y module disable nvidia-driver
RUN dnf -y config-manager setopt cuda-fedora41-$(uname -m).exclude=nvidia-driver,nvidia-modprobe,nvidia-persistenced,nvidia-settings,nvidia-libXNVCtrl,nvidia-xconfig
RUN dnf -y install cuda-toolkit
# These two need to be done when you first load the container to be able to call nvcc
# RUN find /usr -name nvcc|sed 's/\/usr/export PATH="\/usr/' |sed 's/$/:$PATH"\n/' >> ~/.bashrc
# RUN source ~/.bashrc


