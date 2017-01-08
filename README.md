#A simple, yet ready to use Opennebula ansible playbook.

Be aware that these playbooks use submodules. Issue
```
$ git submodule update --recursive
```
when needed

 - Requirements: A Centos-7 machine with a passwordless sudo user "centos", authenticating with keys.

 - Edit "inventory" file to point your TargetHost's ip-address

Now we have a "centos" login with a predefined password and your key
 - Edit "vars" sections in opennebula.yml. Ensure the "masquerade_ext_if" is your physical interface, connected to the internet.
 - $ ansible-playbook -i inventory opennebula.yml
 - Grab your openvpn certificates at /etc/openvpn, connect to openvpn
 - # su oneadmin 
 - $ cd 
 - $ cat ~/.one/one_auth
 - $ EDITOR=vim oneuser update oneadmin
Add a new line like the following to the template:
SSH_PUBLIC_KEY="ssh-rsa AAAAB3NzaC1kc3MAAACBANBWTQmm4Gt..."
Multiple public ssh keys can be bundled into a single string
 - Proceed to Sunstone dashboard http://TargetHost:9869/
 - Virtual Resource -> Virtual Machines -> "+". Wait for VMs creation.
 - Login to your Centos7 VM as root: $ ssh root@10.0.0.10
