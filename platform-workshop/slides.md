***

<img src="./images/kid-jumping.svg" width="20%" height="20%">

# LEAP Encryption Access Project
## Provider installation workshop

```notes
Introduction:
  - working for LEAP since its start in 2012
```

---

<img src="./images/kid-jumping.svg" width="20%" height="20%">

# LEAP Encryption Access Project
## Provider installation workshop

Download the bitmask client: https://bitmask.net

---

<img src="./images/kid-jumping.svg" width="20%" height="20%">

# LEAP Provider installation workshop

If you want to use Vagrant during this session
please start right away with downloading the
"LEAP/jessie" vagrantbox:

```
vagrant box add LEAP/jessie
```

***

<img src="./images/kid-jumping.svg" width="20%" height="20%">

# LEAP Encryption Access Project

@ Anarchist Assembly, Hall 2, Komona Cluster
IRC: #leap @ irc.freenode.net

---


# What to expect

- Short introduction to LEAP
- Install LEAP provider: VPN or encrypted Email (or both if time allows) 
- Test provider using Bitmask client (Android, Mac, Linux, sorry no Windows so far)

```note
- Ask who wants to setup a provider, and what services they are interested in
- Note: Focus on encrypted mail, VPN: Requires a second IP
- Rush through the first part, then show more details during deploy phase (~20 mins)
```

***
<img src="./images/kid-jumping.svg" width="20%" height="20%">

# Introduction to LEAP

---

# Goals

- "Provider in a box"
- Make encryption as easy to use as possible
- Strict client encryption

---

# Increase User experience

<img src="./images/pizarra.jpg">

---

# Protect the provider

<video width="800" controls="controls" loop src="../video/fbi.mp4"></video>

https://mayfirst.org/en/2012/fbi-returns-server/


---

# What we have

- Bitmask client: A client that works smoothly with any LEAP provider.
- LEAP Platform:  A toolkit to make it easy for you to run a federated service provider.
- New protocols:  So that users don't need to trust the provider.

---

# Current Services: VPN

- Route all your internet traffic through an encrypted channel.
- Prevent eavesdropping (thiefs in the public network, police, ...).
- Circunvent censorship, surveillancec and geoblocking
- Prevent leaks (DNS, IPv6, ...).

---

# Current Services: email

- Transparent end-to-end encryption using OpenPGP.
- Automatic key discovery and validation.
- Service provider has no access to user data.
- Strong protection for metadata, whenever possible.
- Cloud synchronized for high availability on multiple devices.

---

# Bitmask client

<img src="./images/bitmask-hex.svg" width="20%" height="20%">

- Currently available for Android (VPN) and Linux (VPN + Email)
- Windows and MacOS coming soon (with your help even faster!)
- Formerly Python 2, Twisted and QT
- Rewritten with Python 2, Twisted and Javascript (React)

***
***

# Bitmask client
## VPN 


<img src="./images/bitmask-dev-demo1.png">

---

# Bitmask client
## VPN 


<img src="./images/bitmask-dev-demo2.png">

---

# Bitmask client
## VPN 


<img src="./images/bitmask-dev-demo3.png">

---

# Bitmask client
## VPN 

```
--- ~ » curl -s ipinfo.io
{
  "ip": "198.252.153.83",
  "hostname": "No Hostname",
  "city": "Seattle",
  "region": "Washington",
  "country": "US",
  "loc": "47.6062,-122.3321",
  "org": "AS16652 Riseup Networks",
  "postal": "98194"
}
```

---

# Bitmask for Android
## VPN

<img src="./images/bitmask-android.png">

***
***

# Bitmask client
## Encrypted Mail


<img src="./images/bitmask-dev-mail1.png">

---

# Bitmask Mail

<img src="./images/bitmask-dev-mail2.png">


```notes
- Integrated Mailclient using the Pixelated Useragent
- Not maintained anymore
- Migrating to Nylas Mail
```

---
# Bitmask Mail

<img src="./images/bitmask-dev-bitmask-mail.png">


---
# Bitmask Mail
## Composing

