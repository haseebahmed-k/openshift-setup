# openshift-setup-locally

# Setup docker

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -

add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

apt-get update -y
apt-get install docker-ce -y

**check the status of docker and make confirm that it is active.

systemctl status docker

**move to folder opt.
cd /opt

# Install open shift from github.

wget https://github.com/openshift/origin/releases/download/v3.9.0/openshift-origin-client-tools-v3.9.0-191fece-linux-64bit.tar.gz

tar -zvxf openshift-origin-client-tools-v3.9.0-191fece-linux-64bit.tar.gz

*** After installation move to the openshit folder.

cd openshift-origin-client-tools-v3.9.0-191fece-linux-64bit
cp oc /usr/local/bin/

*** check out openshift version.
oc version

*** open the filer daemon.json and add few json lines and save it.

nano /etc/docker/daemon.json

add the following lines:

{
    "insecure-registries" : [ "172.30.0.0/16" ]
}

save file.

**** restart docker service.

systemctl restart docker

# Start oc server
**** start oc server by provide your id appress.

oc cluster up --public-hostname= your ip address.

*** login as admin.

oc login -u system:admin

*** Make default project in openshift.

oc project default

*** Check oc status and copy the url .

oc status

# Login
**** Login as 
username : developer
password : developer.
