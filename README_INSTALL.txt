HABI SJDM SOS — USER & ADMIN PWA PACKAGE

CONTENTS
- HABI_User_PWA: updated User App (preferred name/nickname saved in Firestore, official-source shortcuts)
- HABI_Admin_PWA: existing Admin App, preserved
- manifests, service workers, and install icons for supported browsers

DEPLOYMENT
1. Extract this ZIP.
2. Upload the two folders HABI_User_PWA and HABI_Admin_PWA to the ROOT of the existing GitHub repository, keeping the folder names.
3. Commit/push the changes and wait for GitHub Pages to publish.
4. User URL: https://gailmacarine-create.github.io/habi-sjdm-sos/HABI_User_PWA/
5. Admin URL: https://gailmacarine-create.github.io/habi-sjdm-sos/HABI_Admin_PWA/

IMPORTANT FIRESTORE SETUP FOR PREFERRED NAME
The updated User App reads/writes userProfiles/{uid}. Add this rule inside your existing
match /databases/{database}/documents block, without deleting or replacing your other rules:

match /userProfiles/{userId} {
  allow read, create, update: if request.auth != null && request.auth.uid == userId;
  allow delete: if false;
}

Review this rule against your complete existing rules before publishing. Do not make the
userProfiles collection publicly readable. Existing Firebase project/configuration is retained.

INSTALL
- Android: Chrome > menu > Install app / Add to Home Screen.
- iPhone/iPad: Safari > Share > Add to Home Screen.
- Windows/macOS: Chrome or Edge > Install this site as an app.

ACCURACY / DATA LIMITS
- Official-source shortcuts open the primary agency/provider pages. They are NOT live API
  integrations and must not be described as real-time HABI feeds.
- Meralco outage status and restoration estimates must be checked on Meralco's own outage
  service. PAGASA warnings/forecasts must be checked on the latest PAGASA bulletin.
- SJDM CDRRMO contacts are shown as official emergency contact sources; an HABI report does
  not dispatch responders.
- Exact barangay waste collection schedules, official disposal-site coordinates, complete
  public-transport terminal inventory, and live utility telemetry are not fabricated or
  claimed verified in this build. Obtain/authorize official datasets before enabling them.
- HABI User report submissions still depend on your existing Firestore rules and project
  configuration. Test submissions with a non-admin user and confirm they appear in Admin.

This is a Progressive Web App, not a native APK/IPA. It requires HTTPS hosting and internet
access for Firebase and external official data/services.


HABI LOGO UPDATE
----------------
Both HABI_User_PWA and HABI_Admin_PWA now use the supplied blue-and-gold HABI
logo for the 192px and 512px PWA icons, maskable icon, Apple touch icon,
32px browser favicon, and favicon.ico. Both manifests and HTML icon references
were updated. Service-worker cache names were bumped to force a fresh app shell.

After uploading/deploying both app folders, users may need to close and reopen
the installed PWA. If a device continues to show the previous icon, remove the
old home-screen shortcut/app and install it again from the updated website.