<img src="./images/bitmask-dev-bitmask-mail-compose.png">


***

***

# Key management

- Automated keylookup and validation.

---

# Keys, Keys, Keys

```
--- » gpg --search-keys snowden
gpg: data source: https://ntzwrk.org:443
(1)	Snowden
	  4096 bit RSA key 0xE941A4612E67D76A, created: 2017-03-24
(2)	This Is Snowden
	  4096 bit RSA key 0xBB44DF1AFC479844, created: 2017-03-20
(3)	Edward Snowden <trump2020buildawall@gmail.com>
	  4096 bit RSA key 0xA15DD46C59051BDB, created: 2017-03-12, expires: 2022-03-11
(4)	Edward Snowden <trump2020buildawall@gmail.com>
	  4096 bit RSA key 0xE64ECB1548116AEB, created: 2017-03-10, expires: 2022-03-09
(5)	Snowden <sfogert@gmail.com>
	  3072 bit RSA key 0xE643E968226937A1, created: 2017-03-10
(6)	Edward Snowden <joshing@protonmail.com>
	  4096 bit RSA key 0x2C3C1EFA83946932, created: 2017-01-20, expires: 2021-01-20
(7)	Edward Snowden (Very secret) <ed_snowden2016@outlook.com>
	  2048 bit RSA key 0xDC245D84A0F97A17, created: 2016-12-14
(8)	Edward Snowden
	  4096 bit RSA key 0xFAD43291D0951541, created: 2016-12-10
(9)	Edward Joseph Snowden <snowden@edwardsnowden>
	  4096 bit RSA key 0x34BD314D37015D55, created: 2016-11-02, expires: 2020-11-02
(10)	snowden <snowdenet@163.com>
	  3072 bit RSA key 0xFD764233079ACE40, created: 2016-10-11
(11)	Edvard Snowden <lordkott1987@gmail.com>
	  2048 bit RSA key 0xF5BE6495E2210CE1, created: 2016-10-07
Keys 1-11 of 146 for "snowden".  Enter number(s), N)ext, or Q)uit >
```

***
***
# LEAP Platform

- Configuration Management using puppet
- Installs and configures the servers
- leap_cli is the tool to deploy to the servers

---
# LEAP Platform Example: Setup single node email provider

```
sudo gem install leap_cli
leap new example --domain workshop.bitmask.net
cd example
leap add-user --self
leap cert ca
leap cert csr
leap node add workshop \
  services:couchdb,webapp,soledad,mx ip_address:1.1.1.3
leap init node
leap deploy
```

---

# LEAP Platform: Install and configure the server(s)

- Email: Postfix, spamassassin, clamav
- Database: couchdb, stunnel
- Webserver: apache
- Encrypting remailer: leap-mx
- Synchronisation: soledad
- Account management, issue tracking: leap-webapp
- Firewall: shorewall
- Monitoring: nagios, check_mk
- ...

***

# Server-side techstack

- PLatform: Puppet
- leap_cli: ruby
- leap_web: Ruby on Rails
- leap_mx, soledad: Python 2/Twisted

---

# Client-side techstack

- Bitmask client: Python 2, Twisted, React JS
- Bitmask Mail (a.k.a. Pixelated Useragent): Python 2, Twisted, FlightJS

---

# Soledad

- Acronym for "Synchronization Of Locally Encrypted Data Among Devices"
- Searchable client-encrypted synchronized database

***
# LEAP Webapp

- API for user registration and authentication
- User Management
- Integrated Issue Tracker
- Payment processing
- Customisable

---

# LEAP Webapp Main Page

<img src="./images/leap-webapp1.png" width="100%" height="100%">


---

# LEAP Webapp Account Management

<img src="./images/leap-webapp2.png" width="100%" height="100%">

***
<img src="./images/kid-jumping.svg" width="20%" height="20%">

# LEAP Encryption Access Project
## Platform Workshop

---
# System requirements 

- A remote sever/VM installed with fresh Debian jessie (!) OS
- Physical or paravirtualized Server (KVM, Xen, OpenStack, Amazon, but not VirtualBox or OpenVZ)
- Depending on the service 1-4 GB RAM, >3 GB disk space
- Able to login as root with ssh key
- Second public IPv4 (for VPN only)

