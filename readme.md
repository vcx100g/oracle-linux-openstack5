# Init

Using Oracle Linux 7 only, Oracle Linux 8 is still not support Btrfs and Openstack

Follow instruction in:

https://docs.oracle.com/cd/E64747_01/E64749/html/osusg-openstack-install.html

https://docs.oracle.com/cd/E64747_01/E64749/html/osusg-install-node-os.html
https://docs.oracle.com/cd/E64747_01/E64749/html/osusg-install-master.html
https://docs.oracle.com/cd/E64747_01/E64749/html/osusg-install-docker-setup.html
https://docs.oracle.com/cd/E64747_01/E64749/html/osusg-install-run.html

## Setup hostname

```shell
sudo hostnamectl set-hostname masternode
sudo hostnamectl set-hostname targetnode1
sudo hostnamectl set-hostname targetnode2
```

edit /etc/hosts add:
```
192.168.17.140  masternode masternode.localdomain masternode-6 masternode-6.localdomain
192.168.17.142  targetnode2 targetnode2.localdomain targetnode2-6 targetnode2-6.localdomain
192.168.17.143  targetnode1 targetnode1.localdomain targetnode1-6 targetnode1-6.localdomain
```

## Use latest repo

download and replace oracle-linux-ol7.repo:
```
$ sudo curl -L -o /etc/yum.repos.d/oracle-linux-ol7.repo \
    http://public-yum.oracle.com/public-yum-ol7.repo
```
