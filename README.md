# vmware
### Create EE image using VMware collections
- To create AWX-EE image using Ansible builder
- Pre-Requisites:
   ```
   - Python 3.8 or Above
   - pip3 install ansible ansible-builder
   ```
- Create a directory with the `ansible-builder`
  ```
  - mkdir -p ~/ansible-builder
  - cd ~/ansible-builder
  ```
- Create a virtual environment and make to source.
  ```
  - python3 venv -m ansible_builder_venv
  - source ansible_builder_venv/bin/activate
  ```
