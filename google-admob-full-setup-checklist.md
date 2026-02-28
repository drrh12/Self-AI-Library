# Google AdMob — Full Setup Checklist

---

## 1. ADMOB ACCOUNT SETUP
**URL:** https://admob.google.com

### Prerequisites

- [ ] **Google Account** — You need a Google Account (new or existing). If you already have one for Google Play Console, you can use the same one.
- [ ] **Age requirement** — You must be at least 18 years old. If under 18, a parent or guardian must sign up using their own Google Account.
- [ ] **Phone number** — A local phone number for verification (may not be required if you have previously verified with Google).
- [ ] **Identity documents** — Government-issued ID (passport, driver's license, national ID) for identity verification.
- [ ] **Bank account** — Required for receiving payments; must be in your name or your company's name.

### Sign-Up Steps

- [ ] **Go to** https://admob.google.com and click "Get Started."
- [ ] **Sign in** with your Google Account (or create a new one).
- [ ] **Select country/territory** — Choose where you currently live. This determines your currency, payment methods, and tax forms. **Cannot be changed later.**
- [ ] **Review and accept** AdMob Terms and Conditions.
- [ ] **Click** "Start using AdMob."

### Identity Verification (Triggered at $10 earnings threshold)

- [ ] **Wait for prompt** — Google will ask you to verify your identity when your earnings reach the verification threshold (~$10 or equivalent).
- [ ] **Submit government-issued ID** — Upload a valid, non-expired document (passport, driver's license, or national ID card). Ensure the name matches your AdMob account name exactly.
- [ ] **Photo requirements** — High resolution, in focus, full document visible, all four corners captured.
- [ ] **Deadline** — You have **45 days** from the date Google requests verification. If not completed, ad serving will be stopped.

### Address Verification (PIN)

- [ ] **Triggered at** ~$10 earnings threshold (after identity verification is complete).
- [ ] **PIN mailed** — Google sends a 6-digit PIN to your payments address via standard international mail.
- [ ] **Delivery time** — Typically 3 weeks; no tracking number provided.
- [ ] **Enter PIN** in AdMob console at: **Payments > Verify address**.
- [ ] **Deadline** — You have **4 months** to enter the PIN from the date it was generated. After that, ad serving stops.
- [ ] **Replacement PINs** — You can request up to 3 additional replacement PINs if the first doesn't arrive.

---

## 2. APP REGISTRATION IN ADMOB CONSOLE
**Path:** AdMob console > Apps > Add app

### Adding a New App

- [ ] **Click** "Add app" in the Apps section of the AdMob sidebar.
- [ ] **Select platform** — Choose **Android** or **iOS**.
- [ ] **Search for your app** — If already published, search by app name or package name/bundle ID in Google Play or App Store.
- [ ] **Or add manually** — If not yet published, select "No" when asked if the app is listed on a supported app store. Enter your app name manually.
- [ ] **Copy your App ID** — Format: `ca-app-pub-XXXXXXXXXXXXXXXX~YYYYYYYYYY` (you will need this for SDK integration).
- [ ] **Enable User Metrics** — Toggle on in the App settings. Required if you plan to link to Firebase.

### Linking to App Store (after publishing)

- [ ] **Path:** Apps > [Your App] > App settings > App stores
- [ ] **Click** "Add store" and search for your published app.
- [ ] **Wait time** — After publishing to Google Play/App Store, it may take 24-48 hours (up to 1 week) before the app is findable in AdMob.
- [ ] **Restriction** — Private Google Play apps cannot be linked to AdMob. The app must be publicly available.

---

## 3. AD UNIT CREATION
**Path:** AdMob console > Apps > [Your App] > Ad units > Add ad unit

### Banner Ads

- [ ] **Select** "Banner" ad format.
- [ ] **Name** — Give the ad unit a descriptive name (e.g., "home_screen_banner").
- [ ] **Ad type** — Choose between Text, Image & rich media, or Video.
- [ ] **Copy the ad unit ID** — Format: `ca-app-pub-XXXXXXXXXXXXXXXX/YYYYYYYYYY`.
- [ ] **Recommended size** — Use Adaptive Banner (auto-adjusts to device width). Legacy fixed sizes: 320x50 (phone banner), 320x100 (large banner), 728x90 (tablet leaderboard), 300x250 (medium rectangle).
- [ ] **Refresh rate** — Configurable in AdMob console (default: every 60 seconds; range: 30-150 seconds). Do NOT set additional refresh in third-party mediation UIs.

### Interstitial Ads

- [ ] **Select** "Interstitial" ad format.
- [ ] **Name** — Descriptive name (e.g., "level_complete_interstitial").
- [ ] **Ad type** — Text, Image & rich media, and/or Video.
- [ ] **Frequency capping** — Set in AdMob console to limit how often users see interstitials.
- [ ] **Copy the ad unit ID.**

### Rewarded Ads

- [ ] **Select** "Rewarded" ad format.
- [ ] **Name** — Descriptive name (e.g., "extra_lives_rewarded").
- [ ] **Set reward amount** — e.g., "1" (amount of in-app currency given).
- [ ] **Set reward type** — e.g., "coins", "lives", "gems" (the label for the reward).
- [ ] **Server-side verification (optional)** — Enable if you need server-side reward verification. Set callback URL.
- [ ] **Copy the ad unit ID.**

### Rewarded Interstitial Ads

- [ ] **Select** "Rewarded interstitial" ad format.
- [ ] **Name** — Descriptive name.
- [ ] **Set reward amount and type** — Same as rewarded ads.
- [ ] **Copy the ad unit ID.**

### Native Ads

- [ ] **Select** "Native" ad format.
- [ ] **Name** — Descriptive name (e.g., "feed_native_ad").
- [ ] **Copy the ad unit ID.**
- [ ] **Note:** You are responsible for rendering native ad assets in your own layout (headline, body, icon, media, CTA button, AdChoices).

### App Open Ads

- [ ] **Select** "App open" ad format.
- [ ] **Name** — Descriptive name (e.g., "app_open_splash").
- [ ] **Copy the ad unit ID.**
- [ ] **Note:** App open ads expire after **4 hours**. You must validate the load time before displaying.

---

## 4. SDK INTEGRATION

### Android Setup

#### Gradle Dependencies

- [ ] **settings.gradle** — Ensure `google()` and `mavenCentral()` are in both `pluginManagement.repositories` and `dependencyResolutionManagement.repositories`:
```groovy
pluginManagement {
    repositories {
        google()
        mavenCentral()
    }
}
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
    }
}
```

- [ ] **build.gradle (app-level)** — Add the Google Mobile Ads SDK dependency:
```groovy
dependencies {
    implementation("com.google.android.gms:play-services-ads:25.0.0")
}
```

- [ ] **Minimum SDK** — Set `minSdk` to **23** or higher.
- [ ] **Compile SDK** — Set `compileSdk` to **35** or higher.

#### AndroidManifest.xml Configuration

- [ ] **Add AdMob App ID** — Add inside the `<application>` tag:
```xml
<manifest>
    <application>
        <!-- Replace with your actual AdMob App ID -->
        <meta-data
            android:name="com.google.android.gms.ads.APPLICATION_ID"
            android:value="ca-app-pub-XXXXXXXXXXXXXXXX~YYYYYYYYYY"/>
    </application>
</manifest>
```
**WARNING:** Omitting this tag causes a crash: `"Missing application ID."`

- [ ] **Advertising ID permission** (if targeting Android 13+ with SDK 20.3.0 or lower):
```xml
<uses-permission android:name="com.google.android.gms.permission.AD_ID"/>
```

- [ ] **Hardware acceleration** (required for video ads):
```xml
<application android:hardwareAccelerated="true">
```

#### SDK Initialization (Android)

- [ ] **Initialize on a background thread** at app launch, before loading any ads:

**Kotlin:**
```kotlin
import com.google.android.gms.ads.MobileAds
import kotlinx.coroutines.CoroutineScope
import kotlinx.coroutines.Dispatchers
import kotlinx.coroutines.launch

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        CoroutineScope(Dispatchers.IO).launch {
            MobileAds.initialize(this@MainActivity)
        }
    }
}
```

**Java:**
```java
import com.google.android.gms.ads.MobileAds;

new Thread(() -> MobileAds.initialize(this, initializationStatus -> {})).start();
```

- [ ] **Order of operations** — Set consent flags and request configuration BEFORE calling `MobileAds.initialize()`.

### iOS Setup

#### Installation (choose one method)

- [ ] **CocoaPods** — Add to your `Podfile`:
```ruby
pod 'Google-Mobile-Ads-SDK'
```
Then run: `pod install --repo-update`

- [ ] **Swift Package Manager** — In Xcode: **File > Add Package Dependencies**, enter:
```
https://github.com/googleads/swift-package-manager-google-mobile-ads.git
```
**Note:** Mediation adapter libraries are NOT available via SPM. Use CocoaPods for mediation.

- [ ] **Manual download** — Download and embed:
  - `GoogleMobileAds.xcframework`
  - `UserMessagingPlatform.xcframework`
  - Add `/usr/lib/swift` to Runpath Search Paths
  - Add `-ObjC` to Other Linker Flags

#### Xcode Requirements

- [ ] **Xcode** version **16.0** or higher.
- [ ] **Minimum deployment target** — iOS **13.0** or higher.

#### Info.plist Configuration

- [ ] **Add AdMob App ID:**
```xml
<key>GADApplicationIdentifier</key>
<string>ca-app-pub-XXXXXXXXXXXXXXXX~YYYYYYYYYY</string>
```

- [ ] **Add SKAdNetwork identifiers** — Required for Apple's attribution framework. Add the `SKAdNetworkItems` array containing Google's identifier and third-party buyer identifiers:
```xml
<key>SKAdNetworkItems</key>
<array>
    <dict>
        <key>SKAdNetworkIdentifier</key>
        <string>cstr6suwn9.skadnetwork</string>  <!-- Google -->
    </dict>
    <dict>
        <key>SKAdNetworkIdentifier</key>
        <string>4fzdc2evr5.skadnetwork</string>
    </dict>
    <dict>
        <key>SKAdNetworkIdentifier</key>
        <string>2fnua5tdw4.skadnetwork</string>
    </dict>
    <dict>
        <key>SKAdNetworkIdentifier</key>
        <string>ydx93a7ass.skadnetwork</string>
    </dict>
    <dict>
        <key>SKAdNetworkIdentifier</key>
        <string>p78axxw29g.skadnetwork</string>
    </dict>
    <!-- Plus ~35 additional third-party buyer IDs from Google's documentation -->
    <!-- Full list: https://developers.google.com/admob/ios/quick-start#update_your_infoplist -->
</array>
```

- [ ] **Add App Tracking Transparency usage description** (for IDFA access):
```xml
<key>NSUserTrackingUsageDescription</key>
<string>This identifier will be used to deliver personalized ads to you.</string>
```

#### SDK Initialization (iOS)

- [ ] **Initialize as early as possible:**

**Swift:**
```swift
import GoogleMobileAds

@main
class AppDelegate: UIResponder, UIApplicationDelegate {
    func application(_ application: UIApplication,
                     didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        MobileAds.shared.start()
        return true
    }
}
```

**SwiftUI:**
```swift
import GoogleMobileAds

@main
struct MyApp: App {
    init() {
        MobileAds.shared.start()
    }
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```

**Objective-C:**
```objc
@import GoogleMobileAds;

- (BOOL)application:(UIApplication *)application
    didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [GADMobileAds.sharedInstance startWithCompletionHandler:nil];
    return YES;
}
```

---

## 5. APP-ADS.TXT SETUP
**Path:** AdMob console > Apps > [Your App] > app-ads.txt

### What It Is

app-ads.txt is an IAB initiative that declares which ad networks are authorized to sell your app's ad inventory. **Mandatory for new apps as of January 2025**, with existing apps being phased in throughout 2025.

### Setup Steps

- [ ] **Find your Publisher ID** in AdMob console: **Settings > Account information**. Format: `pub-XXXXXXXXXXXXXXXX`.

- [ ] **Get the code snippet** — AdMob provides a personalized snippet in the console. The standard format is:
```
google.com, pub-XXXXXXXXXXXXXXXX, DIRECT, f08c47fec0942fa0
```
  - `google.com` = the ad system domain
  - `pub-XXXXXXXXXXXXXXXX` = your unique publisher ID
  - `DIRECT` = you directly control the account
  - `f08c47fec0942fa0` = Google's TAG ID (Trustworthy Accountability Group certification)

- [ ] **Add mediation partner entries** — If using mediation, add entries for each mediation partner in the same file.

- [ ] **Create the file** — Name it exactly `app-ads.txt` (lowercase, no other filename).

- [ ] **Host the file** — Publish at the root of your developer website:
  - URL must be: `https://example.com/app-ads.txt`
  - The domain must match the developer website URL on your Google Play or App Store listing.
  - Must be served over HTTPS.
  - Must return HTTP 200 status code.

- [ ] **Alternative: Firebase Hosting** — If you cannot host at your website root, use Firebase Hosting. The file will be at: `https://PROJECT_ID.web.app/app-ads.txt`.

- [ ] **Update your store listing** — Ensure your developer website URL in Google Play Console / App Store Connect matches where you host the file.

- [ ] **Request verification** — In the AdMob console, go to Apps > [Your App] > app-ads.txt tab and request verification.

- [ ] **Wait for crawling** — AdMob takes **24+ hours** to crawl and verify the file. Check the status in the AdMob console.

### Consequences of Non-Compliance

- Apps without app-ads.txt will face **limited ad serving** which may reduce revenue.
- For apps listed only in third-party stores (not Google Play or App Store), app-ads.txt is not currently required.

---

## 6. ADMOB POLICIES AND COMPLIANCE
**Reference:** https://support.google.com/admob/answer/6128543

### Prohibited Content

- [ ] **No counterfeit goods** — Ads/content imitating brand features to pass as genuine.
- [ ] **No dangerous products/services** — Recreational drugs, weapons, explosives, instructions for harm.
- [ ] **No dishonest behavior** — Hacking software, academic cheating services, click fraud.
- [ ] **No inappropriate content** — Content promoting hatred, violence, harassment, or discrimination.
- [ ] **No sexually explicit content** — Unless properly classified and region-appropriate.

### Ad Placement Policies

- [ ] **No accidental clicks** — Ads must not be placed where users might accidentally click (near buttons, in scrolling content without clear separation).
- [ ] **No deceptive placement** — Ads must be distinguishable from app content.
- [ ] **No encouraging clicks** — Do not prompt users to click ads (e.g., "click the ad to support us").
- [ ] **No ad stacking** — Do not place multiple ads overlapping each other.
- [ ] **No ads on screens with no content** — Ads must accompany actual app content.
- [ ] **Interstitial timing** — Do not show interstitials at app launch (before content loads) or when the user is about to complete an action.

### Behavioral Policies

- [ ] **No invalid traffic** — Do not click your own ads, use bots, or incentivize clicks.
- [ ] **No ad fraud** — Do not manipulate ad impressions or revenue artificially.
- [ ] **Data disclosure** — Clearly disclose data collection, sharing, and usage practices in connection with Google services (updated February 16, 2025).

### Google Play Console Declarations (Required)

- [ ] **Ads declaration** — In Google Play Console, go to **Policy and programs > App content > Ads** and select **"Yes, my app contains ads."**
- [ ] **Advertising ID declaration** — If targeting Android 13 (API 33)+, declare Advertising ID usage in Google Play Console. Select the reason (e.g., "Advertising or marketing"). **Failure to declare can result in app rejection or removal.**

### Political Advertising (as of September 2025)

- [ ] **EU restriction** — Political advertising in the EU is restricted under EU Regulation 2024/900. If you intend to run political ads via AdMob Campaigns, you must declare this in the console.

### Online Gambling Restrictions (as of March 2025)

- [ ] **Allowed countries only** — Online gambling content may only be shown to users in: Australia, Brazil, Canada, Colombia, France, Germany, Greece, Ireland, Italy, Japan, Mexico, Netherlands, Philippines, South Korea, Spain, Turkey, United Kingdom, and United States.

---

## 7. MEDIATION SETUP
**Path:** AdMob console > Mediation > Create mediation group

### Overview

AdMob mediation sends ad requests to multiple ad networks to maximize fill rate and revenue. Supports **bidding** (real-time auction) and **waterfall** (priority-ordered sequential requests).

### Prerequisites

- [ ] **Google Mobile Ads SDK 18.3.0+** (for bidding support).
- [ ] **Implement the ad format** (banner, interstitial, etc.) with AdMob first, before adding mediation.
- [ ] **AdMob permissions** — Need inventory management, app access, and privacy settings permissions.

### Adding Mediation Partners

- [ ] **Install adapter dependency** for each network. Example for Android:
```groovy
// AppLovin adapter
implementation("com.google.ads.mediation:applovin:13.0.0.0")
// Unity Ads adapter
implementation("com.google.ads.mediation:unity:4.12.5.0")
// Meta Audience Network adapter
implementation("com.google.ads.mediation:facebook:6.18.0.0")
```

- [ ] **Create accounts** with each third-party ad network you want to use.
- [ ] **Configure network settings** in AdMob console: **Mediation > Ad sources > Add ad source**.
- [ ] **Enter third-party credentials** (App ID, Placement ID, etc.) for each network.

### Supported Networks (bidding + waterfall)

| Network | Bidding | Waterfall |
|---------|---------|-----------|
| AppLovin | Yes | Yes |
| Chartboost | Yes | Yes |
| DT Exchange | Yes (beta) | Yes |
| InMobi | Yes | Yes |
| ironSource Ads | Yes | Yes |
| Liftoff Monetize | Yes | Yes |
| LINE Ads Network | Yes | Yes |
| Meta Audience Network | Yes | No (bidding only) |
| Mintegral | Yes | Yes |
| Moloco | Yes | Yes |
| Pangle | Yes | Yes |
| PubMatic OpenWrap | Yes | Yes |
| Unity Ads | Yes | Yes |

Additional bidding-only partners (no third-party SDK required): Ad Generation, Chocolate Platform, Equativ, Fluct, Improve Digital, Index Exchange, InMobi Exchange, Magnite DV+, Media.net, MobFox, Nexxen, OneTag Exchange, OpenX, PubMatic, Rise, Sharethrough, Smaato, Sonobi, TripleLift, Verve Group, Yieldmo, YieldOne.

### Mediation Best Practices

- [ ] **Wait for SDK initialization to complete** before loading ads. Check adapter status via `InitializationStatus.getAdapterStatusMap()`.
- [ ] **Pass Activity context** (not generic Context) when creating ad objects — some mediation networks require it.
- [ ] **Disable refresh** in third-party ad network UIs for banner ads (to avoid double-refresh with AdMob's own refresh).
- [ ] **Use `loadAd()`** for native ads (not `loadAds()`) when using mediation — `loadAds()` only returns Google ads.
- [ ] **Add mediation partners to Privacy & messaging** settings in AdMob for GDPR/US state privacy compliance. Failure to do so may prevent partners from serving ads.

---

## 8. TESTING

### Test Ad Unit IDs (Android)

Use these during development. They are safe to click and will not flag invalid activity:

| Ad Format | Test Ad Unit ID |
|-----------|----------------|
| Adaptive Banner | `ca-app-pub-3940256099942544/9214589741` |
| Fixed Size Banner | `ca-app-pub-3940256099942544/6300978111` |
| Interstitial | `ca-app-pub-3940256099942544/1033173712` |
| Rewarded | `ca-app-pub-3940256099942544/5224354917` |
| Rewarded Interstitial | `ca-app-pub-3940256099942544/5354046379` |
| Native | `ca-app-pub-3940256099942544/2247696110` |
| Native Video | `ca-app-pub-3940256099942544/1044960115` |
| App Open | `ca-app-pub-3940256099942544/9257395921` |

### Test Ad Unit IDs (iOS)

| Ad Format | Test Ad Unit ID |
|-----------|----------------|
| Adaptive Banner | `ca-app-pub-3940256099942544/2435281174` |
| Fixed Size Banner | `ca-app-pub-3940256099942544/2934735716` |
| Interstitial | `ca-app-pub-3940256099942544/4411468910` |
| Rewarded | `ca-app-pub-3940256099942544/1712485313` |
| Rewarded Interstitial | `ca-app-pub-3940256099942544/6978759866` |
| Native | `ca-app-pub-3940256099942544/3986624511` |
| Native Video | `ca-app-pub-3940256099942544/2521693316` |
| App Open | `ca-app-pub-3940256099942544/5575463023` |

### Test Device Registration

- [ ] **Android emulators** — Automatically configured as test devices.
- [ ] **iOS simulators** — Automatically configured as test devices.

- [ ] **Physical Android device:**
  1. Run app and make an ad request.
  2. Check Logcat for a message like: `Use RequestConfiguration.Builder().setTestDeviceIds(Arrays.asList("YOUR_DEVICE_ID"))`.
  3. Add the device ID:
```kotlin
val testDeviceIds = listOf("YOUR_DEVICE_HASH_ID")
MobileAds.setRequestConfiguration(
    RequestConfiguration.Builder()
        .setTestDeviceIds(testDeviceIds)
        .build()
)
```
```java
List<String> testDeviceIds = Arrays.asList("YOUR_DEVICE_HASH_ID");
MobileAds.setRequestConfiguration(
    new RequestConfiguration.Builder()
        .setTestDeviceIds(testDeviceIds)
        .build());
```

- [ ] **Physical iOS device:**
  1. Run app and make an ad request.
  2. Check Xcode console for the device test identifier.
  3. Add the device ID:
```swift
MobileAds.shared.requestConfiguration.testDeviceIdentifiers = ["YOUR_DEVICE_HASH_ID"]
```
```objc
GADMobileAds.sharedInstance.requestConfiguration.testDeviceIdentifiers = @[ @"YOUR_DEVICE_HASH_ID" ];
```

- [ ] **Activation time** — New test devices typically activate within 15 minutes, but can take up to 24 hours.
- [ ] **Remove test device code** before publishing to production.

### Ad Inspector

- [ ] **Requirements** — Google Mobile Ads SDK **20.0.0+** (Android) or **8.5.0+** (iOS for bidding details). Device must be registered as a test device.
- [ ] **Launch programmatically (Android):**
```kotlin
MobileAds.openAdInspector(context) { error ->
    // error is non-null if inspector closed due to an error
}
```
```java
MobileAds.openAdInspector(context, error -> {
    // error is non-null if ad inspector closed due to an error
});
```

- [ ] **Launch programmatically (iOS):**
```swift
MobileAds.shared.presentAdInspector(from: viewController) { error in
    // error is non-nil if there was an issue
}
```
```objc
[GADMobileAds.sharedInstance presentAdInspectorFromViewController:viewController
    completionHandler:^(NSError *error) {
    // error is non-nil if there was an issue
}];
```

- [ ] **Gesture-based launch** — Configure a launch gesture (double flick or shake) in the AdMob UI for your registered test device. After configuring, make an ad request, restart the app, then perform the gesture.
- [ ] **Capabilities** — Verify adapter integrations, test individual ad units, troubleshoot ad loading failures, debug privacy settings.
- [ ] **Note:** Ad Inspector increases memory usage on test devices.

### Pre-Release Testing Checklist

- [ ] Verify all ad formats load correctly with test ad unit IDs.
- [ ] Verify test ads display "Test Ad" or "Test mode" label (SDK 11.6.0+ Android, 7.59.0+ iOS).
- [ ] Verify ad callbacks fire correctly (onAdLoaded, onAdFailedToLoad, onAdDismissed, etc.).
- [ ] Verify interstitials display at natural transition points only.
- [ ] Verify rewarded ads grant rewards correctly.
- [ ] Verify app open ads do not display after 4-hour expiration.
- [ ] Replace ALL test ad unit IDs with production ad unit IDs before release.
- [ ] Remove ALL test device registration code before release.
- [ ] Test on multiple screen sizes (phone, tablet) for banner sizing.

---

## 9. GDPR / CONSENT REQUIREMENTS

### UMP SDK Integration (Android)

- [ ] **Add UMP SDK dependency:**
```groovy
implementation("com.google.android.ump:user-messaging-platform:4.0.0")
```

- [ ] **Requires:** Android API level 21+ and AdMob App ID in AndroidManifest.xml.

### UMP SDK Integration (iOS)

- [ ] **CocoaPods:**
```ruby
pod 'GoogleUserMessagingPlatform'
```

- [ ] **Swift Package Manager:**
```
https://github.com/googleads/swift-package-manager-google-user-messaging-platform.git
```

- [ ] **Manual:** Download and embed `UserMessagingPlatform.xcframework`.

### Create Privacy Messages in AdMob Console

- [ ] **Path:** AdMob console > **Privacy & messaging** tab.
- [ ] **Create an EU consent message** — This is required for users in the EEA and UK.
- [ ] **Create a US state privacy message** (optional but recommended) — For CCPA and other US state privacy laws.
- [ ] **Add all mediation partners** to Privacy & messaging settings — Required so mediation partners can serve ads in compliance with GDPR.

### Consent Flow Implementation

- [ ] **Step 1: Request consent info update at every app launch:**

**Android (Kotlin):**
```kotlin
val consentInformation = UserMessagingPlatform.getConsentInformation(this)
val params = ConsentRequestParameters.Builder().build()
consentInformation.requestConsentInfoUpdate(
    this, params,
    { /* Success: consent info updated */ },
    { error -> /* Failure: handle error */ }
)
```

**iOS (Swift):**
```swift
UMPConsentInformation.sharedInstance.requestConsentInfoUpdate(with: nil) { error in
    // Handle update result
}
```

- [ ] **Step 2: Load and show consent form if required:**

**Android (Kotlin):**
```kotlin
UserMessagingPlatform.loadAndShowConsentFormIfRequired(this) { error ->
    // Consent form dismissed or not required
}
```

**iOS (Swift):**
```swift
UMPConsentForm.loadAndPresentIfRequired(from: viewController) { error in
    // Form dismissed or not required
}
```

- [ ] **Step 3: Check consent before requesting ads:**

**Android:**
```kotlin
if (consentInformation.canRequestAds()) {
    // Safe to request ads
    MobileAds.initialize(this)
}
```

**iOS:**
```swift
if UMPConsentInformation.sharedInstance.canRequestAds {
    MobileAds.shared.start()
}
```

### Privacy Options Entry Point

- [ ] **Check** `privacyOptionsRequirementStatus` after consent info update.
- [ ] **If required**, display a visible UI element (button/link) in your app settings that calls `showPrivacyOptionsForm()` (Android) or `presentPrivacyOptionsForm(from:)` (iOS).
- [ ] **This allows users** to change their consent preferences at any time.

### iOS App Tracking Transparency (ATT)

- [ ] **Add to Info.plist:**
```xml
<key>NSUserTrackingUsageDescription</key>
<string>This identifier will be used to deliver personalized ads to you.</string>
```

- [ ] **Request ATT permission before loading ads** (iOS 14.5+):
```swift
import AppTrackingTransparency

ATTrackingManager.requestTrackingAuthorization { status in
    // Now load ads - IDFA will be used if authorized
    MobileAds.shared.start()
}
```

- [ ] **2025 requirement** — ATT prompt must now specify actual partner names (e.g., "Share with Google for advertising") rather than generic "tracking for ads."
- [ ] **Ordering** — Show UMP consent form first, then ATT prompt, then initialize ads SDK.

### US State Privacy Laws (CCPA, etc.)

- [ ] **Restricted Data Processing (RDP)** — When enabled, AdMob will not serve personalized ads and will send non-personalized requests to bidders.
- [ ] **Implementation options:**
  - Use a Google CMP (Consent Management Platform)
  - Use a third-party CMP
  - Use an in-house CMP to communicate GPP (Global Privacy Protocol) signals
  - Use the IAB US Privacy String (deprecated; Google recommends migrating to GPP)
- [ ] **Covered states (as of 2025-2026):** California (CCPA/CPRA), Virginia, Colorado, Connecticut, Utah, Iowa, Delaware, New Jersey, Nebraska, New Hampshire, Tennessee, Minnesota, Maryland, Indiana, Kentucky, Rhode Island.

### TCF v2.3 Transition (Deadline: February 28, 2026)

- [ ] **All publishers and CMPs** must transition to IAB Europe's Transparency and Consent Framework (TCF) v2.3 by **February 28, 2026**.
- [ ] **Google's systems** can already accept and process TCF v2.3 strings.
- [ ] **Do not use cached consent** — Always call `requestConsentInfoUpdate()` to avoid TCF 3.3 errors from expired consent strings.

### Testing Consent (Debug Only)

- [ ] **Register test device ID** using `ConsentDebugSettings.Builder().addTestDeviceHashedId("YOUR_HASH")` (Android) or debug settings on iOS.
- [ ] **Force geography** using `setDebugGeography()` to simulate EEA/UK users.
- [ ] **Reset consent state** using `reset()` method for testing first-install scenarios.
- [ ] **Remove all debug/test consent code before release.**

---

## 10. LINKING ADMOB TO FIREBASE AND GOOGLE PLAY CONSOLE

### Linking AdMob to Firebase

**Path:** AdMob console > Settings > Linked services

**Prerequisites:**
- [ ] **AdMob permissions** — You need administrator permissions in AdMob.
- [ ] **Firebase permissions** — You need `firebase.links.create` IAM permission (included in Owner role and Firebase Admin role).
- [ ] **User Metrics enabled** — Must be turned on in AdMob app settings before linking.

**Steps:**
- [ ] Sign in to AdMob at https://admob.google.com.
- [ ] Click **Settings** in the sidebar.
- [ ] Click **Linked services**.
- [ ] Find the app you want to link and click its row.
- [ ] Toggle on **Firebase linking**.
- [ ] Choose to **link an existing Firebase app** or **create a new Firebase project**.
- [ ] Click **Link app**.

**Benefits of linking:**
- Google Analytics integration with ad revenue data
- Enhanced user engagement and monetization reporting
- Access to Firebase A/B testing for ad placements
- Predictive analytics for ad revenue
- Audience segmentation based on ad behavior

### Linking AdMob to Google Play Console

- [ ] **This happens automatically** when you link your AdMob app to a published Google Play app via the app store linking in Section 2.
- [ ] **Ensure** the package name in AdMob matches the package name in Google Play Console.
- [ ] **Revenue data** from AdMob will appear in Play Console financial reports after linking.

---

## 11. PAYMENT SETUP AND THRESHOLDS

### Payment Thresholds

| Milestone | Threshold | Action |
|-----------|-----------|--------|
| Verification trigger | ~$10 (or local equivalent) | Identity verification and PIN mailing initiated |
| Minimum payout | **$100** (or local equivalent) | Payments are issued once balance reaches this amount |
| Account cancellation payout | $10 minimum | If canceling, you can withdraw if balance is at least $10 |

### Payment Schedule

- [ ] **Monthly cycle** — Earnings accumulate throughout the month.
- [ ] **Payment date** — Around the **21st of the following month**. Example: November earnings are paid around December 21st.
- [ ] **Delivery** — Payment should arrive by the end of the month it was issued.

### Payment Methods (varies by country)

- [ ] **Electronic Funds Transfer (EFT)** — Direct bank deposit (most common).
- [ ] **Wire transfer** — International bank transfer.
- [ ] **SEPA (Single Euro Payments Area)** — For publishers in SEPA member countries.
- [ ] **Check** — Mailed paper check (limited availability, being phased out in many regions).

### Payment Setup Steps

- [ ] **Path:** AdMob console > **Payments** > **Payment settings**.
- [ ] **Add payment method** — Enter bank account details (account number, routing number / IBAN / SWIFT).
- [ ] **Tax information** — Complete tax forms as required by your country (e.g., W-9 for US, W-8BEN for non-US).
- [ ] **Verify bank account** — Google may send a small test deposit to verify your bank details.
- [ ] **Set payment threshold** — Default is $100; can be changed to higher amounts in settings.

---

## 12. AD CONTENT FILTERS AND BLOCKING CONTROLS
**Path:** AdMob console > Blocking controls

### General Category Blocking

- [ ] **Path:** Blocking controls > Manage > General categories.
- [ ] **Max blocks:** Up to 200 general categories can be blocked.
- [ ] **Categories include:** Apparel, Internet, Real Estate, Vehicles, Dating, etc.
- [ ] **Scope** — Can be applied to a single app or across your entire AdMob account.
- [ ] **Note:** Category filtering uses automatic classification; some ads may slip through.

### Sensitive Category Blocking

- [ ] **Path:** Blocking controls > Manage > Sensitive categories.
- [ ] **Max blocks:** Up to 50 sensitive categories can be blocked.
- [ ] **Categories include:** Alcohol, Gambling, Politics, Religion, Significant Skin Exposure (being removed July 30, 2025), etc.

### Advertiser URL Blocking

- [ ] **Path:** Blocking controls > Advertiser URLs.
- [ ] **Block specific advertiser domains** to prevent their ads from appearing in your app.

### Ad Network Blocking

- [ ] **Path:** Blocking controls > Ad networks.
- [ ] **Block entire ad networks** from serving ads in your app.

### App Install Ad Blocking

- [ ] **Path:** Blocking controls > App install ads.
- [ ] **Block ads** that promote specific app installs.

### Maximum Ad Content Rating

- [ ] **Path:** Can be set per-app or per-account in the AdMob console OR programmatically via SDK.
- [ ] **Programmatic configuration (Android):**
```kotlin
MobileAds.setRequestConfiguration(
    RequestConfiguration.Builder()
        .setMaxAdContentRating(RequestConfiguration.MAX_AD_CONTENT_RATING_G)
        .build()
)
```
- [ ] **Rating levels:**
  - `MAX_AD_CONTENT_RATING_G` — General Audiences
  - `MAX_AD_CONTENT_RATING_PG` — Parental Guidance
  - `MAX_AD_CONTENT_RATING_T` — Teen
  - `MAX_AD_CONTENT_RATING_MA` — Mature Audiences
- [ ] **Behavior** — Ads returned will have a content rating at or below the configured level.

### Child-Directed Treatment (COPPA)

- [ ] **Set via `setTagForChildDirectedTreatment()`:**
  - `TAG_FOR_CHILD_DIRECTED_TREATMENT_TRUE` — Content is child-directed. Blocks Android Advertising ID transmission.
  - `TAG_FOR_CHILD_DIRECTED_TREATMENT_FALSE` — Content is not child-directed.
  - `TAG_FOR_CHILD_DIRECTED_TREATMENT_UNSPECIFIED` — No indication.

### Under Age of Consent (GDPR)

- [ ] **Set via `setTagForUnderAgeOfConsent()`:**
  - `TAG_FOR_UNDER_AGE_OF_CONSENT_TRUE` — Disables personalized ads and remarketing for EEA users under consent age.
  - `TAG_FOR_UNDER_AGE_OF_CONSENT_FALSE` — Standard treatment.
  - `TAG_FOR_UNDER_AGE_OF_CONSENT_UNSPECIFIED` — Not specified.
- [ ] **IMPORTANT:** Do not set both child-directed treatment and under-age-of-consent to `TRUE` simultaneously. If both are true, child-directed takes precedence.

### Global Configuration

- [ ] **`RequestConfiguration`** applies to ALL ad requests app-wide. Set it before initializing the SDK:
```kotlin
MobileAds.setRequestConfiguration(
    RequestConfiguration.Builder()
        .setMaxAdContentRating(RequestConfiguration.MAX_AD_CONTENT_RATING_T)
        .setTagForChildDirectedTreatment(
            RequestConfiguration.TAG_FOR_CHILD_DIRECTED_TREATMENT_FALSE)
        .setTagForUnderAgeOfConsent(
            RequestConfiguration.TAG_FOR_UNDER_AGE_OF_CONSENT_FALSE)
        .build()
)
```

---

## 13. VERIFICATION AND IDENTITY REQUIREMENTS

### Summary of All Verification Steps

| Step | Trigger | Deadline | Consequence |
|------|---------|----------|-------------|
| Identity verification | ~$10 earnings | 45 days | Ad serving stopped |
| Address verification (PIN) | After identity verification | 4 months | Ad serving stopped |
| app-ads.txt verification | New apps (Jan 2025+); all apps (phased 2025) | Ongoing | Limited ad serving |
| Payment method verification | Before first payment | Before payout | Payment withheld |

### Identity Verification Details

- [ ] **Triggered automatically** when earnings reach ~$10.
- [ ] **Document types accepted:** Passport, driver's license, national ID card.
- [ ] **Requirements:**
  - Full name on document must match AdMob account name.
  - Document must be current (not expired).
  - Photo must capture the entire document.
  - High resolution, in focus, readable.
- [ ] **Timeline:** 45 days to submit. Verification typically takes a few business days after submission.
- [ ] **Failure:** If not completed in 45 days, ad serving is suspended.

### Publisher Policies Compliance

- [ ] **Ongoing requirement** — Your account must remain compliant with Google Publisher Policies at all times.
- [ ] **Policy violations** — May result in: warning, ad serving limitation, ad serving suspension, or account termination.
- [ ] **Policy center** — Monitor your compliance status at: AdMob console > **Policy center**.

---

## 14. RECENT CHANGES AND REQUIREMENTS (2025-2026)

### SDK Version Changes

- [ ] **Current Android SDK:** `com.google.android.gms:play-services-ads:25.0.0`
- [ ] **Current iOS SDK:** v12.0.0 (Swift API changes: GAD prefix removed, GAM renamed to AdManager, GADM renamed to Mediation, Swift 6 concurrency support, requires Xcode 16.0).
- [ ] **Deprecation:** iOS SDK v10.x.x is deprecated and will sunset in **Q2 2026**.
- [ ] **Sunset:** iOS SDK v9.x.x will sunset on **June 30, 2025**.

### Policy Changes (2025)

- [ ] **January 2025** — app-ads.txt becomes mandatory for new apps registered in AdMob. Existing apps phased in throughout 2025.
- [ ] **February 16, 2025** — Updated Google Publisher Policies: publishers must clearly disclose data collection, sharing, and usage in connection with Google services.
- [ ] **March 2025** — Online gambling restriction updated: gambling content ads must only be shown to users in the 18 allowed countries.
- [ ] **July 30, 2025** — "Significant Skin Exposure" sensitive category removed from Blocking controls.
- [ ] **September 2025** — Political advertising restricted in the EU under EU Regulation 2024/900.

### API Changes (2026)

- [ ] **February 5, 2026** — `getLargeAnchoredAdaptiveBannerAdSize` replaces `getCurrentOrientationAnchoredAdaptiveBannerAdSize` with updated sizing logic for modern devices.
- [ ] **February 28, 2026** — TCF v2.3 transition deadline. All publishers and CMPs must support TCF v2.3.

### New US State Privacy Laws (2025-2026)

- [ ] **July 1, 2025** — Tennessee Information Protection Act, Minnesota Consumer Data Privacy Act.
- [ ] **October 1, 2025** — Maryland Online Data Privacy Act.
- [ ] **2025** — Indiana Consumer Data Protection Act, Kentucky Consumer Data Protection Act.
- [ ] **January 2026** — Rhode Island Data Transparency and Privacy Protection Act.

### Mediation Updates (July 2025)

- [ ] **New bidding partners:** InMobi, ironSource, Unity (now available to all AdMob publishers).
- [ ] **Enhanced integration:** Liftoff and Mintegral added support for open ads.
- [ ] **New partners:** Moloco and LINE joined the platform.

### Privacy & Messaging Report

- [ ] **New report type** available in AdMob console showing how users interact with consent messages in your apps.

---

## QUICK REFERENCE: COMPLETE IMPLEMENTATION ORDER

1. Create AdMob account and complete initial setup.
2. Register your app in AdMob and copy the App ID.
3. Create ad units for each format you need and copy ad unit IDs.
4. Add SDK dependencies (Gradle/CocoaPods/SPM).
5. Configure AndroidManifest.xml / Info.plist with App ID.
6. Set up GDPR consent flow (UMP SDK) and ATT (iOS).
7. Initialize MobileAds SDK (after consent, on background thread).
8. Implement ad loading and display for each format.
9. Set content rating and child-directed tags if applicable.
10. Test with test ad unit IDs and registered test devices.
11. Use Ad Inspector to verify integration.
12. Set up app-ads.txt and host it.
13. Link AdMob to Firebase (optional but recommended).
14. Link app to app store in AdMob console.
15. Configure blocking controls and content filters.
16. Set up mediation (if using multiple ad networks).
17. Declare ads and advertising ID usage in Google Play Console.
18. Replace all test ad unit IDs with production IDs.
19. Remove all test device code.
20. Submit app for review and publish.
21. Complete identity and address verification when prompted.
22. Set up payment method and tax information.
23. Monitor Policy center for compliance issues.

---

## Sources

- [AdMob Android Quick Start](https://developers.google.com/admob/android/quick-start)
- [AdMob iOS Quick Start](https://developers.google.com/admob/ios/quick-start)
- [AdMob Android Test Ads](https://developers.google.com/admob/android/test-ads)
- [AdMob iOS Test Ads](https://developers.google.com/admob/ios/test-ads)
- [AdMob Android Privacy (UMP SDK)](https://developers.google.com/admob/android/privacy)
- [AdMob iOS Privacy (UMP SDK)](https://developers.google.com/admob/ios/privacy)
- [AdMob Android Mediation](https://developers.google.com/admob/android/mediation)
- [AdMob Android Choose Networks](https://developers.google.com/admob/android/choose-networks)
- [AdMob Android Targeting](https://developers.google.com/admob/android/targeting)
- [AdMob Android Banner Ads](https://developers.google.com/admob/android/banner)
- [AdMob Android Interstitial Ads](https://developers.google.com/admob/android/interstitial)
- [AdMob Android Rewarded Ads](https://developers.google.com/admob/android/rewarded)
- [AdMob Android Native Ads](https://developers.google.com/admob/android/native/start)
- [AdMob Android App Open Ads](https://developers.google.com/admob/android/app-open)
- [AdMob Android Ad Inspector](https://developers.google.com/admob/android/ad-inspector)
- [AdMob Android app-ads.txt](https://developers.google.com/admob/android/app-ads)
- [Set up app-ads.txt (AdMob Help)](https://support.google.com/admob/answer/9363762)
- [app-ads.txt Mandatory Policy (January 2025)](https://ppc.land/new-admob-policy-requires-app-ads-txt-from-january-2025/)
- [AdMob Sign Up](https://support.google.com/admob/answer/7356219)
- [AdMob Age Requirements](https://support.google.com/admob/answer/2785008)
- [AdMob Payment Thresholds](https://support.google.com/admob/answer/2772208)
- [AdMob Payments and Transactions](https://support.google.com/admob/answer/2772140)
- [AdMob Address Verification (PIN)](https://support.google.com/admob/answer/2772302)
- [AdMob Identity Verification](https://support.google.com/admob/answer/13030080)
- [Link Apps to Firebase](https://support.google.com/admob/answer/6383165)
- [Link AdMob to Firebase (Firebase Help)](https://support.google.com/firebase/answer/6387949)
- [AdMob Policies and Restrictions](https://support.google.com/admob/answer/6128543)
- [AdMob Behavioral Policies](https://support.google.com/admob/answer/2753860)
- [AdMob Policy Change Log](https://support.google.com/admob/answer/9391084)
- [Block Ads by General Category](https://support.google.com/admob/answer/3150174)
- [Block Ads by Sensitive Category](https://support.google.com/admob/answer/3150176)
- [Ad Blocking Options](https://support.google.com/admob/answer/3150235)
- [Link App to App Store](https://support.google.com/admob/answer/10037806)
- [Set up App in AdMob](https://support.google.com/admob/answer/9989980)
- [Google Play Console Ads Declaration](https://support.google.com/googleplay/android-developer/answer/9857753)
- [Google Play Console Advertising ID](https://support.google.com/googleplay/android-developer/answer/6048248)
- [AdMob US State Privacy Compliance](https://support.google.com/admob/answer/9561022)
- [2025 AdMob Release Archive](https://support.google.com/admob/answer/16368266)
- [AdMob Android Release Notes](https://developers.google.com/admob/android/rel-notes)
- [AdMob iOS Release Notes](https://developers.google.com/admob/ios/rel-notes)
- [Google Consent Requirements (EEA/UK)](https://support.google.com/admob/answer/13554116)
- [iOS Privacy Strategies](https://developers.google.com/admob/ios/privacy/strategies)
- [App Tracking Transparency (Apple)](https://developer.apple.com/documentation/apptrackingtransparency)
- [Mediation Bidding Partners](https://support.google.com/admob/answer/12374909)
- [Waterfall Ad Sources](https://support.google.com/admob/answer/3245073)
