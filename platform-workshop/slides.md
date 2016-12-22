## While you wait

If you want to use vagrant during this session
please start right away with downloading the
`LEAP/jessie` vagrantbox:

:thumbsup:

### vagrant box add LEAP/jessie

---

<img src="./images/kid-jumping.svg" width="20%" height="20%">

## LEAP Encryption Access Project
## Pixelated Project
### Platform Workshop

Kwadronaut (LEAP),  Varac (Pixelated, LEAP),   Zara (Pixelated)

```note
Why two projects ?
```

---

## LEAP Encryption Access Project

- "Provider in a box"
- VPN
- Encrypted email

```note
- VPN: Cirumvent censorship, surveillance and geoblocking
- Email: Transparent email encryption and keymanagement
```

---

## Pixelated

- Encrypted Webmail on top of LEAP

---

### Where to deploy to


Vagrant         | Remote Server
:-------------: | :-------------:
Locally on your Laptop, for testing | Out there, for testing or real
Requires Vagrant and Virtualbox or other hypervisor | Physical or paravirtualized Server (KVM, Xen, OpenStack, Amazon, but not VirtualBox or OpenVZ)

---


# Vagrant



```note
We'll show the vagrant installation,
and go through it step by step.
```

---

# Install Pixelated

- see https://github.com/pixelated/puppet-pixelated for details

```
vagrant ssh

cd /home/vagrant/leap/configuration/
mkdir -p files/puppet/modules
git clone https://github.com/pixelated/puppet-pixelated.git files/puppet/modules/pixelated

mkdir -p files/puppet/modules/custom/manifests
echo 'class custom { include ::pixelated::dispatcher }' > files/puppet/modules/custom/manifests/init.pp

leap deploy
leap deploy
leap test
```

---

### Local with Vagrant

- https://leap.se/en/docs/platform/tutorials/vagrant


### Remote Server

- https://leap.se/en/docs/platform/tutorials/single-node-email

---

