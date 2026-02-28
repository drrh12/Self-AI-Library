# Google Play Store — Full App Approval Checklist

---

## 1. STORE LISTING
**Path:** Grow users → Store presence → Store listings

- [ ] **App name** — Up to 30 characters. The name shown on Google Play.
- [ ] **Short description** — Up to 80 characters. Appears on the store listing below the app name.
- [ ] **Full description** — Up to 4000 characters. Detailed description of the app.
- [ ] **App icon** — 512x512 PNG, 32-bit, up to 1MB.
- [ ] **Feature graphic** — 1024x500 PNG or JPEG. Displayed at the top of the store listing.
- [ ] **Phone screenshots** — Minimum 2, maximum 8. JPEG or PNG, 16:9 or 9:16 aspect ratio.
- [ ] **Tablet screenshots** — Optional but recommended. Same format rules.
- [ ] **Video (YouTube URL)** — Optional. Promo video for the listing.

---

## 2. STORE SETTINGS
**Path:** Grow users → Store presence → Store settings

- [ ] **App category** — Select App or Game, then pick a category (e.g., Photography).
- [ ] **Tags** — Optional. Helps discoverability.
- [ ] **Contact email** — Required. Shown publicly on the store listing.
- [ ] **Contact phone** — Optional.
- [ ] **Contact website** — Optional but recommended.
- [ ] **External marketing** — Choose whether to allow ads outside Google Play.

---

## 3. APP CONTENT
**Path:** Monitor and improve → Policy and programs → App content

### Required Declarations

- [ ] **Privacy policy** — Provide a URL to your privacy policy page.
- [ ] **App access** — Indicate if all functionality is available without special access, or provide credentials/instructions for restricted content.
- [ ] **Ads declaration** — Declare whether the app contains ads.
- [ ] **Content rating** — Complete the IARC content rating questionnaire. Answer questions about the app's content (violence, language, etc.) to get age ratings.
- [ ] **Target audience and content** — Declare the target age group (e.g., 13 and older). If targeting children, additional requirements apply.
- [ ] **Data safety** — Complete the data safety questionnaire: what data you collect, whether it's shared, encryption practices, and whether users can request deletion.
- [ ] **Government apps** — Declare whether the app is a government app.
- [ ] **Financial features** — Declare whether the app provides financial services.
- [ ] **Health apps** — Declare whether the app is a health-related app.

### Conditional Declarations (triggered by manifest/SDK)

- [ ] **Advertising ID** — If your app uses ads or includes an ad SDK, declare "Yes" and select the reason (e.g., Advertising or marketing).
- [ ] **Photo and video permissions** — If your manifest includes `READ_MEDIA_IMAGES` or `READ_MEDIA_VIDEO`, describe why the app needs full access to photos/videos (max 250 chars each).

---

## 4. APP SIGNING & INTEGRITY
**Path:** Test and release → App integrity

- [ ] **Play App Signing** — Must be enabled. Google manages your app signing key.
- [ ] **Automatic protection** — Recommended to be on. Adds runtime integrity checks.

---

## 5. INTERNAL TESTING
**Path:** Test and release → Testing → Internal testing

- [ ] **Upload app bundle (.aab)** — Upload your Android App Bundle.
- [ ] **Create a release** — Set release name and release notes.
- [ ] **Add testers** — Create an email list and add tester Gmail addresses.
- [ ] **Publish** — Roll out the internal test to verify the app works.

---

## 6. CLOSED TESTING
**Path:** Test and release → Testing → Closed testing

- [ ] **Select countries/regions** — Choose which countries testers can be from.
- [ ] **Select testers** — Create/reuse an email list with tester Gmail addresses.
- [ ] **Upload app bundle (.aab)** — Upload or reuse from library.
- [ ] **Set release name** — Internal identifier for the release.
- [ ] **Write release notes** — Using `<en-US>` language tags. Describe what's in the release.
- [ ] **Review and confirm release** — Preview the release details.
- [ ] **Send to Google for review** — Submit via Publishing overview. Google reviews the release.
- [ ] **Get 12+ testers opted-in** — Testers must click the opt-in link and join. Not just added to the list.
- [ ] **Run for 14 days** — The closed test must be active with 12+ opted-in testers for at least 14 days.

---

## 7. PUBLISHING OVERVIEW
**Path:** Publishing overview

- [ ] **Send all changes for review** — All pending changes (store listing, app content, store settings, releases) are bundled and sent to Google together.
- [ ] **Quick checks pass** — Google runs automated policy and quality checks before human review.
- [ ] **Managed publishing** — Optional. If off, approved changes publish automatically. If on, you control when to push live.

---

## 8. PRODUCTION ACCESS
**Path:** Dashboard → Production

After closed testing requirements are met:

- [ ] **Apply for production** — Answer questions about your closed test experience.
- [ ] **Google reviews the application** — Google decides whether to grant production access.
- [ ] **Create production release** — Upload app bundle, set release name and notes.
- [ ] **Submit for production review** — Final review before the app goes live on Google Play.

---

## 9. ADDITIONAL CONSIDERATIONS

- [ ] **Geo-blocking regulation** — If distributing in the EU, review Geo-blocking Regulation (EU) 2018/302.
- [ ] **App bundle requirements** — Must target the required minimum Android API level (currently API 33+).
- [ ] **64-bit support** — App must include 64-bit native libraries if using native code.
- [ ] **Permissions justification** — Any sensitive permissions (camera, location, storage, etc.) may require justification.
- [ ] **Deceptive behavior policy** — App must not mislead users about functionality.
- [ ] **Intellectual property** — App name, icon, and content must not infringe on trademarks.
