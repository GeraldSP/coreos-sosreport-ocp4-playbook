# coreos-sosreport-ocp4-playbook


This repos is based on the following contribution:

https://gist.github.com/blemmenes/1ec380a1e214a38d5aa69db30e83ab71

## Prepare
Clone this repo, 
Fill up the inventory file with openshift hosts, beware of ssh key based authentication, please configure your ansible inventory acordingly. 

this playbooks was tested with ansible 2.9
~~~
[ocp4@ocp-bastion01 ~]$ ansible --version
ansible 2.9.9
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/home/ocp4/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /bin/ansible
  python version = 2.7.5 (default, Sep 26 2019, 13:23:47) [GCC 4.8.5 20150623 (Red Hat 4.8.5-39)]
~~~

## Execute

~~~
 [ocp4@ocp-bastion01 ~]$ cd coreos-sosreport-ocp4-playbook/
 [ocp4@ocp-bastion01 coreos-sosreport-ocp4-playbook]$ mkdir -p sos-report-must-gather-drp
 [ocp4@ocp-bastion01 coreos-sosreport-ocp4-playbook]$ ansible-playbook -i inventory gather-sosreport.yaml -e "dest=/home/ocp4/coreos-sosreport-ocp4-playbook/sos-report-must-gather-drp name=drp-sos-report case_id=123456"
~~~


## Upload the sosreports to your Red Hat Support Case

~~~
 [ocp4@ocp-bastion01 coreos-sosreport-ocp4-playbook]$ cd sos-report-must-gather-drp/123456/
 [ocp4@ocp-bastion01 123456]$ redhat-support-tool addattachment -c 123456 sosreports-02810690_20201125031220.tgz
~~~