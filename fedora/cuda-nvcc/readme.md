To build the docker image, run:
docker build -t nvcc .

There are notes for commands to make nvcc present in the dockerfile, but run these two commands in the docker container created from the image.
find /usr -name nvcc|sed 's/\/usr/export PATH="\/usr/' |sed 's/$/:$PATH"\n/' >> ~/.bashrc
source ~/.bashrc

