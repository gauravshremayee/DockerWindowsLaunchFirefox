# DockerWindowsLaunchFirefox
launch firefox from ubuntu image to Windows system
Download vcxsrv
https://sourceforge.net/projects/vcxsrv/

Make sure to save to configuration file before you click finish!
Save it to one of the following locations:

%appdata%\Xming
%userprofile%\Desktop
%userprofile%
Create a Dockerfile
To use a simple example, create a new folder and place a Dockerfile with the following content in it:

FROM ubuntu:14.04
RUN apt-get update && apt-get install -y firefox
CMD /usr/bin/firefox
Docker
Build and run the container
For advanced docker users, here the quick commands:

docker build -t firefox .
set-variable -name DISPLAY -value YOUR-IP:0.0
docker run -ti --rm -e DISPLAY=$DISPLAY firefox
PowerShell
With some explaination:
Now build the new container and label it firefox:

docker build -t firefox .
PowerShell
Because the container has its own localhost interface, we need to use the IP-address of our network adapter.
Find out your ip address with

ipconfig
PowerShell
Set the environment variable (replace IP with yours):

set-variable -name DISPLAY -value 10.11.128.118:0.0
PowerShell
Run to the container:

docker run -ti --rm -e DISPLAY=$DISPLAY firefox
PowerShell
