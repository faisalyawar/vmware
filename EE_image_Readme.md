#Steps to create AWX-EE image using Ansible builder
#python version should be 3.8 or above
#Create a directory
mkdir ~/ansible-builder && cd ~/ansible-builder
python -m venv builder
source builder/bin/activate

#install ansible & ansible-builder package
pip3 install ansible
pip3 install ansible-builder


#create below files if any collection,python package or any software need to be installed in the image
requirement.yml: Ansible-galaxy collection to install
requirements.txt : python dependencies to install


#cat requirements.yml
---
collections:
    - hpe.oneview
    - community.vmware
    - hpe.nimble
    - awx.awx


# cat requirements.txt
ansible==4.1.0
hpeOneView==7.2.0
pyvmomi==7.0.3
redfish==3.1.7
hpe3par-sdk==1.2.2
python-ilorest-library==3.5.0.2
psutil==5.9.2
nimble-sdk==1.2.1

  
#create execution-environment.yml with below data
---
version: 1
dependencies:
  galaxy: requirements.yml
  python: requirements.txt
additional_build_steps:
  append: |
    RUN pip3 uninstall pyOpenSSL -y && pip3 install pyOpenSSL==19.0.0
 

#run ansible-builder build command to start creating image for AWX-EE
ansible-builder build --tag <gitlab-container-registry-ip>/root/hpe-deployment-automation:latest --verbosity=3
