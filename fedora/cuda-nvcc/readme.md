To build the docker image, run:<br />
docker build -t nvcc .<br />
sudo docker run -it --name=nvcc --entrypoint bash nvcc:latest<br />
To start container back up with shell<br />
sudo docker start -i nvcc<br />
<br />
There are notes for commands to make nvcc present in the dockerfile path.<br />
First run this <br />
find /usr -name nvcc<br />
In the statement below, replace {Resulting path} with the path that it returns. <br />
export PATH={Resulting path}:$PATH<br />
Find the path in the return results that contains the nvcc you would like to execute<br />
Paste that minus the nvcc at the end into the bottom of your ~/.bashrc<br />
After doing that run the statement below.<br />
source ~/.bashrc<br />

