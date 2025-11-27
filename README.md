Ansible Automation Platform Daily Demo for F5
=========
A demo designed to build the F5 Infrastructure needed to showcase many of the use cases related to F5.  This builds a standalone F5 at Amazon and sets the admin password so you will be ready to go when the playbook is done building the infrastructure.

Notes
=========
1. This demo is designed to work with the Red Hat Demo Platform. Please see the aap.as.code repo below. [aap.as.code](https://github.com/ericcames/aap.as.code "aap.as.code")
2. This demo works with Amazon only currently.
3. Must accept Terms and conditions at this link while logged into the AWS environment before running this. https://aws.amazon.com/marketplace/pp?sku=c5mtwrozlfns1fnawk1nvx2dh
![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/f5optin.png "Terms")

Day 0 - Configuration as code (CAC)
=========
Configuration as code give you an easy way to recover/move your ansible related artifacts to a new platform.  That includes your hardcoded credentials.  The hardcoded credentials can be safely vaulted in an ansible vault file.  Check out the setup_demo.yml for the configurations for setting up this demo using configuration as code.

[Setup - F5 Daily Demo - CAC](https://github.com/ericcames/aap.dailydemo.F5/blob/main/playbooks/setup_demo.yml "Setup - F5 Daily Demo - CAC")<br>

Extra Vars
```
my_vault: Eric Ames
timezone_id: America/Phoenix
my_remote_vault: >-
  https://raw.githubusercontent.com/ericcames/sourcefiles/refs/heads/main/vault_ames.yml
my_remote_ssh_pub_key: >-
  https://raw.githubusercontent.com/ericcames/sourcefiles/refs/heads/main/id_rsa.pub
```

Day 1 - Infrastructure as code (IAC)
=========
# Deploy the infrastruture we need for the demo

"Run workflow for the f5 Daily Demo" to setup the needed infrastructure for the demo<br>
![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/f5wf.png "The workflow")

# The F5 User Interface

![Check out the readme in the git repo](/images/F5uipre.png)
![Check out the readme in the git repo](/images/F5uipost.png)

**The job logs contain the URL needed to login to the gui**
![Check out the readme in the git repo](/images/f5joblog.png)

```
https://ec2-54-67-87-75.us-west-1.compute.amazonaws.com:8443
```
# The command line; there's no place like home :-)

![Check out the readme in the git repo](/images/F5cli.png)

Example login using your ssh key that was shared with Amazon
```
ssh admin@ec2-54-67-87-75.us-west-1.compute.amazonaws.com
```

**The AAP Managed Inventory**

![Check out the readme in the git repo](/images/F5inventory.png)<br>

Group name
```
f5demo
```

**The Cleanup Schedule**
![Check out the readme in the git repo](/images/F5cleanup.png)<br>

Day 2
=========

**The Playbooks**

[F5 -0- AWS -Gather specific facts](https://gitlab.com/mlowcher/F5_examples/-/blob/master/0_bigip_facts.yml?ref_type=heads "F5 -0- AWS -Gather specific facts")<br>
[F5 -1- AWS -Import certificate and key](https://gitlab.com/mlowcher/F5_examples/-/blob/master/1_bigip_cert_key_import.yml?ref_type=heads "F5 -1- AWS -Import certificate and key")<br>
[F5 -2- AWS -Add custom HTTP profile](https://gitlab.com/mlowcher/F5_examples/-/blob/master/2_create_http_profile.yml?ref_type=heads "")<br>


**Execution Environment**<br>
- [F5_ee](https://quay.io/locust61/f5_ee:0.1 "F5 Execution Environment")
```
quay.io/locust61/f5_ee:0.1
```
f5-execution-environment.yml
```
---
version: 3

images:
  base_image:
    name: registry.redhat.io/ansible-automation-platform-24/ee-minimal-rhel8:latest

dependencies:
  galaxy:
    collections:
      - f5networks.f5_modules
      - f5networks.f5_bigip
      - ansible.netcommon
  system:
    - pkgconf-pkg-config [platform:rpm]
    - systemd-devel [platform:rpm]
    - gcc [platform:rpm]
    - python39-devel [platform:rpm]
  python:
    - packaging
    - requests[security]
    - xmltodict
    - msgraph-sdk==1.0.0
    - psycopg2-binary
    - urllib3==1.26.15
options:
  package_manager_path: /usr/bin/microdnf
```

**A Network Credential is reguired for Day 2 ops**

![Check out the readme in the git repo](/images/F5networkcred.png)<br>


Looking for other Daily Demos?
=========

- [AAP Daily Demo Windows](https://github.com/ericcames/aap.dailydemo.windows "AAP Daily Demo Windows")
- [AAP Daily Demo Linux](https://github.com/ericcames/aap.dailydemo.linux "AAP Daily Demo Linux")
- [AAP Daily Demo F5](https://github.com/ericcames/aap.dailydemo.F5 "AAP Daily Demo F5")
- [AAP Daily Demo Panos](https://github.com/ericcames/aap.dailydemo.Panos "AAP Daily Demo Panos")
- [AAP Daily Demo Satellite](https://github.com/ericcames/aap.dailydemo.satellite "AAP Daily Demo Satellite")