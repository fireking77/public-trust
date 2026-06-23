# WireGuard — peer public key

WireGuard interface **public key** for Istvan Darvas. A peer that wants to
establish a tunnel puts this value in the `[Peer]` block of its config:

```ini
[Peer]
PublicKey = DYe1gF4RGcjCkHlMJKbMdLb6ov7vOemEgQpEYWJMRnc=
# Endpoint / AllowedIPs are exchanged out of band
```

WireGuard has **no cipher negotiation** — every key is Curve25519 (X25519),
fixed; the data plane is ChaCha20-Poly1305 + BLAKE2s (Noise_IKpsk2). There is
nothing to choose and nothing to pin beyond the key value itself.

## Get + pin the key

```sh
curl -fsSL -o darvas_istvan.pub \
  https://raw.githubusercontent.com/fireking77/public-trust/main/wireguard/darvas_istvan.pub
echo "943c01e1f84b474eca5c417cf0b9e9082db8614e554fe3fa419d36915de0e10e  darvas_istvan.pub" | sha256sum -c
```

Active key fingerprint: `FINGERPRINTS.md`. Rotation policy: `SECURITY.md`.
