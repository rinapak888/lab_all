There are three virtual machines: web1, web2, rrobin.

Web1 and web2 servers should generate a custom page, and robin will configure load balancing of these servers in round-robin mode. 

To complete the tasks, you need to: install nginx on web 1, web 2, rrobin servers, web1 and web2 servers should work on port 8080, that is, you need to change the port, you need to make it so that when you log in to a custom page, it is clear which server we are on (web1 is 111 or web2 is 112), perform balancing of web1 and web2 servers, create a playbook in which we describe the roles of webservers (web1, web2) and rrobin.

This playbook will create a nginx rrobin balancing page for two pages (web1 and web2). 

Before the installation we will need a custom CentOS 7 virtualbox image with SElinux disabled. 

Let's start our virtual machines with Vagrant. Make sure you are using the latest version of vagrant (2.2.19).

## Post Installation

If have no errors on summary you can proceed to http://192.168.11.113 to see if your balancer works.