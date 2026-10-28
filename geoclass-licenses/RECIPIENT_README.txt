GEOCLASS iOS LIBRARY MATERIALS — LOCAL RELEASE-CANDIDATE DRAFT

This folder is a review package, not the final App Store release. Read
publication-status.json before publishing it. The app version/build and binary
SHA-256 in compiled-kit/kit.json identify the local candidate. New app builds
require a newly matched package. Do not label this as a final public release.

WHAT IS INCLUDED
* Official, checksum-pinned Qt source archives, source identity inventory,
  installed configuration records and linked-component SBOM review.
* A full local source snapshot of PROJ, MapLibre Qt/native and vendored sources,
  SQLite and minizip-ng. Existing library modifications are preserved in the
  snapshot rather than relying on a mutable upstream checkout.
* Library build scripts, exact source hashes, original notices and compiled
  Geoclass inputs with a path-independent linker recipe.
* Application-input relinking permission, utility licence and concrete recipient installation instructions (pending publisher release approval).

WHAT IS EXCLUDED
Geoclass's complete repository and plain C++/Swift application source files;
survey/user data; Apple or Google SDK distributions; signing certificates,
private keys, provisioning profiles, Apple accounts and passwords.
Compiled app resources include readable QML/JavaScript, accepted by the owner.
AdMob identifiers are public client identifiers, not account credentials.
The publisher's Esri API key is removed from the bundle template and is not
compiled into the app objects. Satellite requires a recipient-owned limited
basemap credential: optionally pass --esri-key-file /local/path to
assemble_bundle.py. Without it, the relinked app still has street/blank maps.
Keep client service credentials out of public uploads; mobile client keys can
be extracted from an installed app, so restrict privileges and billing.

REBUILD / RELINK
1. Verify SHA256SUMS.txt with `shasum -a 256 -c SHA256SUMS.txt` from this folder.
2. Use your own properly licensed Xcode/SDK, Qt host tools and Google SDK.
   Read BUILD_LIBRARIES.txt for target versions, settings and source layout.
3. Build the relevant libraries or supply the matching existing installations.
   Do not mix iOS device, simulator and macOS archives. This kit targets iOS
   device arm64. Qt private APIs require matching configuration/interfaces;
   arbitrary Qt versions are not interchangeable.
4. From compiled-kit run:
   python3 relink.py --qt /path/to/qt/ios --native /path/to/native-ios \
     --maplibre /path/to/maplibre-ios --ads /path/to/GoogleMobileAdsSdkiOS-13.11.0
   Choose a separate --output directory if desired. The linker makes an unsigned
   executable; it does not alter an installed app, sign, install or upload.
5. See INSTALLATION.txt for the separate bundle/signing requirements.

RIGHTS AND SUPPORT
Each third-party component retains its original licence and copyright. No
blanket GPL/MIT licence is applied to Geoclass or this mixed-material folder.
See RELINK_PERMISSION.txt and MATERIALS_TOOLS_LICENSE.txt; owner approval and final distribution terms
remain necessary. The publisher does not promise QA, updates or ongoing support
for recipient-modified libraries. This does not remove the recipient's LGPL
modification, relinking or debugging rights.

PUBLIC ACCESS, WHEN APPROVED
Publish versioned assets and checksums in
https://github.com/razoridunos/razoridunos.github.io/releases
and link them from https://razoridunos.github.io/geoclass-licenses/ and the app's licence page.
The privacy policy remains https://edips.github.io/privacypolicy.
Do not require an email request or login to obtain the offered downloads.
Preserve downloads for previously distributed versions as required. No files
have been uploaded by preparing this local package.
