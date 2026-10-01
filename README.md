# MASS4 brick registry

The static site behind `https://bricks.mass4.org/v1`, served by GitHub Pages. The format is specified in the Turian
repository's `docs/bricks/registry.md`.

```
CNAME                     the custom domain GitHub Pages serves this repository on
v1/index.json             the index of published bricks
v1/keys                   the registry's public key, which hosts built for MASS4 trust for org.mass4 and user bricks
v1/bricks/<id>/<version>/ the .brick files
mass4_ed25519.pub         the same public key as a plain OpenSSH line
```

Key fingerprint: `SHA256:EuuDyUXw5sI8RR/wvFpRhCAsu+n0m5G4jiL9CY0PVUA`

## Publishing a brick

Run from a checkout of this repository, with the registry's **private** key (never commit it):

```sh
turian-cli brick publish <brick folder> --registry . --key <path to private key> [--publisher-key <key> --claim <prefix>]
```

This packs the brick, copies it under `v1/bricks`, signs it and updates `v1/index.json`. Commit and push the result.

## DNS

Point `bricks.mass4.org` at GitHub Pages with a `CNAME` record to `mass4org.github.io`, then enable Pages for this
repository and turn on "Enforce HTTPS".
