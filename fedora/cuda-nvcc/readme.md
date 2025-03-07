To build the docker image, run:
docker build -t nvcc .
sudo docker run -it --name=nvcc --entrypoint bash nvcc:latest

There are notes for commands to make nvcc present in the dockerfile path.
First run this 
find /usr -name nvcc
In the statement below, replace {Resulting path} with the path that it returns. 
export PATH={Resulting path}:$PATH
Find the path in the return results that contains the nvcc you would like to execute
Paste that minus the nvcc at the end into the bottom of your ~/.bashrc
After doing that run the statement below.
source ~/.bashrc

