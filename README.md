# openshift-operator

For detailed official documentation, you may check here 
<pre>
https://docs.openshift.com/container-platform/4.10/operators/operator_sdk/ansible/osdk-ansible-tutorial.html
</pre>

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

## Install Ansible Runner
For detailed instructions, you may check here https://ansible-runner.readthedocs.io/en/latest/install/
```
pip install ansible-runner
```

Expected output is
<pre>
(jegan@tektutor.org)$ <b>pip install ansible-runner</b>
Collecting ansible-runner
  Downloading https://files.pythonhosted.org/packages/f3/7b/b1e7e449959d53e37daeb454d0581ebf2aa3f3f23d51aaaa5c9835f7fefa/ansible-runner-2.2.0.tar.gz (172kB)
    100% |████████████████████████████████| 174kB 2.1MB/s 
Collecting pexpect>=4.5 (from ansible-runner)
  Downloading https://files.pythonhosted.org/packages/39/7b/88dbb785881c28a102619d46423cb853b46dbccc70d3ac362d99773a78ce/pexpect-4.8.0-py2.py3-none-any.whl (59kB)
    100% |████████████████████████████████| 61kB 3.3MB/s 
Collecting packaging (from ansible-runner)
  Downloading https://files.pythonhosted.org/packages/3e/89/7ea760b4daa42653ece2380531c90f64788d979110a2ab51049d92f408af/packaging-20.9-py2.py3-none-any.whl (40kB)
    100% |████████████████████████████████| 40kB 4.1MB/s 
Collecting python-daemon (from ansible-runner)
  Downloading https://files.pythonhosted.org/packages/b1/cc/2ab0d910548de45eaaa50d0372387951d9005c356a44c6858db12dc6b2b7/python_daemon-2.3.0-py2.py3-none-any.whl
Collecting pyyaml (from ansible-runner)
  Downloading https://files.pythonhosted.org/packages/ba/d4/3cf562876e0cda0405e65d351b835077ab13990e5b92912ef2bf1a2280e0/PyYAML-5.4.1-cp27-cp27mu-manylinux1_x86_64.whl (574kB)
    100% |████████████████████████████████| 583kB 1.5MB/s 
Collecting six (from ansible-runner)
  Downloading https://files.pythonhosted.org/packages/d9/5a/e7c31adbe875f2abbb91bd84cf2dc52d792b5a01506781dbcf25c91daf11/six-1.16.0-py2.py3-none-any.whl
Collecting ptyprocess>=0.5 (from pexpect>=4.5->ansible-runner)
  Downloading https://files.pythonhosted.org/packages/22/a6/858897256d0deac81a172289110f31629fc4cee19b6f01283303e18c8db3/ptyprocess-0.7.0-py2.py3-none-any.whl
Collecting pyparsing>=2.0.2 (from packaging->ansible-runner)
  Downloading https://files.pythonhosted.org/packages/8a/bb/488841f56197b13700afd5658fc279a2025a39e22449b7cf29864669b15d/pyparsing-2.4.7-py2.py3-none-any.whl (67kB)
    100% |████████████████████████████████| 71kB 4.2MB/s 
Collecting docutils (from python-daemon->ansible-runner)
  Downloading https://files.pythonhosted.org/packages/8d/14/69b4bad34e3f250afe29a854da03acb6747711f3df06c359fa053fae4e76/docutils-0.18.1-py2.py3-none-any.whl (570kB)
    100% |████████████████████████████████| 573kB 1.4MB/s 
Collecting lockfile>=0.10 (from python-daemon->ansible-runner)
  Downloading https://files.pythonhosted.org/packages/c8/22/9460e311f340cb62d26a38c419b1381b8593b0bb6b5d1f056938b086d362/lockfile-0.12.2-py2.py3-none-any.whl
Collecting setuptools (from python-daemon->ansible-runner)
  Downloading https://files.pythonhosted.org/packages/e1/b7/182161210a13158cd3ccc41ee19aadef54496b74f2817cc147006ec932b4/setuptools-44.1.1-py2.py3-none-any.whl (583kB)
    100% |████████████████████████████████| 583kB 1.5MB/s 
