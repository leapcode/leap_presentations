## LEAP Platform Workshop


# Generate slides

    reveal-ck generate
    chromium-browser --temp-profile file:///home/varac/dev/projects/leap/git/leap_presentations/platform-workshop/slides/index.html

# Prepare presentation

DNS is already setup for `workshop.bitmask.net`, currently for 37.218.245.94 (blackbox, Amsterdam).
As fallback we can also use 37.218.240.130 (backblock-backup, hong kong)

- Recreate blackbox.workshop.bitmask.net server from [portal.eclips.is](https://portal.eclips.is/portal/cloud/instance/console?id=1692):
  - Stop instance
  - [Reinstall](https://portal.eclips.is/portal/cloud/Instance/reinstall?id=1692)

Upload final slides and share URL https://leap.se/slides/platform-workshop

    rsync -avz ~/leap/git/leap_presentations/platform-workshop/slides/ website@hare.leap.se:slides/platform-workshop

Start fresh

    rm -rf ~/.config/leap ~/.leap/pixelated  ~/workshop

# Todo

## Nice to have 

- Add mail/vpn service
- Code block wraps
- Anonymous feedback

- Use custom header/footer for all slides

## Update Docuementation

- https://leap.se/en/docs/platform/guide/virtual-machines  `leap vm start mynode` not needed anymore
