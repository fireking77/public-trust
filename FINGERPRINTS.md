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

One file per authorized public key — together they mirror the key list at
<https://github.com/fireking77.keys>.

| File | SHA-256 (file) | ssh-keygen SHA256 | Comment | Type | Since |
|------|----------------|-------------------|---------|------|-------|
| `ssh/darvas_istvan.pub` | `a1df8780406ce96bd45bcf76347a797d936219d546d3d17f7e5ea442c3372f2a` | `SHA256:D7SMUaDxSBsbWMZUVJc/lRKNoIyC6oqAHLfJXBd4g84` | `darvas.istvan@DESKTOP-NBQDMG5` | RSA 2048 | 2026-05-19 |
| `ssh/darvas_istvan_20260524.pub` | `53d27401601a3f7ec8c50821987525fe29f85ce6500c41c0fcc0b5ab0755ef4a` | `SHA256:HSiYYDDRC8ofrPpulvKTUQ0nqgf/IkmjkT8G2PsM3Jk` | `darvas.istvan@gmail.com 20260524` | ED25519 | 2026-05-24 |

```sh
ssh-keygen -l -f ssh/darvas_istvan.pub
# 2048 SHA256:D7SMUaDxSBsbWMZUVJc/lRKNoIyC6oqAHLfJXBd4g84 darvas.istvan@DESKTOP-NBQDMG5 (RSA)

ssh-keygen -l -f ssh/darvas_istvan_20260524.pub
# 256 SHA256:HSiYYDDRC8ofrPpulvKTUQ0nqgf/IkmjkT8G2PsM3Jk darvas.istvan@gmail.com 20260524 (ED25519)
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

## wireguard

WireGuard interface public key — a peer puts this value in its `[Peer]
PublicKey = …` block. WireGuard has no cipher negotiation, so the key value is
the only thing to pin.

| File | SHA-256 (file) | Public key | Type | Status | Since |
|------|----------------|------------|------|--------|-------|
| `wireguard/darvas_istvan.pub` | `943c01e1f84b474eca5c417cf0b9e9082db8614e554fe3fa419d36915de0e10e` | `DYe1gF4RGcjCkHlMJKbMdLb6ov7vOemEgQpEYWJMRnc=` | Curve25519 (X25519) | ACTIVE | 2026-06-23 |

```sh
curl -fsSL -o darvas_istvan.pub \
  https://raw.githubusercontent.com/fireking77/public-trust/main/wireguard/darvas_istvan.pub
echo "943c01e1f84b474eca5c417cf0b9e9082db8614e554fe3fa419d36915de0e10e  darvas_istvan.pub" | sha256sum -c
```
