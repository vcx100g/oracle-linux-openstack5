# Init

Using Oracle Linux 7 only, Oracle Linux 8 is still not support Btrfs and Openstack

Hosting 1 master node (include registry docker) and 2 target nodes

You can also host 1 master node, 1 docker registry and 2 target nodes

Follow instruction in:

https://docs.oracle.com/cd/E64747_01/E64749/html/osusg-openstack-install.html

https://docs.oracle.com/cd/E64747_01/E64749/html/osusg-install-node-os.html
https://docs.oracle.com/cd/E64747_01/E64749/html/osusg-install-master.html
https://docs.oracle.com/cd/E64747_01/E64749/html/osusg-install-docker-setup.html
https://docs.oracle.com/cd/E64747_01/E64749/html/osusg-install-run.html

For kolla account password generate:
https://docs.oracle.com/cd/E96260_01/E96263/html/kolla-accounts.html

## Install Target node

First install all
https://docs.oracle.com/cd/E64747_01/E64749/html/osusg-install-node-os.html

Then setup ssh
https://docs.oracle.com/cd/E96260_01/E96263/html/kolla-user.html

!important, must install
```shell
sudo yum install -y openstack-kolla-user
```

Also need kolla folder to have permission
```shell
$ sudo chown kolla:kolla /usr/share/kolla
```

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

## Kollacli command

https://docs.oracle.com/cd/E64747_01/E64749/html/osusg-kollacli-commands.html#osusg-kollacli-host-add

Setup on multiple PC/Server need to use remote (not local)
```shell
$ kollacli setdeploy remote
```

## Add target node

Copy the SSH public key for the kolla user to each host and confirm that the kolla user can log in to the host using SSH keys. 

```shell
$ kollacli host add targetnode1
$ kollacli host setup targetnode1

```
