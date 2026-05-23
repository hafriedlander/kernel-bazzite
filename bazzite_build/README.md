# BC250 40 CU unlock

This is the Bazzite R43 KDE Deck image, with one specfic customisation for the BC250 -
it includes the kernel patch from https://github.com/duggasco/bc250-40cu-unlock which
allows you to unlock all the CUs on the AMD BC250

This is cleaner than using `rpm-ostree override replace`, and doesn't end up with some
broken modules (xpadpro, the fan control module, etc).

# To install:

````
sudo rpm-ostree rebase ostree-unverified-registry:ghcr.io/hafriedlander/bazzite-deck-cu40:latest
```

Wait until it's done, then reboot, then:

```
sudo rpm-ostree rebase ostree-image-signed:docker://ghcr.io/hafriedlander/bazzite-deck-cu40:latest
```

Then reboot again.

# To use:

Check the old lamer videos, https://www.youtube.com/@OldLamer

Very brief, incomplete guide:

```
sudo systemctl disable cyan-skillfish-governor-smu.service

sudo rpm-ostree kargs --append=amdgpu.bc250_cc_write_mode=3
```

and if needed

```
sudo rpm-ostree kargs --append=amdgpu.disable_cu=0.0.4,0.1.4,1.0.4,1.1.4
```

# Can you make a Desktop version / Gnome version / help me get this working?

Nope.