```notes
- Please pair with your neighbour
- When you are stuck, pls tell us - if it can be fixed easily, great.
- If not, pls just continue to watch the demo,
  we can help you out later.
```
---

# Tutorials

- These slides: https://leap.se/slides/platform-workshop
- Quick VPN tutorial: https://leap.se/en/docs/platform/tutorials/single-node-vpn
---

# Install prerequisites

- Ruby
- leap-cli gem to manage your provider config on your workstation/laptop

```notes
- The Provider config contains secret key material which should not reside on the server for security reasons.
- Managing your server(s) happens from you laptop, you should only seldomly login to your servers for debugging.
- All commands shown here are run from the laptop.
```

---
# Ruby

## Debian / Ubuntu

```
$ apt install rubygems
```

## Mac OS

```
$ brew install ruby
```

```notes
- `$` indicates this command should be run on your laptop
```

---

# Install the LEAP command-line utility


```
$ sudo gem install leap_cli

$ leap --version
leap 1.9.2, ruby 2.3.3
```

***

# Create provider config

```
$ leap new --domain workshop.bitmask.net ./workshop
  Create directory /home/dev/workshop ? y
  = created /home/dev/workshop/

  The name of the provider: |Example| Workshop demo
  File path of the leap_platform directory: |/home/dev/leap_platform| 
  Default email address contacts: |root@workshop.bitmask.net| 

  The platform directory "/home/varac/dev/projects/leap/leap_platform" does not exist.
  Do you want me to create it by cloning from the
  git repository https://leap.se/git/leap_platform.git? y
  …  
```


```notes
- Just accept the default values
- The directory name doesn't mean anything
- Slides below only for cloning leap_platform with different branches
```

---

# leap_platform master branch build status

