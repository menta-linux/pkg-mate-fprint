# pkg-mate-fprint (Menta Linux)

Debian packaging of [KeremSoke/mate-fprint](https://github.com/KeremSoke/mate-fprint)
1.0.0 (tag `v1.0.0`), a Vala/GTK 3 fingerprint settings tool for MATE. Packaging written
from scratch (no Debian/Salsa package exists).

Version scheme: `<upstream>-1mentaN`, e.g. `1.0.0-1menta1`. Bump with `dch -i`.

Notes:
- Upstream has no Wayland or in-process options (it is a plain GTK application talking to
  fprintd over D-Bus), so there is nothing to switch on.
- The package ships a `pam-auth-update` profile (`/usr/share/pam-configs/mate-fprint`,
  `Default: yes`); `postinst`/`postrm` run `pam-auth-update --package`, as Debian
  policy for PAM profiles asks.

CI builds on every push to `master` and publishes the `.deb`s as the rolling `latest`
release; pushing a tag `menta/<version>` also creates a versioned release. CI clones the
upstream tag from the version in `debian/changelog`.
