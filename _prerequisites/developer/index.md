---
title: "Developer Prerequisites"
id: "developer-prerequisites"
---


#Pack Development Prerequisites
----------------

  The prerequisites for pack development is same as creating a new [component](#component)/[cookbook](#cookbook)

  * Ruby

```ruby
# Install RVM
$\curl -sSL https://get.rvm.io | bash
# Install Ruby
$ rvm install ruby-1.9.3
$ rvm use --default ruby-1.9.3
```
 * Get [circuit-oneops](https://github.com/oneops/circuit-oneops-1) source
 * Install [circuit](#../key-concepts/circuit)

```ruby
$ gem install --local oneops-admin-1.0.0.gem
```



# Component Dependencies

The following products and components are used by OneOps. Operating System | Version
--------- |---------
Linux  | Modern Linux distribution - Ubuntu, SUSE, RedHat, etc.
Apple Mac | OS X 10.11 (El Capitan) or newer recommended
Window | Windows 8.1 and newer

# Build Dependencies

Hardware | Minimum | Recommended
-------- |---------  |-----------
Memory | 12 Gb | 16 Gb or more
Disk Space | 40 Gb | 40 Gb or more
CPU | 4 x Cores | 8 x Cores or more

---
Component | Description
--------- | -----------
<a href="https://www.virtualbox.org/" target="_blank">VirtualBox</a> | Virtual Box 5 or newer
<a href="https://www.vagrantup.com/" target="_blank">Vagrant</a> | Vagrant 1.7.4 or newer
