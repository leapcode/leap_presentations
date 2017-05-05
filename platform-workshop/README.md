## LEAP Platform Workshop


# Generate slides

    reveal-ck generate


# Known Issues / Things to be aware of during presentation

- keylookup for @leap.se keys doesn't work
- Until we have an RDNS entry for blackbox.workshop.bitmask.net, riseup won't accept mails

# Present

- Recreate blackbox.workshop.bitmask.net server from [portal.eclips.is](https://portal.eclips.is/portal/cloud/instance/console?id=1690):
  - Stop instance
  - [Reinstall](https://portal.eclips.is/portal/cloud/Instance/reinstall?id=1690)


Upload final slides and share URL https://leap.se/slides/platform-workshop

    rsync -avz ~/leap/git/leap_presentations/platform-workshop/slides/ website@hare.leap.se:slides/platform-workshop

DNS is already setup for `workshop.bitmask.net`

    rm -rf ~/leap/workshop.bitmask.net ~/.leap/pixelated

# Todo

## Nice to have 

- update LEAP/jessie so `leap node init` doesnt take so long
- Use custom header/footer for all slides
- explain ssl certs foo better

- Next time: Add a VPN node ?

## Update Docuementation

- https://leap.se/en/docs/platform/guide/virtual-machines  `leap vm start mynode` not needed anymore