Building wheels for collected packages: ansible-runner
  Running setup.py bdist_wheel for ansible-runner ... done
  Stored in directory: /home/jegan/.cache/pip/wheels/a4/02/ec/167e79b59e3a3654fcfa44bc3d198d6ac53e87f86c053cdecd
Successfully built ansible-runner
Installing collected packages: ptyprocess, pexpect, pyparsing, packaging, docutils, lockfile, setuptools, python-daemon, pyyaml, six, ansible-runner
Successfully installed ansible-runner-2.2.0 docutils-0.18.1 lockfile-0.12.2 packaging-20.9 pexpect-4.8.0 ptyprocess-0.7.0 pyparsing-2.4.7 python-daemon-2.3.0 pyyaml-5.4.1 setuptools-44.1.1 six-1.16.0
</pre>

## Installing Ansible Http Event Emitter
```
pip install ansible-runner-http
```

## Installing OpenShift python client
```
```

Expected output is
<pre>
(jegan@tektutor.org)$ pip install openshift
Collecting openshift
  Downloading https://files.pythonhosted.org/packages/97/c0/d8e2aae7b4e8f3709eca4fd8c2f70ea3c66151d1a5259e9a7e1ee2497608/openshift-0.13.1.tar.gz
Collecting kubernetes>=12.0 (from openshift)
  Downloading https://files.pythonhosted.org/packages/19/4a/39b09950b35a36fe1af54bb85413c2976b62a5c29e7254c8c3573f86c028/kubernetes-18.20.0-py2.py3-none-any.whl (1.6MB)
    100% |████████████████████████████████| 1.6MB 653kB/s 
Collecting python-string-utils (from openshift)
  Downloading https://files.pythonhosted.org/packages/5d/13/216f2d4a71307f5a4e5782f1f59e6e8e5d6d6c00eaadf9f92aeccfbb900c/python-string-utils-0.6.0.tar.gz
Collecting six (from openshift)
  Using cached https://files.pythonhosted.org/packages/d9/5a/e7c31adbe875f2abbb91bd84cf2dc52d792b5a01506781dbcf25c91daf11/six-1.16.0-py2.py3-none-any.whl
Collecting setuptools>=21.0.0 (from kubernetes>=12.0->openshift)
  Using cached https://files.pythonhosted.org/packages/e1/b7/182161210a13158cd3ccc41ee19aadef54496b74f2817cc147006ec932b4/setuptools-44.1.1-py2.py3-none-any.whl
