# Public binary releases

This repository distributes ELO.exe and ELO.exe.sha256. Application source, build logs, tests and credential-scan reports stay in the private build repository. The public source archives contain only this public repository's files.

The build pipeline stages an existing checked executable and checksum in a draft release, then sends a publish-verified-release repository dispatch containing the tag and expected SHA-256. This repository's Actions workflow downloads those two assets, checks the checksum file and the independently supplied expected hash, then publishes the draft using its own GITHUB_TOKEN.

The workflow can also be run manually with a draft tag and its expected SHA-256. It refuses missing assets, extra assets, invalid hashes, mismatches and already-published releases. Existing releases are not overwritten. Only release assets are transferred; private source history is never mirrored here.