Leap Platform Build Status: [![Build Status](https://0xacab.org/leap/platform/badges/master/build.svg)](https://0xacab.org/leap/platform/commits/master)

see https://0xacab.org/leap/platform/

---


# Optional: Use latest release tag for stable version

If the build status of current leap_platform:master failed we need to checkout the last stable version of the leap_platform:


```
git clone -b version/0.10.0 https://leap.se/git/leap_platform \
  ../leap_platform
```
***

# Add your ssh key


```
$ leap user add --self
```

---

# SSL certificates

Create a SSL certificate authority and a certificate signining request:

```
$ leap cert ca
$ leap cert csr
```

```notes
- CSR can get used to buy a proper signed cert
- But letsencrypt is a better option for free, we can deploy proper LE certs
```

***

# Single node VPN provider

Tutorial:  https://leap.se/en/docs/platform/tutorials/single-node-vpn

```
$ export OPTS=(services:webapp,couchdb,openvpn openvpn.gateway_address:37.218.245.4)
```

```notes
- Next slides for optional email provider 
```

---

# Single node email provider

Tutorial:  https://leap.se/en/docs/platform/tutorials/single-node-email

```
$ export OPTS=(services:webapp,couchdb,soledad,mx)
```

***

# Generate diffie-hellman parameters for openvpn

```
$ leap cert dh
```

```notes
- Only needed for VPN 
```
***
# Add an existing remote server

```
$ leap node add blackbox ip_address:37.218.245.94 $OPTS
```

---

# Option B: Create a new server in the cloud

- Currently works only with AWS ec2
- `cloud.json` needed for AWS config and credentials
- https://leap.se/en/docs/platform/guide/virtual-machines for details

```
$ leap vm add blackbox services:webapp,couchdb,soledad,mx
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

***

# Time to deploy !

```
$ leap list

$ leap node init blackbox

$ leap deploy blackbox 
```

```notes

    unbuffer leap node init blackbox | ts
    unbuffer leap deploy blackbox | ts

- Email deploy: ~10 min on AWS, 15 min on Greenhost
- VPN deploy:    ~8 min on AWS, 13 min on Greenhost
- We'll setup DNS meanwhile
```

***


# DNS

```
leap compile zone
```

Use the listed entries in our DNS provider.

These are for workshop.bitmask.net (in this workshop's case):

```
@                     IN A      37.218.245.94
blackbox              IN A      37.218.245.94
api                   IN A      37.218.245.94
nicknym               IN A      37.218.245.94
@                     IN MX 10  blackbox
@                     IN TXT    "v=spf1 MX ip4:37.218.245.94 -all"
234072283e._domainkey IN TXT    "v=DKIM1;h=sha256;k=rsa;s=email;p=MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEApdCDTAuRJJa0yx8T3Z7d" "f2NLE0oOvKysLqHqtvJk92Zf8RHYO6/RzpvJ5s51fPfOfyLnAjEzGs3gBL5GkWNV" "hLyMB9TzYnuQ9lmnz3ep3Hyh8U9yPVmNu1YZDrMYGaeoHE6FZXkmvrtBUOv3XAZw" "4BNQwdcHCa/Z9iWgMDtBx0h+56DRDTOrJvr7M/7qGxknBo0FnnQ/Qhw9GQjkTg0h" "UmFZjuvx3BmgN/9lCMkrjxC7qfADvGYMIYer3iPt0wI7cqAvgWN0a+7iqm2PU+aB" "wLPWOSmWsl3e6wzHW4jFS7EchilGXjHiGQ5WC9anRC6WWr3SomL/cxKZNCjTCfBy" "dwIDAQAB"
```

---

# DNS
## Option A: Fake DNS for new provider 

We are using a domain here without proper DNS, so we need to override our DNS resolution.

- Open another terminal and:
```
cd ~/workshop
leap compile hosts
```

You need to edit your `hosts` file with admin privileges and add the output of above command to it.

* Linux: `sudo editor /etc/hosts`
* MacOS: `sudo nano /etc/hosts`

see [Quick start tutorial/Setup DNS](https://leap.se/en/docs/platform/tutorials/quick-start#setup-dns) for details.

***

# Download Bitmask client

- Download Bitmask from https://bitmask.net
- Available for Linux, Android, MacOS

```notes
- Ubuntu Artful broken
- Download takes a bit (75mb), so we start it before it's time for questions ?
- Any potential Windows contributors ?
```

# Questions ?

---

# Let's encrypt certificates

For proper, free-of-cost TLS certificates issued
by https://letsencrypt.org/:

```
$ leap cert register
$ leap cert renew workshop.bitmask.net
$ leap deploy --tags x509 --fast
```

Check https://workshop.bitmask.net in browser afterwards.

---

# Test if things work correctly

```
$ leap test
```

---

# Use Bitmask

- Extract downloaded Bitmask archive, and run ./bitmask-0.10.2/bitmask
- Add workshop.bitmask.net as a new provider
- Register a new user

```notes
Show:

- VPN

- Mail to myself
- Mail to/from other workshop participants
- Mail from outside `swaks -t varac@workshop.bitmask.net`
- Bitmask mail now Pixelated, migration to Nylas Mail client
…
```
---

# Try more

- LEAP Demo provider (Email): https://mail.bitmask.net

- LEAP Demo provider (VPN):   https://demo.bitmask.net

---

# Contribute

- Please consider to contribute - any help with QA or other is appreciated !  :heart:

- User experience / QA
- Python / Twisted
- JS / React
- MacOS
- Windows
- Puppet

https://leap.se/en/docs/get-involved
https://leap.se/en/docs/get-involved/project-ideas

```notes
- Short of funding, looking for contributors
- Show get involved and project ideas website
```

---

# Thanks!

- LEAP Encryption Access Project: [https://leap.se](https://leap.se)
- Bitmask Application: [https://bitmask.net](https://bitmask.net)
- Github: [https://github.com/leapcode](https://github.com/leapcode)
- Twitter: [https://twitter.com/leapcode](https://twitter.com/leapcode)
- IRC: #leap@freenode
- Come by: Anarchist Assembly, Hall 2, Komona Cluster

***

# Etc


---

# Bitmask Schema

<img src="./images/schema.jpg">
