## While you wait

If you want to use `Vagrant` during this session
please start right away with downloading the
`LEAP/jessie` vagrantbox:

:thumbsup:

### vagrant box add LEAP/jessie

---

<img src="./images/kid-jumping.svg" width="20%" height="20%">

## LEAP Encryption Access Project
## Pixelated Project
### Platform Workshop

Varac (LEAP, Pixelated)

```note
We'll briefly explain both projects later

```

---

## What to expect

- Have a LEAP provider installed, for real or for testing
- Focus on encrypted email (no VPN)

```note
- Rush through the first part, then show more details during deploy phase (~20 mins)
- VPN: Requires a second IP
```

---

## Prerequisites

- Have a working (!) Vagrant setup
  or a remote sever/VM installed with fresh Debian stable OS
- A public/private ssh keypair to login your host

```notes
- We cannot help you / debug your vagrant issues here
- Otherwise, please pair with your neighbour
- When you are stuck, pls tell us - if it can be fixed easily, great. If not, pls just continue to watch the demo,
  we can help you out later.
- Who wants to use vagrant/a remote sever ?
```

---

## LEAP Encryption Access Project

- "Provider in a box"
- VPN
- Encrypted email
- Strict client encryption

```note
- VPN: Cirumvent censorship, surveillance and geoblocking
- Email: Transparent email encryption and keymanagement
```

---

## Bitmask Client

<img src="./images/bitmask-dev-201612.png" width="50%" height="50%">

- Formerly Python/Twisted
- Currently rewritten with Python/Javascript
- Only for Ubuntu/Debian Linux (VPN+Email) or Android (VPN)
- Windows and MacOS coming soon (with your help even faster!)

---

## Pixelated

- Encrypted Webmail on top of LEAP
- No installation hassle
- Private key will be unlocked on server
- Looking for maintainers/contributors

---

## Where to deploy to


Vagrant         | Remote Server
:-------------: | :-------------:
Locally on your laptop, for testing | Out there, for testing or real
Requires Vagrant >= 1.5 and Virtualbox or other hypervisor | Physical or paravirtualized Server (KVM, Xen, OpenStack, Amazon, but not VirtualBox or OpenVZ)

---

# Tutorials

These slides: https://leap.se/slides/33c3/

## Vagrant

- https://leap.se/en/docs/platform/tutorials/vagrant


## Single node email provider

- https://leap.se/en/docs/platform/tutorials/quick-start
- https://leap.se/en/docs/platform/tutorials/single-node-email

---

# Install prerequisites

- Install leap-cli on your workstation/laptop, NOT on the server !

## Debian & Ubuntu

```
$ sudo apt install git ruby ruby-dev rsync \
    openssh-client openssl rake make bzip2
```

## Mac OS

```
$ brew install ruby-install
$ ruby-install ruby
```

```notes
- `workstation$` indicates this command should be run on your laptop
```

---

## Install the LEAP command-line utility


```
$ sudo gem install leap_cli

$ leap --version
leap 1.9, ruby 2.3.3
...

```

---

# Prepare provider config

Use `example.org` for testing, or pick your own domain.

```
$ mkdir -p ~/leap/example.org
$ cd ~/leap/example.org
```

---

# Checkout stable version of platform

Leap Platform Build Status: [![Build Status](https://0xacab.org/leap/platform/badges/master/build.svg)](https://0xacab.org/leap/platform/commits/master)
If the last build failed, we need to checkout the last stable version of the leap_platform:

```
git clone https://0xacab.org/leap/platform.git \
  ../leap_platform
git checkout -b 0.9.0 0.9.0
```

```notes

```

---

# Create provider config

```
$ leap new .

  The primary domain of the provider: |example.org|
  The name of the provider: |Example|
  File path of the leap_platform directory: |/home/varac/leap_platform|
  Default email address contacts: |root@example.org|
  The platform directory "/home/varac/leap/leap_platform" does not exist.
  Do you want me to create it by cloning from the
  git repository https://leap.se/git/leap_platform.git? y
  ...
```


```notes
Just accept the default values
```

---

# Add your ssh key


```
$ leap add-user varac --self
```

---

# SSL certificates

Create SSL certificate authority, to self-sign host certificates:

```
$ leap cert ca
$ leap cert csr
```

---

# Option A: Add your local vagrant node

```
$ leap node add --local wildebeest services:webapp,couchdb,soledad,mx
$ leap list

$ leap local start wildebeest
$ leap local status
```

---

# Option B: Add an existing remote server


```
$ leap node add wildebeest ip_address:0.1.2.3 \
  services:webapp,couchdb,soledad,mx
```

```notes

```

---

# Option C: Create a new server in the cloud

- Currently works only with AWS ec2
- `cloud.json` needed for AWS config and credentials
- https://leap.se/en/docs/platform/guide/virtual-machines for details

```
$ leap vm add wildebeest services:webapp,couchdb,soledad,mx
$ leap vm status
```

```notes
- Only reocmmended for testing

  `leap vm key-register` is needed if you haven't done it already

  cp ~/leap/git/bitmask/cloud.json .
  grep -v aws_ cloud.json
  leap vm status | ts

- Takes 4 mins to finish - questions ?
- Otherwise show next slide while bootstrapping VM,
  and help out with vagrant
```

---

# Time to deploy !

```
$ leap list

$ leap node init wildebeest
$ leap deploy wildebeest
```

```notes

    unbuffer leap node init wildebeest | ts
    unbuffer leap deploy wildebeest | ts

- Takes ~10 min to finish on AWS
- We'll setup DNS meanwhile
```

---

# Setup DNS

We are using a fake domain here, so we need to override our DNS resolution.

- Open another terminal and:
```
cd ~/leap/example.org
leap compile hosts
```

You need to edit your `hosts` file with admin privileges and add the output of above command to it.

* Linux: `sudo editor /etc/hosts`
* MacOS: `sudo nano /etc/hosts`

see [Quick start tutorial/Setup DNS](https://leap.se/en/docs/platform/tutorials/quick-start#setup-dns) for details.


---

# Questions so far ?

```notes
- Time for Q&A, explain more about platform
- We'll wait until deploy finishes
```

---

# Test if things work correctly

```
$ leap test
```

---

# Use Bitmask

- Register a user at https://example.org (accept self-signed provider cert)

```notes

Show:

- Mail to myself
- Mail to/from other workshop participants
- Mail from outside (cat swaks -t varac@example.org -s IP)
...
```
---

# Try more

- LEAP: https://mail.bitmask.net
- Bitmask: https://bitmask.net
- Pixelated: https://try.pixelated-project.org/ (no outbound mail)

---

# Contribute

- Please consider to contribute - any help with QA or other is appreciated !
:heart:

- UX
- Python / Twisted
- JS / React
- MacOS
- Windows
- Puppet

https://leap.se/en/docs/get-involved
https://leap.se/en/docs/get-involved/project-ideas

---

# Thanks!

- LEAP Encryption Access Project: [https://leap.se](https://leap.se)
- Bitmask Application: [https://bitmask.net](https://bitmask.net)
- Github: [https://github.com/leapcode](https://github.com/leapcode)
- Twitter: [https://twitter.com/leapcode](https://twitter.com/leapcode)
- https://pixelated-project.org/
- IRC: #leap@freenode
