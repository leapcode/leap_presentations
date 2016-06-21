<img src="./images/kid-jumping.svg" width="20%" height="20%">

# LEAP Encryption Access Project
## Platform Hands-On

```note
Notes during the presentation:

-
-

```

---

## Where to install ?

### Local with Vagrant

- https://leap.se/en/docs/platform/tutorials/vagrant

  (http://is.gd/NVNo6y)

- While you wait:

```bash
vagrant box add LEAP/jessie
```

### Remote Server

- https://leap.se/en/docs/platform/tutorials/single-node-email

  (http://is.gd/oqeWZw)

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

# Fix Pixelated

```
systemctl restart pixelated-dispatcher-manager.service
systemctl status pixelated-dispatcher-manager.service
```

put right fingerprint into `/etc/default/pixelated-dispatcher-manager` 

```
systemctl restart pixelated-dispatcher-manager.service
systemctl status pixelated-dispatcher-manager.service
```

```
systemctl restart pixelated-dispatcher-proxy.service
systemctl status pixelated-dispatcher-proxy.service
```


