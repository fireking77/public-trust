# Fingerprints — the pin list

Trust these from an identity-bound channel (this repo, cross-checked against
<https://www.linkedin.com/in/istvandarvas/>), then pin before use.

## artifact-signing (cosign)

| Project | File | SHA-256 (file) | SPKI-SHA256 | Status | Since |
|---------|------|----------------|-------------|--------|-------|
| maia | `artifact-signing/maia/cosign.pub` | `5f8971916aaf99377c83287f24e44e8cd4e5880ca8d380347beaa8b8560493c7` | `b2c61f6a1b4425f45cfb33385d818c332b001d67fe37d8e35db2d8c772f39b21` | ACTIVE | 2026-05-19 |

```sh
curl -fsSL -o cosign.pub \
  https://raw.githubusercontent.com/fireking77/public-trust/main/artifact-signing/maia/cosign.pub
echo "5f8971916aaf99377c83287f24e44e8cd4e5880ca8d380347beaa8b8560493c7  cosign.pub" | sha256sum -c
```

## ssh

| File | SHA-256 (file) | ssh-keygen SHA256 | Comment | Type |
|------|----------------|-------------------|---------|------|
| `ssh/darvas_istvan.pub` | `a1df8780406ce96bd45bcf76347a797d936219d546d3d17f7e5ea442c3372f2a` | `SHA256:D7SMUaDxSBsbWMZUVJc/lRKNoIyC6oqAHLfJXBd4g84` | `darvas.istvan@DESKTOP-NBQDMG5` | RSA 2048 |

```sh
ssh-keygen -l -f ssh/darvas_istvan.pub
# 2048 SHA256:D7SMUaDxSBsbWMZUVJc/lRKNoIyC6oqAHLfJXBd4g84 darvas.istvan@DESKTOP-NBQDMG5 (RSA)
```
