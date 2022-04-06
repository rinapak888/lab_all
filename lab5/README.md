![Снимок экрана от 2022-04-05 23-15-47](https://user-images.githubusercontent.com/89969193/161935161-ddf1eaf3-4a37-44ea-8dcd-8f1e3427a8ab.png)
![Снимок экрана от 2022-04-05 23-15-58](https://user-images.githubusercontent.com/89969193/161935167-50357a5d-77d5-4b73-82f0-2c00f84b64ff.png)

Install Nginx on web1, web2 servers. 

On haproxy1, haproxy2 servers, install and configure a fail-safe link between HAproxy and Keepalived. 

Configure VIP using Keepalived according to the scheme. On web1, web2 servers, Nginx should work on port 8080 and give a custom page, going to which you can understand which server you are on. On servers with HAproxy, the software should provide load balancing of web1 and web2 servers in round-robin mode. Make the response timeouts of web1 and web2 smaller, 1-2 seconds. Installation and configuration of all software should be provided by Ansible script. Upload all files for this task to Github and write a ReadMe with health screenshots and instructions for running your Ansible script.

To raise virtual machines, the command:

vagrant up

Command to run Ansible:

ansible-playbook index.yml

