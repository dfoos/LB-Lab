# LB-Lab
Vagrant/Ansible project to build simple Ubuntu/Apache/HAProxy Lab

This is a simple project to create a load balancer/webserver lab environment using Vagrant and Ansible.
It creates three ubuntu servers one running HAProxy and the other two running Apache.  The load balancer can be reached at http://10.0.0.10 and can be tested by refreshing the page or shutting down the individual Apache node servers.
