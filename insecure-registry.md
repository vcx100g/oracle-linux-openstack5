# Doc

https://docs.docker.com/registry/insecure/#troubleshoot-insecure-registry

follow each step to solve insecure cert problem 

https://docs.docker.com/registry/deploying/#get-a-certificate

### To test local registry work

docker pull ubuntu:16.04
docker tag ubuntu:16.04 masternode.localdomain:5000/my-ubuntu
docker push masternode.localdomain:5000/my-ubuntu
docker pull masternode.localdomain:5000/my-ubuntu
