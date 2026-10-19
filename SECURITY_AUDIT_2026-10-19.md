# Security follow-up — 19 October 2026

This is an upstream desktop-app fork. Constants.cs contains populated AUTH_APPID/AUTH_SECRET and development HTTP-auth passwords inherited from upstream. Ownership and current validity are unknown. Do not test them. The source and desktop distribution cannot protect a shared embedded secret; review with the upstream service operator before replacing its authentication scheme. The scanner also flags Interface Builder serialized data; review these separately as likely false positives. No legacy desktop build was attempted.

The new baseline scans the current checked-out tree, not historical commits. Do not interpret a green check as proof that historical credentials were revoked. No production deployment or provider credential test was performed.

Repository rulesets, required PR checks, secret scanning/push protection, Dependabot alerts, account 2FA, and token/SSH-key hygiene require verification in GitHub settings. These settings were not mutated by this PR. Apply required checks only after their first verified successful run, so existing deployments are not unexpectedly blocked.

## CI remediation follow-up

Unused AUTH_APPID and AUTH_SECRET declarations were removed from both Windows and macOS source after checking that no exact-symbol call sites exist in the repository. Nonempty Windows DEBUG HTTP-auth password literals now come from VSCO_KEYS_AUTH_AUTH_PASSWORD, VSCO_KEYS_VERSION_AUTH_PASSWORD and VSCO_KEYS_WEB_KEYS_ENDPOINT_PASSWORD; Release defaults remain unchanged. Do not distribute a shared secret inside a desktop build. Existing history is unchanged; only the upstream service operator can confirm/revoke historical credentials.

Three scanner locations in MainMenu.xib were reviewed as Interface Builder border/dictionary metadata, not credentials; only those exact fingerprints are excluded. No general file/rule exclusion was added. Desktop compilation and authenticated upstream features remain unverified; retain draft status until reviewed on the supported legacy Windows/macOS build environment.
