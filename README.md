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

## Layout

```
FINGERPRINTS.md            – the pin list (every key's SHA-256)
SECURITY.md                – key-rotation policy + contact
artifact-signing/maia/     – cosign key + exact verify commands for maia
ssh/darvas_istvan.pub      – authorized SSH public key (also at
                             https://github.com/fireking77.keys)
```

## Index

| Item | Where |
|------|-------|
| **maia** release verification (images + Helm chart) | [`artifact-signing/maia/`](artifact-signing/maia/) |
| Authorized SSH public key | [`ssh/darvas_istvan.pub`](ssh/darvas_istvan.pub) |

## Contact

Istvan Darvas — <https://www.linkedin.com/in/istvandarvas/>, or an issue here.
