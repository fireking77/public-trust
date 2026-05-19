# Security

**Key rotation.** Public keys are never deleted. On rotation, the superseded
key moves to a `retired/` directory next to the active one (created on first
rotation) so artifacts signed with it stay verifiable; the change is recorded
in `FINGERPRINTS.md`. A retired key must not sign new artifacts.

**Reporting.** Report a suspected key compromise or an incorrect fingerprint to
Istvan Darvas via <https://www.linkedin.com/in/istvandarvas/> or an issue here.
Compromise reports trigger immediate rotation.
