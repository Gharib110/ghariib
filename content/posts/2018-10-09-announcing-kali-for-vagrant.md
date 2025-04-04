---
title: "Announcing Kali for Vagrant"
date: Tue, 09 Oct 2018 00:00:00 +0000
draft: false
type: posts
---
# Announcing Kali for Vagrant

https://www.kali.org/blog/announcing-kali-for-vagrant/images/kali-on-vagrant.jpg



Inspired by a recent community blog post, we have decided to add a new official way for our community to use Kali. Starting now, you can find an officially maintained Kali Linux image in the Vagrant Cloud. What is Vagrant? From Vagrant&rsquo;s website: Vagrant is a tool for building and managing virtual machine

Inspired by a recent [community blog post](https://blog.secureideas.com/2018/09/automating-red-team-homelabs-part-1-kali-automation.html), we have decided to add a new official way for our community to use Kali. Starting now, you can find an officially maintained Kali Linux image in the [Vagrant Cloud](https://app.vagrantup.com/).

What is Vagrant?
----------------

From Vagrant’s [website](https://www.vagrantup.com/):

> Vagrant is a tool for building and managing virtual machine environments in a single workflow.

Put simply, with a single configuration file, you can download a base “box” and apply additional configurations like adding an additional network interface, setting the number of CPU cores and memory, or running a script on first boot. Even more importantly, all of this is contained in a configuration file, which is very easy to share compared to a virtual machine that spans many gigabytes.

### Getting Started

To get started, first install [Vagrant](https://www.vagrantup.com/) and [VirtualBox](https://www.virtualbox.org/). Then create an empty directory and from there run the following command:

```console
$ vagrant init kalilinux/rolling
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
```

This will create a file named **_Vagrantfile_**, which contains all the configuration options for the virtual machine. Every ‘vagrant’ command must be run from the directory containing that file. By default, it contains only the box name as well as many commented common options. We’ll review some of those later, but here is an excerpt:

```console
$ cat Vagrantfile
# -*- mode: ruby -*-
# vi: set ft=ruby :
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
# The most common configuration options are documented and commented below.
# For a complete reference, please see the online documentation at
# https://docs.vagrantup.com.
# Every Vagrant development environment requires a box. You can search for
# boxes at https://vagrantcloud.com/search.
config.vm.box = "kalilinux/rolling"
...
# Create a forwarded port mapping which allows access to a specific port
# within the machine from a port on the host machine. In the example below,
# accessing "localhost:8080" will access port 80 on the guest machine.
# NOTE: This will enable public access to the opened port
# config.vm.network "forwarded_port", guest: 80, host: 8080
...
end
```

Next, make sure you have enough disk space. The vagrant “box” (you can think of it as a template) uses around 4GB, and the spun up VM will take around 10GB or more depending on what you install inside. Then run this command:

```console
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Box 'kalilinux/rolling' could not be found. Attempting to find and install...
default: Box Provider: virtualbox
default: Box Version: >= 0
==> default: Loading metadata for box 'kalilinux/rolling'
default: URL: https://vagrantcloud.com/kalilinux/rolling
==> default: Adding box 'kalilinux/rolling' (v2018.3.1) for provider: virtualbox
default: Downloading: https://vagrantcloud.com/kalilinux/boxes/rolling/versions/2018.3.1/providers/virtualbox.box
...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Mounting shared folders...
default: /vagrant => /Users/woodbine/vagrant-boxes/kali
```

Vagrant will first download the box file if it’s not in its cache, then create the Kali VM and power it on. You will see the VirtualBox UI pop up so you can use Kali normally with the **root/toor** credentials. Vagrant veterans might notice that the VM is not headless, unlike most other Vagrant boxes. We have decided to show the GUI by default because many Kali tools require it. If you do not need the GUI, you can disable it in the **_Vagrantfile_** (see below for an example config) and run the following command to SSH to the machine as the **vagrant** user:

```console
$ vagrant ssh
Linux kali 4.18.0-kali1-amd64 #1 SMP Debian 4.18.6-1kali1 (2018-09-10) x86_64
The programs included with the Kali GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.
Kali GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
vagrant@kali:~$
```

This user has password-less sudo configured with the password **vagrant**, as per Vagrant conventions.

### Configuration

The VM comes with a NAT interface pre-configured, so you don’t need to edit the configuration to have Internet access from inside the VM. In addition, Vagrant will create a shared folder by default: the current directory on the host (the one containing the **_Vagrantfile_**) is available in the **_/vagrant_** directory of the guest. This directory allows you to keep data saved on the host, but easily accessible by the guest. This is a good practice, as it would allow you to quickly reset your Vagrant machine and never lose data.

Let’s see what more we can do with just a little configuration:

```ruby
# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
config.vm.box = "kalilinux/rolling"
# Create a forwarded port
config.vm.network "forwarded_port", guest: 80, host: 8080
# Create a private network. In VirtualBox, this is a Host-Only network
config.vm.network "private_network", ip: "192.168.33.10"
# VirtualBox specific settings
config.vm.provider "virtualbox" do |vb|
# Hide the VirtualBox GUI when booting the machine
vb.gui = false
# Customize the amount of memory on the VM:
vb.memory = "4096"
end
# Provision the machine with a shell script
config.vm.provision "shell", inline: <<-SHELL
apt-get update
apt-get install -y crowbar
SHELL
end
```

Add/uncomment the options inside the **_Vagrantfile_** then restart the machine with the following command for your changes to take effect:

```sh
vagrant reload
```

The provision script will only be run the first time the machine boots, but you can use one of these commands to re-run it:

```sh
vagrant provision # Provision the powered on VM
vagrant up --provision # When VM is powered off, power it on then provision
vagrant reload --provision # Reboot the VM then provision
```

Note that while it is possible to add a bridged network (called a “public network” in Vagrant), this is likely a bad idea as Vagrant is [insecure by default](https://www.vagrantup.com/docs/networking/public_network.html).

### Wrapping Up

We hope you find this new offering useful. We have shown a few simple things that you can do with Vagrant, but make sure to check out the [official documentation](https://www.vagrantup.com/docs/) for more configuration options and the [Vagrant Cloud](https://app.vagrantup.com/) for more boxes!

#### [Source](https://www.kali.org/blog/announcing-kali-for-vagrant/)

