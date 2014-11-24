## How to play with this Ansible-Playbook

You should have Ansible installed on your machine.
You should have Vagrant and Virtual Box installed on your machine.

First checkout this repository into an folder on your machine.
Change directory into created directory.

Start up the vagrant machines with `vagrant up`.
Both machines are setup with fixed names and ips (ansible:10.10.10.30) (ansible2:10.10.10.31).

Create an user `siggi` with password `siggi` on both machines. For that login to the machines
as `vagrant` with password `vagrant`. That's a sudoer, so the command should be:

```
sudo adduser siggi

follow the dialog
...

```

Add your public ssh-key to `siggi`s authorized_keys file for passwordless ssh-connections.

```
cat ~/.ssh/id_rsa.pub | ssh siggi@10.10.10.30 "mkdir ~/.ssh; cat >> ~/.ssh/authorized_keys"
```

Try out accessing both machines with

```
ssh siggi@10.10.10.30
```

You should not be asked to provide an password.

Then you are ready to start.

Use the following command to setup the complete staging-environment:

```
ansible-playbook -i hosts setup.yml
```

You should see some colored output on console. Green is good, Yellow shows changes, Blue shows that things were skipped, Red is bad.
