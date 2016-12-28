#HSLIDE?image=https://rawgit.com/leapcode/leap_presentations/master/rgsoc2016_leap_overview/images/kid-jumping.png
<!--
TODO:

- Could need some CSS polishing: https://github.com/gitpitch/gitpitch/wiki/Slideshow-Custom-CSS
-->

# LEAP Encryption Access Project

## LEAP Platform Overview

#HSLIDE

## LEAP Platform

- A toolkit to make it easy for you to run a federated service provider.

#HSLIDE

# LEAP Platform

- Configuration Management using puppet
- Installs and configures the servers
- leap_cli is the tool to deploy to the servers
- Provider confiduration is stored on admin laptop

#HSLIDE

# LEAP Platform Example: Setup single node email provider

```
sudo gem install leap_cli
leap new example --domain example.org
cd example
leap add-user --self
leap cert ca
leap cert csr
leap node add raspberry \
  services:couchdb,webapp,soledad,mx ip_address:1.1.1.3
leap init node
leap deploy
```

#HSLIDE

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

# HSLIDE

## Server-side techstack

- PLatform: Puppet
- leap_cli: ruby
- leap_web: Ruby on Rails
- leap_mx, soledad: Python Twisted

#HSLIDE

## Soledad

- Acronym for "Synchronization Of Locally Encrypted Data Among Devices"
- Searchable client-encrypted synchronized database

#HSLIDE

## Bonafide

- Secure user registration
- Authentication
- Password change
- etc.

#HSLIDE
## Current Services: VPN

- Route all your internet trafic through an encrypted channel.
- Prevent eavesdropping (thiefs in the public network, police, ...).
- Circunvent internet censorship.
- Prevent leaks (DNS, IPv6, ...).

#HSLIDE

## Current Services: email

- End-to-end encryption using OpenPGP.
- Automatic key discovery and validation.
- Service provider has no access to user data.
- Strong protection for metadata, whenever possible.
- Cloud synchronized for high availability on multiple devices.

#HSLIDE

## LEAP Webapp

- API for user authentication
- Help Tickets
- User Management
- Payment processing
- Customisable

#HSLIDE

## LEAP Webapp Main Page

![Image-Absolute](https://rawgit.com/leapcode/leap_presentations/master/rgsoc2016_leap_overview/images/leap-webapp1.png)


#HSLIDE

## LEAP Webapp Account Management

![Image-Absolute](https://rawgit.com/leapcode/leap_presentations/master/rgsoc2016_leap_overview/images/leap-webapp2.png)

#HSLIDE

## LEAP Webapp Ticket System

![Image-Absolute](https://rawgit.com/leapcode/leap_presentations/master/rgsoc2016_leap_overview/images/leap-webapp-tickets.png)

