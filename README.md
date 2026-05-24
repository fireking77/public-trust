# public-trust

Public verification material — signing **public keys**, fingerprints, and
verification instructions — for software published by **Istvan Darvas**
(System Architect / Platform Engineer / Data Engineer / DevOps,
<https://www.linkedin.com/in/istvandarvas/>).

> This repository contains **only public, non-sensitive material** — never
> private keys, secrets, tokens, or source. (Stated once, here.)

## Why

Release artifacts (images, Helm charts) are published publicly; their source
repositories are private by design. A signature is only meaningful if the
verifier gets the signer's public key from a channel **independent of the
signed artifact** — this repository, cross-checked against the maintainer's
public identity above. Pin the fingerprint from `FINGERPRINTS.md`, then verify.

## Index

### Artifact signing (cosign)

| Project | Where |
|---------|-------|
| maia — images + Helm chart | [`artifact-signing/maia/`](artifact-signing/maia/) |

### SSH

Authorized public keys — together mirror `github.com/fireking77.keys`.

| Key | Where |
|-----|-------|
| RSA 2048 (`darvas.istvan@DESKTOP-NBQDMG5`) | [`ssh/darvas_istvan.pub`](ssh/darvas_istvan.pub) |
| ED25519 (`darvas.istvan@gmail.com 20260524`) | [`ssh/darvas_istvan_20260524.pub`](ssh/darvas_istvan_20260524.pub) |

### SOPS (age recipient)

| Key | Where |
|-----|-------|
| Cross-project SOPS recipient public key (X25519) | [`sops-age/darvas_istvan.age.pub`](sops-age/darvas_istvan.age.pub) |

### Reference

- Pin list (all fingerprints) — [`FINGERPRINTS.md`](FINGERPRINTS.md)
- Key rotation & contact — [`SECURITY.md`](SECURITY.md)

## Contact

Istvan Darvas — <https://www.linkedin.com/in/istvandarvas/>, or an issue here.
