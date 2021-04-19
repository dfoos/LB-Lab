# LB-Lab
Vagrant/Ansible project to build simple LB Lab

This is a simple project to create a LB/webserver lab environment using Vagrant and Ansible.
It creates three ubuntu servers one running haproxy and the other two running apache.  The load balancer can be reached at http://10.0.0.10 and can be tested by shutting down the apache node servers.
