# Security follow-up — 19 October 2026

This is an upstream desktop-app fork. Constants.cs contains populated AUTH_APPID/AUTH_SECRET and development HTTP-auth passwords inherited from upstream. Ownership and current validity are unknown. Do not test them. The source and desktop distribution cannot protect a shared embedded secret; review with the upstream service operator before replacing its authentication scheme. The scanner also flags Interface Builder serialized data; review these separately as likely false positives. No legacy desktop build was attempted.

The new baseline scans the current checked-out tree, not historical commits. Do not interpret a green check as proof that historical credentials were revoked. No production deployment or provider credential test was performed.

Repository rulesets, required PR checks, secret scanning/push protection, Dependabot alerts, account 2FA, and token/SSH-key hygiene require verification in GitHub settings. These settings were not mutated by this PR. Apply required checks only after their first verified successful run, so existing deployments are not unexpectedly blocked.
