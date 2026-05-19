# maia — release verification

cosign key-pair signatures, **no transparency log** → all consumer commands use
`--new-bundle-format=true --private-infrastructure=true` (cosign v3.x).

This page is **version-agnostic** — it applies to every maia release. Pick the
chart version / image tag you are installing; the signing key below verifies
all of them (until rotated — see `SECURITY.md`).

## Artifacts

- Helm chart (OCI): `ghcr.io/fireking77/charts/maia`
- Images: `ghcr.io/fireking77/maia-router`, `ghcr.io/fireking77/maia-hermes`,
  `ghcr.io/fireking77/maia-hermes-sidecar`

Image tags use the format `v<YYYYMMDD>-<HHMM>`. A chart version pins its
matching image tag in the chart's `appVersion`.

## 1 — get + pin the key (once; key is release-independent)

```sh
curl -fsSL -o cosign.pub \
  https://raw.githubusercontent.com/fireking77/public-trust/main/artifact-signing/maia/cosign.pub
echo "5f8971916aaf99377c83287f24e44e8cd4e5880ca8d380347beaa8b8560493c7  cosign.pub" | sha256sum -c
```

## 2 — choose the release you are verifying

```sh
CHART=ghcr.io/fireking77/charts/maia

# pick a chart version (latest, or a specific one):
CHART_VERSION="$(helm show chart "oci://${CHART}" | awk -F'"? *' '/^version:/{print $2}')"

# the image tag that chart pins:
IMAGE_TAG="$(helm show chart "oci://${CHART}" | awk -F'"? *' '/^appVersion:/{print $2}')"
```
(or set `CHART_VERSION` / `IMAGE_TAG` by hand to the release you intend to use.)

## 3 — pull (anonymous)

```sh
helm pull "oci://${CHART}" --version "${CHART_VERSION}"
```

## 4 — verify

Chart (signature + SBOM):

```sh
cosign verify             --key cosign.pub --new-bundle-format=true --private-infrastructure=true "${CHART}:${CHART_VERSION}"
cosign verify-attestation --key cosign.pub --type spdxjson --new-bundle-format=true --private-infrastructure=true "${CHART}:${CHART_VERSION}"
```

Each image (signature + SBOM + SLSA provenance):

```sh
for img in maia-router maia-hermes maia-hermes-sidecar; do
  ref="ghcr.io/fireking77/${img}:${IMAGE_TAG}"
  cosign verify             --key cosign.pub --new-bundle-format=true --private-infrastructure=true "$ref"
  cosign verify-attestation --key cosign.pub --type spdxjson      --new-bundle-format=true --private-infrastructure=true "$ref"
  cosign verify-attestation --key cosign.pub --type slsaprovenance --new-bundle-format=true --private-infrastructure=true "$ref"
done
```

Active key fingerprint: `FINGERPRINTS.md`. Rotation policy: `SECURITY.md`.