Collecting ipaddress>=1.0.17; python_version == "2.7" (from kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/c2/f8/49697181b1651d8347d24c095ce46c7346c37335ddc7d255833e7cde674d/ipaddress-1.0.23-py2.py3-none-any.whl
Collecting requests (from kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/2d/61/08076519c80041bc0ffa1a8af0cbd3bf3e2b62af10435d269a9d0f40564d/requests-2.27.1-py2.py3-none-any.whl (63kB)
    100% |████████████████████████████████| 71kB 4.4MB/s 
Collecting python-dateutil>=2.5.3 (from kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/36/7a/87837f39d0296e723bb9b62bbb257d0355c7f6128853c78955f57342a56d/python_dateutil-2.8.2-py2.py3-none-any.whl (247kB)
    100% |████████████████████████████████| 256kB 2.6MB/s 
Collecting requests-oauthlib (from kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/6f/bb/5deac77a9af870143c684ab46a7934038a53eb4aa975bc0687ed6ca2c610/requests_oauthlib-1.3.1-py2.py3-none-any.whl
Collecting websocket-client!=0.40.0,!=0.41.*,!=0.42.*,>=0.32.0 (from kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/f7/0c/d52a2a63512a613817846d430d16a8fbe5ea56dd889e89c68facf6b91cb6/websocket_client-0.59.0-py2.py3-none-any.whl (67kB)
    100% |████████████████████████████████| 71kB 5.5MB/s 
Collecting certifi>=14.05.14 (from kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/37/45/946c02767aabb873146011e665728b680884cd8fe70dde973c640e45b775/certifi-2021.10.8-py2.py3-none-any.whl (149kB)
    100% |████████████████████████████████| 153kB 3.3MB/s 
Collecting urllib3>=1.24.2 (from kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/ec/03/062e6444ce4baf1eac17a6a0ebfe36bb1ad05e1df0e20b110de59c278498/urllib3-1.26.9-py2.py3-none-any.whl (138kB)
    100% |████████████████████████████████| 143kB 3.7MB/s 
Collecting google-auth>=1.0.1 (from kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/fc/04/ea9a945a6fbd7f7f977fcf7e300a715f1635939e5daf141b95068abaa5ec/google_auth-2.6.6-py2.py3-none-any.whl (156kB)
    100% |████████████████████████████████| 163kB 3.3MB/s 
Collecting pyyaml>=5.4.1 (from kubernetes>=12.0->openshift)
  Using cached https://files.pythonhosted.org/packages/ba/d4/3cf562876e0cda0405e65d351b835077ab13990e5b92912ef2bf1a2280e0/PyYAML-5.4.1-cp27-cp27mu-manylinux1_x86_64.whl
Collecting idna<3,>=2.5; python_version < "3" (from requests->kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/a2/38/928ddce2273eaa564f6f50de919327bf3a00f091b5baba8dfa9460f3a8a8/idna-2.10-py2.py3-none-any.whl (58kB)
    100% |████████████████████████████████| 61kB 4.3MB/s 
Collecting chardet<5,>=3.0.2; python_version < "3" (from requests->kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/19/c7/fa589626997dd07bd87d9269342ccb74b1720384a4d739a1872bd84fbe68/chardet-4.0.0-py2.py3-none-any.whl (178kB)
    100% |████████████████████████████████| 184kB 2.9MB/s 
Collecting oauthlib>=3.0.0 (from requests-oauthlib->kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/05/57/ce2e7a8fa7c0afb54a0581b14a65b56e62b5759dbc98e80627142b8a3704/oauthlib-3.1.0-py2.py3-none-any.whl (147kB)
    100% |████████████████████████████████| 153kB 3.6MB/s 
Collecting pyasn1-modules>=0.2.1 (from google-auth>=1.0.1->kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/95/de/214830a981892a3e286c3794f41ae67a4495df1108c3da8a9f62159b9a9d/pyasn1_modules-0.2.8-py2.py3-none-any.whl (155kB)
    100% |████████████████████████████████| 163kB 3.9MB/s 
Collecting cachetools<6.0,>=2.0.0 (from google-auth>=1.0.1->kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/2f/a6/30b0a0bef12283e83e58c1d6e7b5aabc7acfc4110df81a4471655d33e704/cachetools-3.1.1-py2.py3-none-any.whl
Collecting rsa<4.6; python_version < "3.6" (from google-auth>=1.0.1->kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/26/f8/8127fdda0294f044121d20aac7785feb810e159098447967a6103dedfb96/rsa-4.5-py2.py3-none-any.whl
Collecting enum34>=1.1.10; python_version < "3.4" (from google-auth>=1.0.1->kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/6f/2c/a9386903ece2ea85e9807e0e062174dc26fdce8b05f216d00491be29fad5/enum34-1.1.10-py2-none-any.whl
Collecting pyasn1<0.5.0,>=0.4.6 (from pyasn1-modules>=0.2.1->google-auth>=1.0.1->kubernetes>=12.0->openshift)
  Downloading https://files.pythonhosted.org/packages/62/1e/a94a8d635fa3ce4cfc7f506003548d0a2447ae76fd5ca53932970fe3053f/pyasn1-0.4.8-py2.py3-none-any.whl (77kB)
    100% |████████████████████████████████| 81kB 5.0MB/s 
Building wheels for collected packages: openshift, python-string-utils
  Running setup.py bdist_wheel for openshift ... done
  Stored in directory: /home/jegan/.cache/pip/wheels/31/5c/3f/c655e9f2030f180a983293feeec85ff95d2546ae7d3da6cb41
  Running setup.py bdist_wheel for python-string-utils ... done
  Stored in directory: /home/jegan/.cache/pip/wheels/b2/1d/3f/2f554103ba3e4aa8d53b8e1ea70b5a0b4f74409a789e17fa35
Successfully built openshift python-string-utils
Installing collected packages: setuptools, ipaddress, idna, certifi, urllib3, chardet, requests, six, python-dateutil, oauthlib, requests-oauthlib, websocket-client, pyasn1, pyasn1-modules, cachetools, rsa, enum34, google-auth, pyyaml, kubernetes, python-string-utils, openshift
Successfully installed cachetools-3.1.1 certifi-2021.10.8 chardet-4.0.0 enum34-1.1.10 google-auth-2.6.6 idna-2.10 ipaddress-1.0.23 kubernetes-18.20.0 oauthlib-3.1.0 openshift-0.13.1 pyasn1-0.4.8 pyasn1-modules-0.2.8 python-dateutil-2.8.2 python-string-utils-0.6.0 pyyaml-5.4.1 requests-2.27.1 requests-oauthlib-1.3.1 rsa-4.5 setuptools-44.1.1 six-1.16.0 urllib3-1.26.9 websocket-client-0.59.0
</pre>

## Initialize the ansible operator project
```
operator-sdk init \
    --plugins=ansible \
    --domain=example.com
```

Expected output is
<pre>
(jegan@tektutor.org)$ operator-sdk init \
>     --plugins=ansible \
>     --domain=example.com
Writing kustomize manifests for you to edit...
Next: define a resource with:
$ operator-sdk create api
</pre>

Further, you can also check the folder listing and cat the file PROJECT
<pre>
(jegan@tektutor.org)$ <b>ls</b>
config  Dockerfile  Makefile  molecule  playbooks  PROJECT  requirements.yml  roles  watches.yaml
(jegan@tektutor.org)$ <b>cat PROJECT</b>
domain: example.com
layout:
- ansible.sdk.operatorframework.io/v1
plugins:
  manifests.sdk.operatorframework.io/v2: {}
  scorecard.sdk.operatorframework.io/v2: {}
  sdk.x-openshift.io/v1: {}
projectName: memcached-operator
version: "3"
</pre>

## Creating an API
```
operator-sdk create api \
    --group cache \
    --version v1 \
    --kind Memcached \
    --generate-role 
```
Expected output is
<pre>
(jegan@tektutor.org)$ operator-sdk create api \
>     --group cache \
>     --version v1 \
>     --kind Memcached \
>     --generate-role 
Writing kustomize manifests for you to edit...
</pre>

## Let's update the Ansible role

Currently the /roles/memcached/tasks/main.yml file will be empty
<pre>
(jegan@tektutor.org)$ <b>cat roles/memcached/tasks/main.yml</b>
---
# tasks file for Memcached
</pre>

Edit the /roles/memcached/tasks/main.yml and add the below coe
<pre>
---
- name: start memcached
  community.kubernetes.k8s:
    definition:
      kind: Deployment
      apiVersion: apps/v1
      metadata:
        name: '{{ ansible_operator_meta.name }}-memcached'
        namespace: '{{ ansible_operator_meta.namespace }}'
      spec:
        replicas: "{{size}}"
        selector:
          matchLabels:
            app: memcached
        template:
          metadata:
            labels:
              app: memcached
          spec:
            containers:
            - name: memcached
              command:
              - memcached
              - -m=64
              - -o
              - modern
              - -v
              image: "docker.io/memcached:1.4.36-alpine"
              ports:
                - containerPort: 11211
</pre>

## Update the default variable size to 1

Append the below line in roles/memcached/defaults/main.yml

```
size: 1
```

Currently the file config/samples/cache_v1_memcached.yaml looks as below
<pre>
(jegan@tektutor.org)$ <b>cat config/samples/cache_v1_memcached.yaml</b>
apiVersion: cache.example.com/v1
kind: Memcached
metadata:
  name: memcached-sample
spec:
  # TODO(user): Add fields here
</pre>

We need to edit as shown below
<pre>
(jegan@tektutor.org)$ cat config/samples/cache_v1_memcached.yaml
apiVersion: cache.example.com/v1
kind: Memcached
metadata:
  name: memcached-sample
spec:
  size: 3
</pre>

## Let's run the operator on your local system as a Go program
```
make install run
```

Expected output is
<pre>
(jegan@tektutor.org)$ <b>make install run</b>
/home/jegan/projects/memcached-operator/bin/kustomize build config/crd | kubectl apply -f -
customresourcedefinition.apiextensions.k8s.io/memcacheds.cache.example.com created
ANSIBLE_ROLES_PATH=":/home/jegan/projects/memcached-operator/roles" /home/jegan/projects/memcached-operator/bin/ansible-operator run
{"level":"info","ts":1653607617.8546693,"logger":"cmd","msg":"Version","Go Version":"go1.16.13","GOOS":"linux","GOARCH":"amd64","ansible-operator":"v1.16.0","commit":"560044140c4f3d88677e4ef2872931f5bb97f255"}
{"level":"info","ts":1653607617.8610969,"logger":"cmd","msg":"Watch namespaces not configured by environment variable WATCH_NAMESPACE or file. Watching all namespaces.","Namespace":""}
I0527 04:56:58.910368   35700 request.go:665] Waited for 1.020120093s due to client-side throttling, not priority and fairness, request: GET:https://api.ocp.tektutor.org:6443/apis/console.openshift.io/v1alpha1?timeout=32s
{"level":"info","ts":1653607620.3634233,"logger":"controller-runtime.metrics","msg":"metrics server is starting to listen","addr":":8080"}
{"level":"info","ts":1653607620.3642817,"logger":"watches","msg":"Environment variable not set; using default value","envVar":"ANSIBLE_VERBOSITY_MEMCACHED_CACHE_EXAMPLE_COM","default":2}
{"level":"info","ts":1653607620.3643806,"logger":"cmd","msg":"Environment variable not set; using default value","Namespace":"","envVar":"ANSIBLE_DEBUG_LOGS","ANSIBLE_DEBUG_LOGS":false}
{"level":"info","ts":1653607620.3644018,"logger":"ansible-controller","msg":"Watching resource","Options.Group":"cache.example.com","Options.Version":"v1","Options.Kind":"Memcached"}
{"level":"info","ts":1653607620.365774,"logger":"proxy","msg":"Starting to serve","Address":"127.0.0.1:8888"}
{"level":"info","ts":1653607620.3661122,"msg":"starting metrics server","path":"/metrics"}
{"level":"info","ts":1653607620.366202,"logger":"controller.memcached-controller","msg":"Starting EventSource","source":"kind source: cache.example.com/v1, Kind=Memcached"}
{"level":"info","ts":1653607620.3663027,"logger":"controller.memcached-controller","msg":"Starting Controller"}
{"level":"info","ts":1653607620.4667695,"logger":"controller.memcached-controller","msg":"Starting workers","worker count":48}
</pre>

## You need to login to your redhat account to authorize downloading redhat container images
```
docker login registry.redhat.io
```

<pre>
(jegan@tektutor.org)$ <b>docker login registry.redhat.io</b>
Authenticating with existing credentials...
Login did not succeed, error: Error response from daemon: Get https://registry.redhat.io/v2/: unauthorized: Please login to the Red Hat Registry using your Customer Portal credentials. Further instructions can be found here: https://access.redhat.com/articles/3399531
Username (youremail@gmail.com): <type-your-redhat-login>
Password: <type-your-redhat-password>
WARNING! Your password will be stored unencrypted in /home/jegan/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
</pre>

## Build the OpenShift operator image
```
make docker-build IMG=tektutor/memcached-openshift-operator:1.0 
```

## Troubleshooting version conflicts
You may get this kind of version conflict errors while building your operator image.

You need to edit the /home/jegan/projects/memcached-operator/requirements.yml and update the version to 0.4.0 as necessary.

<pre>
(jegan@tektutor.org)$ <b>make docker-build IMG=tektutor/memcached-openshift-operator:1.0</b>
docker build -t tektutor/memcached-openshift-operator:1.0 .
Sending build context to Docker daemon  85.69MB
Step 1/6 : FROM registry.redhat.io/openshift4/ose-ansible-operator:v4.10
v4.10: Pulling from openshift4/ose-ansible-operator
237bfbffb5f2: Already exists 
39382676eb30: Already exists 
a7635174fc67: Pull complete 
804449b22e26: Pull complete 
466a9b3ce4ae: Pull complete 
Digest: sha256:4bc6b9cde3a23bb9d8a75aa0feb31b71caf2b079775b936e39bd765d0b1249f6
Status: Downloaded newer image for registry.redhat.io/openshift4/ose-ansible-operator:v4.10
 ---> f4f5e47f0f23
Step 2/6 : COPY requirements.yml ${HOME}/requirements.yml
 ---> 1a872f2bf218
Step 3/6 : RUN ansible-galaxy collection install -r ${HOME}/requirements.yml  && chmod -R ug+rwx ${HOME}/.ansible
 ---> Running in 2021cd511478
Process install dependency map
ERROR! Cannot meet requirement operator_sdk.util:0.3.1 as it is already installed at version '0.4.0'. Use --force to overwrite
The command '/bin/sh -c ansible-galaxy collection install -r ${HOME}/requirements.yml  && chmod -R ug+rwx ${HOME}/.ansible' returned a non-zero code: 1
Makefile:80: recipe for target 'docker-build' failed
make: *** [docker-build] Error 1
</pre>

Another error that I encountered
<pre>
(jegan@tektutor.org)$ make docker-build IMG=tektutor/memcached-openshift-operator:1.0 
docker build -t tektutor/memcached-openshift-operator:1.0 .
Sending build context to Docker daemon  85.69MB
Step 1/6 : FROM registry.redhat.io/openshift4/ose-ansible-operator:v4.10
 ---> f4f5e47f0f23
Step 2/6 : COPY requirements.yml ${HOME}/requirements.yml
 ---> 13bfdc35caad
Step 3/6 : RUN ansible-galaxy collection install -r ${HOME}/requirements.yml  && chmod -R ug+rwx ${HOME}/.ansible
 ---> Running in 5ca298368e12
Process install dependency map
ERROR! Cannot meet requirement kubernetes.core:2.2.0 as it is already installed at version '2.2.3'. Use --force to overwrite
The command '/bin/sh -c ansible-galaxy collection install -r ${HOME}/requirements.yml  && chmod -R ug+rwx ${HOME}/.ansible' returned a non-zero code: 1
Makefile:80: recipe for target 'docker-build' failed
make: *** [docker-build] Error 1
</pre>

My updated requirements.yml file looks as below
<pre>
(jegan@tektutor.org)$ cat requirements.yml 
---
collections:
  - name: community.kubernetes
    version: "1.2.1"
  - name: operator_sdk.util
    version: "0.4.0"
  - name: kubernetes.core
    version: "2.2.3"
</pre>

Once you update the requirements.yml with the tool version installed on your system, you can expect the build go thru.

## Build your opetor image
```
```

Expected ouptut is

<pre>
(jegan@tektutor.org)$ <b>ake docker-build IMG=tektutor/memcached-openshift-operator:1.0</b>
docker build -t tektutor/memcached-openshift-operator:1.0 .
Sending build context to Docker daemon  85.69MB
Step 1/6 : FROM registry.redhat.io/openshift4/ose-ansible-operator:v4.10
 ---> f4f5e47f0f23
Step 2/6 : COPY requirements.yml ${HOME}/requirements.yml
 ---> e022b262f13f
Step 3/6 : RUN ansible-galaxy collection install -r ${HOME}/requirements.yml  && chmod -R ug+rwx ${HOME}/.ansible
 ---> Running in fafe325a28a8
Process install dependency map
Starting collection install process
Skipping 'community.kubernetes' as it is already installed
Skipping 'operator_sdk.util' as it is already installed
Skipping 'kubernetes.core' as it is already installed
Removing intermediate container fafe325a28a8
 ---> 94a6737f891d
Step 4/6 : COPY watches.yaml ${HOME}/watches.yaml
 ---> 127d8fc73381
Step 5/6 : COPY roles/ ${HOME}/roles/
 ---> 93855f5a5ecb
Step 6/6 : COPY playbooks/ ${HOME}/playbooks/
 ---> d269d0d3412a
Successfully built d269d0d3412a
Successfully tagged tektutor/memcached-openshift-operator:1.0
</pre>

## Login to your Docker Hub account
```
docker login
```

Expected output is
<pre>
(jegan@tektutor.org)$ <b>docker login</b>
Authenticating with existing credentials...
WARNING! Your password will be stored unencrypted in /home/jegan/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
</pre>

## Push your OpenShift operator image to your Docker Hub repository
In my case I already created a tektutor/memcached-openshift-operator public repository in my Docker Hub account.
```
docker push tektutor/memcached-openshift-operator:1.0
```

Expected output is
<pre>
(jegan@tektutor.org)$ docker push tektutor/memcached-openshift-operator:1.0
The push refers to repository [docker.io/tektutor/memcached-openshift-operator]
0c49a12a877a: Pushed 
75afd9f602f6: Pushed 
95d155708ffb: Pushed 
134e709b3ce9: Pushed 
2bf80cc44396: Pushed 
aac39aeb35c3: Pushed 
0606abea7f87: Pushed 
d96403e3cf8e: Pushed 
e767386b141e: Mounted from tektutor/controller 
35db14176a6c: Mounted from tektutor/controller 
1.0: digest: sha256:e0e0c28847be51e4a4fda927917a8c0d158c9c43293c6cb7b718f58f2c8c4077 size: 2412
</pre>

## Deploying our memcached-openshift-operator into the OpenShift cluster
```
make deploy IMG=tektutor/memcached-openshift-operator:1.0
```

Expected output is
<pre>
(jegan@tektutor.org)$ make deploy IMG=tektutor/memcached-openshift-operator:1.0
cd config/manager && /home/jegan/projects/memcached-operator/bin/kustomize edit set image controller=tektutor/memcached-openshift-operator:1.0
/home/jegan/projects/memcached-operator/bin/kustomize build config/default | kubectl apply -f -
namespace/memcached-operator-system created
customresourcedefinition.apiextensions.k8s.io/memcacheds.cache.example.com unchanged
serviceaccount/memcached-operator-controller-manager created
role.rbac.authorization.k8s.io/memcached-operator-leader-election-role created
clusterrole.rbac.authorization.k8s.io/memcached-operator-manager-role created
clusterrole.rbac.authorization.k8s.io/memcached-operator-metrics-reader created
clusterrole.rbac.authorization.k8s.io/memcached-operator-proxy-role created
rolebinding.rbac.authorization.k8s.io/memcached-operator-leader-election-rolebinding created
clusterrolebinding.rbac.authorization.k8s.io/memcached-operator-manager-rolebinding created
clusterrolebinding.rbac.authorization.k8s.io/memcached-operator-proxy-rolebinding created
configmap/memcached-operator-manager-config created
service/memcached-operator-controller-manager-metrics-service created
deployment.apps/memcached-operator-controller-manager created
</pre>

## Check your deployment in the cluster
```
oc get deploy -n memcached-operator-system
```

Expected output is
<pre>
(jegan@tektutor.org)$ <b>oc get deploy -n memcached-operator-system</b>
NAME                                    READY   UP-TO-DATE   AVAILABLE   AGE
memcached-operator-controller-manager   1/1     1            1           2m54s
</pre>

## Let's create a Custom Resource
```
oc apply -f config/samples/cache_v1_memcached.yaml
```

Expected output is
<pre>
(jegan@tektutor.org)$ pwd
/home/jegan/projects/memcached-operator

(jegan@tektutor.org)$ oc apply -f config/samples/cache_v1_memcached.yaml 
memcached.cache.example.com/memcached-sample created
</pre>

## Bundling an Operator and deploying with Operator Lifecycle Manager

We need to edit the Makefile with the image tektutor/memcached-openshift-operator:1.0 before proceeding
```
make bundle
```

Expected output is
<pre>
(jegan@tektutor.org)$ make bundle
operator-sdk generate kustomize manifests -q

Display name for the operator (required): 
> tektutor-memcached-operator

Description for the operator (required): 
> TekTutor's Memcached Openshift Operator

Provider's name for the operator (required): 
> tektutor

Any relevant URL for the provider name (optional): 
> https://medium.com/tektutor

Comma-separated list of keywords for your operator (required): 
> k8s,openshift,operator

Comma-separated list of maintainers and their emails (e.g. 'name1:email1, name2:email2') (required): 
> mail2jegan@gmail.com, jegan@tektutor.org
cd config/manager && /home/jegan/projects/memcached-operator/bin/kustomize edit set image controller=controller:latest
/home/jegan/projects/memcached-operator/bin/kustomize build config/manifests | operator-sdk generate bundle -q --overwrite --version 0.0.1  
INFO[0001] Creating bundle.Dockerfile                   
INFO[0001] Creating bundle/metadata/annotations.yaml    
INFO[0001] Bundle metadata generated suceessfully       
operator-sdk bundle validate ./bundle
INFO[0000] All validation tests have completed successfully 
</pre>



