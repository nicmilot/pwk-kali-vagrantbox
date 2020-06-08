# Vagrant box PWK Kali image 2018

- This vagrant box is for VMware Fusion.

## Why ?

So you have to understand that this is not my day to day Kali image. I use my vagrant box of Kali 2020.1 image (see links below). So why this ? First, because OffSec put some tools and others stuffs into the box that you may need sometimes. Second, when you attak a target in the lab and your tools have version problem, this box will probably solve it. So you can vagrant up, go take the right version of your tools and bring it into you personnel VM or you can use that box for this particular attack and you can destroy it after that.

## Almost no change

- No snapshot:
The PWK Kali 2018 come with a built-in snapshot if you want to revert the VM. Why I deleted it ? First, it cause problems when you try to package the new vagrant box. Second, I built this vagrant box to be able to easily destroy and create this image, so I dont want it anyway. Third, trying to make it smaller.

- New vagrant user:
Of course, like every other vagrant box.

- EVERYTHING else is the same.

## How to start

```bash
$ cd into-the-desire-folder
$ vagrant init nicmilot/pwk-kali-2018
$ vagrant up
$ vagrant ssh
# see Vagrantfile-Example if you want the GUI to open when vagrant up
# Going root
$ sudo su
$ cd
```

- You can also clone this repo if you want.

## After installation recommendation

- Change password of default user root. Default pass is: toor
- Change password of user vagrant. Default pass is: vagrant
- Reconfigure default SSH.

```bash
$ cd /etc/ssh
$ sudo dpkg-reconfigure openssh-server
$ sudo service ssh restart && sudo systemctl enable ssh
$ sudo service ssh status
```

It's good practice to change the default vagrant ssh key in /home/vagrant/.ssh/authorized_keys. But keep in mind if you do that you will need to update your Vagrantfile (see Vagranfile-Example).

```bash
$ cd /home/vagrant/.ssh
$ cp authorized_keys authorized_keys.old
$ echo "your new ssh public key" > authorized_keys
$ chmod 600 /home/vagrant/.ssh/authorized_keys
# vagrant halt, change your vagrantfile, vagrant up and test if everything works(vagrant ssh).
$ rm /home/vagrant/.ssh/authorized_keys.old
```

### Links

- OffSec PWK Kali 2018 - <https://support.offensive-security.com/pwk-kali-vm/>
- OffSec Kali VM 2020 (No "pwk version" for 2020. Looks like standard kali image) - <https://support.offensive-security.com/kali-vm/>
- My Vagrant box of Kali-PWK 2018 - <https://app.vagrantup.com/nicmilot/boxes/pwk-kali-2018>
- My Vagrant box of Kali 2020 (Kali 2020.1 image) - <https://app.vagrantup.com/nicmilot/boxes/kali-full-2020>
