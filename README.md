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

- create requirements.yml file in `ansible-builder` folder
  ```
  ---
  collections:
    - community.vmware
    - awx.awx
  ```
  - create requirements.txt file in `ansible-builder` folder
  ```
   ansible==4.1.0
   pyvmomi==7.0.3
   redfish==3.1.7
   python-ilorest-library==3.5.0.2
   psutil==5.9.2
  ```

  - Create execution-environment.yml in `ansible-builder` folder
    ```
      ---
      version: 1
      dependencies:
        galaxy: requirements.yml
        python: requirements.txt
      additional_build_steps:
        append: |
          RUN pip3 uninstall pyOpenSSL -y && pip3 install pyOpenSSL==19.0.0
    ```

  - Run the command with `ansible-builder`
    ```
    > ansible-builder build --tag /root/vmware-ee:latest --verbosity=3
    ```
