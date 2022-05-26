# openshift-operator

## Installing Go Programming Language

This url has Go version specific binaries https://go.dev/dl
```
wget https://go.dev/dl/go1.18.2.linux-amd64.tar.gz
tar xvfz go1.18.2.linux-amd64.tar.gz
pwd
```

Maksure the go folder path is exported in your ~/.bashrc file as shown below at the at the end of the file
```
export PATH=/home/jegan/operator-sdk/go/bin:$PATH
```

Apply the changes made in .bashrc
```
source ~/.bashrc
```

Check the verion of go
```
go version
```

The expected output is
<pre>
(jegan@tektutor.org)$ <b>go version</b>
go version go1.18.2 linux/amd64
</pre>

## Install OpenShift Operator SDK

This url has OpenShift version specific Operator SDK binary https://mirror.openshift.com/pub/openshift-v4/x86_64/clients/operator-sdk

```
wget https://mirror.openshift.com/pub/openshift-v4/x86_64/clients/operator-sdk/4.10.12/operator-sdk-v1.16.0-ocp-linux-x86_64.tar.gz

tar xvf operator-sdk-v1.16.0-ocp-linux-x86_64.tar.gz

sudo mv ./operator-sdk /usr/local/bin/operator-sdk
```

Let's us verify the version of operator sdk
```
operator-sdk version
```

The expected output is
<pre>
(jegan@tektutor.org)$ <b>operator-sdk version</b>
operator-sdk version: "v1.16.0-ocp", commit: "28da5f640cef1a81d91f156b74b50344fbe84121", kubernetes version: "v1.22", go version: "go1.17.5", GOOS: "linux", GOARCH: "amd64"
</pre>

## Install Docker Community Edition
```
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

Start the Docker service
```
sudo systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker $USER
newgrp docker
```

Check the docker version and see if you can list the images
```
docker version
docker images
```

The expected output is
<pre>
(jegan@tektutor.org)$ <b>docker --version</b>
Docker version 20.10.7, build 20.10.7-0ubuntu5~18.04.3

(jegan@tektutor.org)$ <b>docker images</b>
REPOSITORY                                           TAG                           IMAGE ID       CREATED        SIZE
</pre>

## Install podman
```
sudo yum install -y epel-release
sudo yum -y install podman
```

Check the version of podman
```
podman version
```

The expected output is
<pre>
(jegan@tektutor.org)$ <b>podman version</b>
Version:      3.0.1
API Version:  3.0.0
Go Version:   go1.15.2
Built:        Thu Jan  1 05:30:00 1970
OS/Arch:      linux/amd64
</pre>

## Install Ansible in CentOS 7.x
```
sudo yum install -y ansible
```

Check the version of ansible 
```
ansible --version
```

Expected outputs is
<pre>
(jegan@tektutor.org)$ <b>ansible --version</b>
ansible 2.9.27
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/home/jegan/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.17 (default, Mar 18 2022, 13:21:42) [GCC 7.5.0]
</pre>
