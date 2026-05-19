# maia — release verification

cosign key-pair signatures, **no transparency log** → consumer commands use
`--new-bundle-format=true --private-infrastructure=true` (cosign v3.x).

## Artifacts

- Helm chart: `oci://ghcr.io/fireking77/charts/maia` — version `0.1.0`
- Images (tag `v20260519-1458`): `ghcr.io/fireking77/maia-router`,
  `ghcr.io/fireking77/maia-hermes`, `ghcr.io/fireking77/maia-hermes-sidecar`

## 1 — get + pin the key

```sh
curl -fsSL -o cosign.pub \
  https://raw.githubusercontent.com/fireking77/public-trust/main/artifact-signing/maia/cosign.pub
echo "5f8971916aaf99377c83287f24e44e8cd4e5880ca8d380347beaa8b8560493c7  cosign.pub" | sha256sum -c
```

## 2 — pull (anonymous)

```sh
helm pull oci://ghcr.io/fireking77/charts/maia --version 0.1.0
```

## 3 — verify

Chart (signature + SBOM):

```sh
cosign verify             --key cosign.pub --new-bundle-format=true --private-infrastructure=true ghcr.io/fireking77/charts/maia:0.1.0
cosign verify-attestation --key cosign.pub --type spdxjson --new-bundle-format=true --private-infrastructure=true ghcr.io/fireking77/charts/maia:0.1.0
```

Each image (signature + SBOM + SLSA provenance):

```sh
for img in maia-router maia-hermes maia-hermes-sidecar; do
  ref="ghcr.io/fireking77/${img}:v20260519-1458"
  cosign verify             --key cosign.pub --new-bundle-format=true --private-infrastructure=true "$ref"
  cosign verify-attestation --key cosign.pub --type spdxjson      --new-bundle-format=true --private-infrastructure=true "$ref"
  cosign verify-attestation --key cosign.pub --type slsaprovenance --new-bundle-format=true --private-infrastructure=true "$ref"
done
```

Active key fingerprint: see `FINGERPRINTS.md`. Rotation policy: `SECURITY.md`.
