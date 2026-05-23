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

## sops-age

Cross-project SOPS recipient public key — usable as `recipient:` in any `.sops.yaml` where Istvan Darvas is an authorized decryptor (e.g., the Maia platform's `_local/k3s/maia-{dev,uat}/.sops.yaml`).

| File | SHA-256 (file) | Public key | Type | Status | Since |
|------|----------------|------------|------|--------|-------|
| `sops-age/darvas_istvan.age.pub` | `7f32933f02c62a8f002eb01662a958bfb8e1d22811bd84c3f4d46d919dab9b1c` | `age1v2xjavmsd4k8ntsugaxxkpa539uxemp4gjknvnnselxwylx5g4lsj3jswv` | X25519 (age) | ACTIVE | 2026-05-23 |

```sh
curl -fsSL -o darvas_istvan.age.pub \
  https://raw.githubusercontent.com/fireking77/public-trust/main/sops-age/darvas_istvan.age.pub
echo "7f32933f02c62a8f002eb01662a958bfb8e1d22811bd84c3f4d46d919dab9b1c  darvas_istvan.age.pub" | sha256sum -c
```
