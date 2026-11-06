# Chorale Manager

An app any choir can use. Each choir registers with an email, names itself, uploads a logo, and gets its own private space.
Includes: member IDs, auditions with scoring, attendance (manual or by member ID), costume tracking, dues, income
(donations, competition prizes, talent fees, merch), expenses, schedule, donation QR and bank details, backup export/import, undo.

## Put it online (about 15 minutes, free tier is enough)

1. **Firebase project.** console.firebase.google.com > Add project.
2. **Sign-in.** Build > Authentication > Get started > turn on **Email/Password**.
3. **Database.** Build > Firestore Database > Create database (production mode, region near you, e.g. asia-southeast1).
4. **Rules.** Firestore > Rules > paste everything from `firestore.rules` > Publish.
5. **Config.** Project settings > Your apps > Web (`</>`) > copy the config values into `firebase-config.js`.
6. **GitHub.** Create a repo, upload every file in this folder (keep `.nojekyll`). Settings > Pages > Deploy from branch > main / root.
7. **Allow your site.** Firebase > Authentication > Settings > Authorized domains > add `YOUR-NAME.github.io`.
8. Open `https://YOUR-NAME.github.io/YOUR-REPO/`, tap **Register a new choir**, and you are in.

## Test before sharing (5 minutes)
Register a choir; upload a logo; add a member and note the ID; check in with that ID; delete something then press Undo;
sign out and back in (data should still be there); register a second account in a private window and confirm it
sees none of the first choir's data; turn off Wi-Fi, change something, turn it back on, reload.

## Known limits of this version
- One login per choir (the officer). Members cannot log in yet.
- All records of a choir live in one Firestore document (limit about 1 MB). Plenty for a roster of a few hundred and years of
  records, but not for photos or files. The app warns you when you get close.
- If two devices edit the same choir at the same moment, the last save wins.
- No music library, photo gallery, merch storefront or QR camera scanning yet. These need Firebase Storage and
  per-member accounts, a larger data model (see the plan in the chat). Build them next.
- Not yet tested against a live Firebase project by the author of this code. Run the checklist above first.
