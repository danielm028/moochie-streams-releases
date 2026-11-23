# Publishing Moochie Streams APKs

After approval, create `danielm028/moochie-streams-releases` as a separate public
repository with `main` as the default branch. Start with fresh Git history.
The initial commit contains `README.md`, `PUBLISHING.md`, and the unavailable
`updates/stable.json`. Keep the local `updates/beta.json` placeholder out of
the initial commit. Keep the private source, signing keys, credentials,
configuration, and backups outside the public repository.

1. Review the local staging folder and the decoded signed metadata. Verify the
   expected channel, package, version, certificate, release notes and APK checksum.
2. Draft a GitHub prerelease tagged `beta-3` targeting `main`. Use the approved
   `RELEASE_NOTES.beta-3.md` as the release body. Attach the approved
   `moochie-streams-beta-3.apk` and its `SHA256SUMS.txt`.
3. Publish the prerelease. Download the APK from the signed URL without
   authentication and verify its size and checksum.
   `https://github.com/danielm028/moochie-streams-releases/releases/download/beta-3/moochie-streams-beta-3.apk`
4. Commit the approved signed envelope as `updates/beta.json` on `main`.
   Fetch the raw manifest and verify its signature and byte-for-byte match
   with the reviewed envelope.
   `https://raw.githubusercontent.com/danielm028/moochie-streams-releases/main/updates/beta.json`
5. Restrict publishing permissions, protect the default branch, and keep
   published assets and tags immutable. To withdraw beta, remove its channel
   document and prepare a replacement with a higher version code.

GitHub documents release assets and repository archives in
[About releases](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases).
