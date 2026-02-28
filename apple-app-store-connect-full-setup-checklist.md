# Apple App Store Connect — Full Setup & Publishing Checklist

> **Last updated:** February 2026
> **Covers:** Developer Account, App Creation, Listings, IAP, Subscriptions, TestFlight, Signing, Agreements, Review, and Release.
> **Official portal:** [App Store Connect](https://appstoreconnect.apple.com) | [Apple Developer](https://developer.apple.com)

---

## Table of Contents

1. [Apple Developer Account Setup](#1-apple-developer-account-setup)
2. [App Store Connect — App Creation](#2-app-store-connect--app-creation)
3. [App Store Listing (Product Page)](#3-app-store-listing-product-page)
4. [App Information (Category, Age Rating, Content Rights)](#4-app-information-category-age-rating-content-rights)
5. [Pricing and Availability](#5-pricing-and-availability)
6. [App Privacy](#6-app-privacy)
7. [App Review Information](#7-app-review-information)
8. [Build Upload](#8-build-upload)
9. [TestFlight Setup](#9-testflight-setup)
10. [In-App Purchases (IAP) — Full Setup](#10-in-app-purchases-iap--full-setup)
11. [Subscriptions — Full Setup](#11-subscriptions--full-setup)
12. [Agreements, Tax, and Banking](#12-agreements-tax-and-banking)
13. [App Signing](#13-app-signing)
14. [App Review Guidelines — Key Requirements](#14-app-review-guidelines--key-requirements)
15. [Submission and Release](#15-submission-and-release)
16. [Recent Changes and Requirements (2025–2026)](#16-recent-changes-and-requirements-20252026)

---

## 1. Apple Developer Account Setup

> **Console:** [developer.apple.com/account](https://developer.apple.com/account)
> **Enrollment:** [developer.apple.com/programs/enroll](https://developer.apple.com/programs/enroll)

### Prerequisites

- [ ] **Apple Account (Apple ID)** — Create one at [appleid.apple.com](https://appleid.apple.com) if you do not already have one
- [ ] **Two-factor authentication** enabled on the Apple Account (mandatory)
- [ ] **Legal age of majority** in your jurisdiction (typically 18+)
- [ ] **Valid government-issued photo ID** for identity verification
- [ ] **Mac with the latest macOS** (recommended for Xcode and signing workflows)

### Individual Enrollment

- [ ] Sign in at [developer.apple.com/programs/enroll](https://developer.apple.com/programs/enroll)
- [ ] Select **Individual / Sole Proprietor**
- [ ] Verify identity (Apple may use the Apple Account app on a device, or manual ID upload)
- [ ] Pay annual fee: **$99 USD/year** (prices vary by region and are shown in local currency)
- [ ] Wait for enrollment approval (typically 24–48 hours)

### Organization Enrollment

- [ ] **D-U-N-S Number** — Required for all organizations (not required for individuals)
  - [ ] Check if your organization already has one: [developer.apple.com/enroll/duns-lookup](https://developer.apple.com/enroll/duns-lookup)
  - [ ] If not, request a free D-U-N-S Number through Apple's lookup tool (provided by Dun & Bradstreet)
  - [ ] D-U-N-S Number is a **unique 9-digit identifier** assigned by Dun & Bradstreet
  - [ ] Processing time: **Up to 14 business days** for a new number
  - [ ] After receiving the D-U-N-S Number, allow **2 additional business days** for Apple to receive the information from D&B
- [ ] Organization must be a **legal entity** (no DBAs, fictitious businesses, trade names, or branches)
- [ ] Enrolling person must have **legal authority** to bind the organization to Apple's agreements
- [ ] Organization **legal entity name** must match the D-U-N-S registration exactly
- [ ] **Website domain** associated with the organization (Apple verifies this)
- [ ] Pay annual fee: **$99 USD/year**
- [ ] Wait for enrollment approval (may take several days; Apple may contact for verification)

### Post-Enrollment

- [ ] Access **Apple Developer account** at [developer.apple.com/account](https://developer.apple.com/account)
- [ ] Access **App Store Connect** at [appstoreconnect.apple.com](https://appstoreconnect.apple.com)
- [ ] Download and install **Xcode** from the Mac App Store (latest stable version)
- [ ] Sign in to Xcode with your Apple Account under **Xcode > Settings > Accounts**
- [ ] Invite team members (if organization) via **App Store Connect > Users and Access**

### Roles Available in App Store Connect

| Role | Key Permissions |
|------|----------------|
| **Account Holder** | Full access, legal agreements, bank/tax info |
| **Admin** | Manage apps, users, TestFlight, reports |
| **App Manager** | Manage specific apps, metadata, pricing |
| **Developer** | Upload builds, manage TestFlight builds |
| **Marketing** | Manage marketing assets, product pages |
| **Finance** | View financial reports, download sales data |
| **Sales** | View sales data, download reports |
| **Customer Support** | Respond to customer reviews |

---

## 2. App Store Connect — App Creation

> **Console:** App Store Connect > **My Apps** > **(+) New App**

### Register Bundle ID

- [ ] Go to **[developer.apple.com/account/resources/identifiers](https://developer.apple.com/account/resources/identifiers)**
- [ ] Click **(+)** to register a new identifier
- [ ] Select **App IDs** > **App**
- [ ] Enter a **Description** (human-readable name)
- [ ] Enter a **Bundle ID** using reverse-domain notation (e.g., `com.company.appname`)
  - Must be unique across the entire App Store
  - **Cannot be changed** after first build upload
  - Must match the Bundle Identifier in your Xcode project
- [ ] Select **Capabilities** your app needs (Push Notifications, In-App Purchase, Sign in with Apple, etc.)
- [ ] Click **Continue** > **Register**

### Create the App Record in App Store Connect

- [ ] Navigate to **App Store Connect > My Apps > (+) > New App**
- [ ] Fill in required fields:
  - [ ] **Platform(s):** iOS, macOS, tvOS, watchOS, visionOS (select all that apply)
  - [ ] **App Name:** Up to **30 characters** — The name displayed on the App Store
    - Must be unique on the App Store
    - Cannot include generic terms that could be confused with existing apps or Apple products
    - Cannot include trademarked terms you do not own
  - [ ] **Primary Language:** The default language for your app's metadata (e.g., English (U.S.))
    - If localized info is unavailable in a user's region, this language is used as fallback
  - [ ] **Bundle ID:** Select the registered Bundle ID from the dropdown
  - [ ] **SKU (Stock Keeping Unit):** A unique internal identifier for your app
    - Not visible to users
    - Can be any alphanumeric string (e.g., `MYAPP001`, `com.company.appname.v1`)
    - Used in sales reports and internal tracking
    - **Cannot be changed** after creation
  - [ ] **User Access:** Full Access or Limited Access (if restricting to specific users)
- [ ] Click **Create**

---

## 3. App Store Listing (Product Page)

> **Console:** App Store Connect > **My Apps** > [Your App] > **App Store** tab > [Platform] version

### App Name and Subtitle

- [ ] **App Name:** Up to **30 characters**
  - Displayed prominently on the App Store
  - Indexed for search; include a relevant keyword if natural
  - Cannot use generic terms like "app" or competitor brand names
- [ ] **Subtitle:** Up to **30 characters**
  - Appears directly below the app name in search results and on the product page
  - Use to expand on your value proposition
  - Indexed for App Store search

### Description

- [ ] **Description:** Up to **4,000 characters**
  - Plain text only (no HTML, no markdown rendering)
  - Line breaks are supported
  - First 1–3 sentences are visible before "Read More" — make them count
  - Describe features, functionality, and value proposition
  - Cannot be updated without submitting a new app version

### Promotional Text

- [ ] **Promotional Text:** Up to **170 characters**
  - Appears above the description on iOS 11+ product pages
  - **Can be updated at any time** without a new app version
  - Use for time-sensitive announcements, seasonal promotions, or current campaigns

### What's New (Version Release Notes)

- [ ] **What's New in This Version:** Up to **4,000 characters**
  - Required for all app updates (not required for initial version)
  - Describe new features, improvements, and bug fixes
  - Be specific — vague notes like "bug fixes and improvements" are discouraged

### Keywords

- [ ] **Keywords:** Up to **100 characters** total
  - Separate keywords with **commas, no spaces** (e.g., `photo,editor,filter,camera,effects`)
  - Each keyword must be at least 2 characters
  - Do not duplicate your app name or company name (already indexed automatically)
  - Do not use other apps' names, company names, or trademarked terms
  - Do not use the words "app" or "free"
  - Localizable per language
  - Single words perform better than phrases

### URLs

- [ ] **Support URL:** Required — full URL with protocol (e.g., `https://example.com/support`)
  - Must lead to actual contact information (email, phone, or address)
  - Required by law in many regions
- [ ] **Marketing URL:** Optional — full URL with protocol
  - Links to your marketing website or landing page

### Copyright

- [ ] **Copyright:** Required — format: `YYYY Company Name` (e.g., `2026 My Company, Inc.`)
  - The copyright symbol is added automatically by Apple

### Screenshots

> **Console:** App Store Connect > [App] > [Version] > **Media** section

**General Requirements:**
- [ ] Format: `.png` or `.jpg` / `.jpeg`
- [ ] Quantity: **Minimum 1, maximum 10** per device size per localization
- [ ] Must be actual screenshots of the app (text/graphics overlays allowed)
- [ ] Do not include device bezels unless they match the actual device

**iPhone Screenshots (Required for iPhone apps):**

| Display Size | Devices | Portrait (px) | Landscape (px) |
|---|---|---|---|
| **6.9"** (Primary — Required) | iPhone Air, 17 Pro Max, 16 Pro Max, 16 Plus, 15 Pro Max, 15 Plus, 14 Pro Max | **1320 x 2868** (recommended) | 2868 x 1320 |
| 6.9" (alt) | Same as above | 1290 x 2796 | 2796 x 1290 |
| 6.9" (alt) | Same as above | 1260 x 2736 | 2736 x 1260 |
| **6.5"** | iPhone 14 Plus, 13 Pro Max, 12 Pro Max, 11 Pro Max, XS Max, XR | **1284 x 2778** or **1242 x 2688** | 2778 x 1284 or 2688 x 1242 |
| **6.3"** | iPhone 17 Pro, 17, 16 Pro, 16, 15 Pro, 15, 14 Pro | **1206 x 2622** or **1179 x 2556** | 2622 x 1206 or 2556 x 1179 |
| **6.1"** | iPhone 16e, 14, 13, 12, 11 Pro, XS, X | **1170 x 2532** or **1125 x 2436** or **1080 x 2340** | various |
| **5.5"** | iPhone 8 Plus, 7 Plus, 6S Plus | 1242 x 2208 | 2208 x 1242 |
| **4.7"** | iPhone SE (3rd/2nd gen), 8, 7, 6S | 750 x 1334 | 1334 x 750 |
| **4"** | iPhone SE (1st gen), 5S, 5C, 5 | 640 x 1136 | 1136 x 640 |

> **Tip:** Upload the **6.9-inch** size (1320 x 2868). Apple auto-scales to smaller iPhones. Upload **6.5-inch** size only if you want device-specific screenshots for older models.

**iPad Screenshots (Required if app runs on iPad):**

| Display Size | Devices | Portrait (px) | Landscape (px) |
|---|---|---|---|
| **13"** (Primary — Required) | iPad Pro (M5, M4, 6th–1st gen), iPad Air (M3, M2) | **2064 x 2752** (recommended) | 2752 x 2064 |
| 13" (alt) | Same | 2048 x 2732 | 2732 x 2048 |
| **11"** | iPad Pro, iPad Air (various), iPad (A16, 10th gen), iPad mini | 1488 x 2266 or 1668 x 2420 or 1668 x 2388 or 1640 x 2360 | various |
| **10.5"** | iPad Pro, iPad Air (3rd gen), iPad (9th–7th gen) | 1668 x 2224 | 2224 x 1668 |
| **9.7"** | iPad (older), iPad mini (5th gen and older) | 1536 x 2048 | 2048 x 1536 |

> **Tip:** Upload the **13-inch** size (2064 x 2752). Apple auto-scales to smaller iPads.

**Apple Watch Screenshots (Required for watchOS apps):**

| Device | Dimensions (px) |
|---|---|
| Ultra 3 | 422 x 514 |
| Ultra 2, Ultra | 410 x 502 |
| Series 11, Series 10 | 416 x 496 |
| Series 9, 8, 7 | 396 x 484 |
| Series 6, 5, 4, SE 3, SE | 368 x 448 |
| Series 3 | 312 x 390 |

**Apple TV Screenshots (Required for tvOS apps):**

| Resolution | Dimensions (px) |
|---|---|
| HD | 1920 x 1080 |
| 4K | 3840 x 2160 |

**Apple Vision Pro Screenshots (Required for visionOS apps):**

| Resolution | Dimensions (px) |
|---|---|
| Standard | 3840 x 2160 |

**Mac Screenshots (Required for macOS apps):**

| Aspect Ratio | Dimensions (px) |
|---|---|
| 16:10 | 2880 x 1800, 2560 x 1600, 1440 x 900, or 1280 x 800 |

### App Preview Videos

- [ ] **Duration:** 15–30 seconds
- [ ] **Max file size:** 500 MB
- [ ] **Max previews:** Up to **3 per device size per localization**
- [ ] **Orientation:** Portrait or Landscape for iOS; Landscape only for macOS, tvOS, visionOS
- [ ] **Content:** Must contain **only screen captures** recorded on the device — no live-action footage, no simulated interactions, no hands operating the device

**Supported Codecs and Formats:**

| Codec | File Formats | Target Bit Rate | Max FPS | Audio |
|---|---|---|---|---|
| H.264 | `.mov`, `.m4v`, `.mp4` | 10–12 Mbps | 30 fps | Stereo, 256 kbps AAC, 44.1/48 kHz |
| ProRes 422 (HQ only) | `.mov` | ~220 Mbps VBR | 30 fps | Stereo, PCM or 256 kbps AAC, 44.1/48 kHz |

**Video Resolutions by Device:**

| Device Category | Portrait (px) | Landscape (px) |
|---|---|---|
| iPhone 6.9"/6.5"/6.3"/6.1" | 886 x 1920 | 1920 x 886 |
| iPhone 5.5" | 1080 x 1920 | 1920 x 1080 |
| iPhone 4.7" | 750 x 1334 | 1334 x 750 |
| iPad 13"/12.9"/11"/10.5" | 1200 x 1600 | 1600 x 1200 |
| iPad 9.7" | 900 x 1200 | 1200 x 900 |
| Mac | N/A | 1920 x 1080 |
| Apple TV | N/A | 1920 x 1080 |
| Apple Vision Pro | N/A | 3840 x 2160 |

---

## 4. App Information (Category, Age Rating, Content Rights)

> **Console:** App Store Connect > [App] > **General** > **App Information**

### Category

- [ ] **Primary Category:** Required — Select the most accurate category for your app
- [ ] **Secondary Category:** Optional — Select a second relevant category

**Available App Categories:**

| Category | Category |
|---|---|
| Books | Business |
| Developer Tools | Education |
| Entertainment | Finance |
| Food & Drink | Graphics & Design |
| Health & Fitness | Kids |
| Lifestyle | Magazines & Newspapers |
| Medical | Music |
| Navigation | News |
| Photo & Video | Productivity |
| Reference | Safari Extensions |
| Shopping | Social Networking |
| Sports | Travel |
| Utilities | Weather |

**Games Subcategories:** Action, Adventure, Board, Card, Family, Music, Puzzle, Racing, Role Playing, Simulation, Sports, Strategy

- [ ] If your app is a Game, select up to **2 Games subcategories**
- [ ] If your app is for children, check the **"Made for Kids"** designation and select the appropriate age band: Ages 5 and Under, Ages 6–8, or Ages 9–11

### Age Rating

> **Console:** App Store Connect > [App] > **General** > **App Information** > **Age Rating**

- [ ] Complete the **age rating questionnaire** — Apple generates the rating based on your answers
- [ ] Questionnaire covers:
  - [ ] Cartoon or Fantasy Violence (frequency: None, Infrequent/Mild, Frequent/Intense)
  - [ ] Realistic Violence
  - [ ] Prolonged Graphic or Sadistic Realistic Violence
  - [ ] Profanity or Crude Humor
  - [ ] Mature/Suggestive Themes
  - [ ] Horror/Fear Themes
  - [ ] Medical/Treatment Information
  - [ ] Simulated Gambling
  - [ ] Sexual Content and Nudity
  - [ ] Alcohol, Tobacco, or Drug Use or References
  - [ ] Contests
  - [ ] Unrestricted Web Access
  - [ ] Gambling with Real Currency
  - [ ] **In-app controls** (new 2025): chatbot/AI interactions, user-generated content capabilities
  - [ ] **Capabilities** (new 2025): location sharing, account creation

**Age Rating Values (Updated July 2025):**

| Rating | Description |
|---|---|
| 4+ | Suitable for all ages |
| 9+ | May contain mild content |
| 13+ | (NEW) May contain content suitable for ages 13+ |
| 16+ | (NEW) May contain content suitable for ages 16+ |
| 18+ | (NEW) Restricted to adults only |

> **Important:** The old 12+ and 17+ ratings have been removed. Complete the **updated age rating questionnaire** by **January 31, 2026** to avoid submission delays.

- [ ] If your app requires a **higher minimum user age** than the auto-assigned rating, you may override it with a higher rating

### Content Rights

- [ ] If your app contains, displays, or accesses third-party content, confirm you have the **rights to use that content**
- [ ] Check the box: **"This app contains, shows, or accesses third-party content"** (if applicable)
- [ ] Check the box: **"I have the rights to distribute this app's content"**

---

## 5. Pricing and Availability

> **Console:** App Store Connect > [App] > **General** > **Pricing and Availability**

### Price Schedule

- [ ] Select a **base price** (or Free) from Apple's price tier system
  - Apple offers **900+ price points** starting at $0.29 USD
  - Prices are set per storefront (175+ countries/regions)
  - Apple auto-generates equalized prices for all regions based on your base country
  - You can manually override prices for individual storefronts
- [ ] **Schedule price changes:** Set future price changes with effective dates (up to end of next calendar year)
- [ ] Apple collects **30% commission** on all sales (or **15% for Small Business Program** participants earning under $1M/year)

### Country/Region Availability

- [ ] Select which **countries and regions** your app should be available in
- [ ] Default: Available in all 175+ App Store territories
- [ ] You can exclude specific countries/regions as needed
- [ ] Some regions may have additional legal or regulatory requirements

### Pre-Orders

- [ ] **Enable pre-orders** (optional) — allows customers to order your app before release
  - Available up to **180 days** before release date
  - Set a release date
  - Customers are charged when the app is released
  - You can provide screenshots and descriptions for the product page before the app is ready

---

## 6. App Privacy

> **Console:** App Store Connect > [App] > **General** > **App Privacy**

### Privacy Policy URL

- [ ] **Privacy Policy URL:** Required for ALL apps
  - Must be a publicly accessible URL
  - Must clearly describe data collection and usage practices
  - Must be accessible from within the app
  - Must be in the language(s) your app supports

### Privacy Nutrition Labels (Data Collection Declarations)

- [ ] Navigate to **App Privacy** section and click **Get Started** or **Edit**
- [ ] Answer whether **you or your third-party partners** collect data from your app
- [ ] If yes, declare ALL data types collected:

**Data Type Categories:**

| Category | Sub-Types |
|---|---|
| **Contact Info** | Name, Email Address, Phone Number, Physical Address, Other User Contact Info |
| **Health & Fitness** | Health, Fitness |
| **Financial Info** | Payment Info, Credit Info, Other Financial Info |
| **Location** | Precise Location, Coarse Location |
| **Sensitive Info** | Sensitive Info (race, ethnicity, sexual orientation, biometric data, etc.) |
| **Contacts** | Contacts |
| **User Content** | Emails/Text Messages, Photos/Videos, Audio Data, Gameplay Content, Customer Support, Other User Content |
| **Browsing History** | Browsing History |
| **Search History** | Search History |
| **Identifiers** | User ID, Device ID |
| **Purchases** | Purchase History |
| **Usage Data** | Product Interaction, Advertising Data, Other Usage Data |
| **Diagnostics** | Crash Data, Performance Data, Other Diagnostic Data |
| **Other Data** | Any other data types not covered above |

- [ ] For each data type, declare the **purpose** of collection:
  - Third-Party Advertising
  - Developer's Advertising or Marketing
  - Analytics
  - Product Personalization
  - App Functionality
  - Other Purposes
- [ ] For each data type, declare whether:
  - [ ] Data is **linked to the user's identity**
  - [ ] Data is used for **tracking** (linking user/device data with third-party data for advertising or data broker purposes)

### Privacy Manifest File (Required since May 2024)

- [ ] Include a **`PrivacyInfo.xcprivacy`** file in your Xcode project
- [ ] Declare **Required Reason APIs** usage (if using any):
  - File timestamp APIs
  - System boot time APIs
  - Disk space APIs
  - Active keyboard APIs
  - User defaults APIs
- [ ] Include privacy manifests for **all third-party SDKs** your app uses
- [ ] Third-party SDKs must include their own privacy manifest files
- [ ] If a third-party SDK lacks a privacy manifest, update the **app-level privacy manifest** to include those details

### Account Deletion Requirement

- [ ] If your app allows users to **create an account**, you must provide a mechanism to **delete their account** from within the app
- [ ] Account deletion must remove all user data or clearly explain data retention policies

---

## 7. App Review Information

> **Console:** App Store Connect > [App] > [Version] > **App Review Information** section

### Contact Information

- [ ] **First Name:** Required
- [ ] **Last Name:** Required
- [ ] **Phone Number:** Required — with country code
- [ ] **Email Address:** Required — a monitored email where Apple can reach you during review

### Demo Account (Required if app has sign-in)

- [ ] **Username:** A valid demo account username
- [ ] **Password:** A working password for the demo account
- [ ] Credentials **must not expire** during the review period
- [ ] If app uses **2FA/MFA**, provide a code or method in the Notes field
- [ ] If app uses **Single Sign-On (SSO)**, provide instructions and test credentials
- [ ] If app has **multiple account types** (admin, user, etc.), provide credentials for each in the Notes field

### Notes for Reviewer

- [ ] **Notes:** Up to **4,000 bytes**
  - Describe all new features and functionality with specificity
  - Provide any hardware/resource instructions (e.g., Bluetooth device needed, QR code, special configurations)
  - Explain any non-obvious functionality
  - Provide streaming URLs if applicable
  - Include backend configuration details if needed
  - Accepts any language
- [ ] **Attachments:** Upload supplementary files if needed (e.g., authorization letters, partnership documentation)

### Review Tips

- [ ] Ensure all backend services are **live and accessible** during review
- [ ] Ensure the demo account has **full access** to all features being reviewed
- [ ] If the app uses **location services**, describe how to trigger location-based features or provide a test location
- [ ] If the app requires **hardware** (Bluetooth, NFC, etc.), explain how to test without the hardware or provide the hardware details

---

## 8. Build Upload

> **Console:** Xcode > **Product** > **Archive** | App Store Connect > [App] > **TestFlight** tab

### Prepare in Xcode

- [ ] Set **Version Number** in Xcode target settings (matches the version in App Store Connect, e.g., `1.0.0`)
- [ ] Set **Build Number** — must be unique and incremented for each upload (e.g., `1`, `2`, `3` or `1.0.1`)
- [ ] Set **Deployment Target** to the minimum OS version your app supports
- [ ] Select the correct **Team** and **Signing Certificate** under Signing & Capabilities
- [ ] Set the **Build Configuration** to **Release**
- [ ] Select **Any iOS Device (arm64)** (or Generic iOS Device) as the build destination

### SDK Requirements (as of 2025–2026)

| Deadline | Requirement |
|---|---|
| Now (2025) | Apps must be built with **Xcode 16** or later, using the **iOS 18 / iPadOS 18 / tvOS 18 / visionOS 2 / watchOS 11** SDK |
| April 28, 2026 | Apps must be built with **Xcode 26** or later, using the **iOS 26 / iPadOS 26 / tvOS 26 / visionOS 26 / watchOS 26** SDK |

### Archive and Upload

- [ ] **Archive:** Xcode > **Product > Archive**
  - Xcode builds the release archive
  - When complete, the **Organizer** window opens showing your archive
- [ ] **Distribute App:** In the Organizer, select the archive and click **Distribute App**
  - Select **App Store Connect** as the distribution method
  - Select **Upload** (to send to App Store Connect)
  - Choose whether to let Xcode manage signing automatically
  - Click **Upload**
- [ ] Alternative upload methods:
  - **Transporter app** (Mac App Store — for `.ipa` files)
  - **altool** command-line tool (deprecated in favor of `notarytool`)
  - **Xcode Cloud** (CI/CD)

### Build Processing

- [ ] After upload, Apple processes the build (typically **5–30 minutes**, can be longer)
- [ ] You will receive an **email notification** when processing completes
- [ ] If there are issues (missing icons, invalid entitlements, etc.), Apple sends an email with specific errors
- [ ] Processed builds appear in App Store Connect under **TestFlight** tab and in the **Build** section of the version

### Select Build for Submission

- [ ] Navigate to App Store Connect > [App] > **App Store** tab > [Version]
- [ ] Scroll to the **Build** section
- [ ] Click **(+)** to select the uploaded and processed build
- [ ] The build must be in **"Ready for Review"** state (no processing issues)

---

## 9. TestFlight Setup

> **Console:** App Store Connect > [App] > **TestFlight** tab

### General TestFlight Information

- [ ] **Test Information** — Fill in before inviting external testers:
  - [ ] **Beta App Description:** Describe what you want testers to focus on
  - [ ] **Feedback Email:** Where testers send feedback
  - [ ] **Privacy Policy URL:** Required for external testing
  - [ ] **Marketing URL:** Optional
  - [ ] **Beta App Review Notes:** Instructions for Apple's beta app review team
  - [ ] **Contact Information:** Name, phone, email for the beta review team
  - [ ] **Sign-in Information:** Demo credentials if the app requires login

### Internal Testing

- [ ] **Create Internal Group:** TestFlight > **(+)** next to **Internal Testing** > Enter group name > **Create**
- [ ] **Add Testers:** Click **Invite Testers** > Select from App Store Connect team members
- [ ] **Limits:**
  - Up to **100 internal testers** (must be App Store Connect users with at least Developer role)
  - **25 devices per tester** (each tester can install on up to 25 devices)
- [ ] **No Beta App Review required** for internal testing — builds available immediately after processing
- [ ] Internal testers receive an email/notification to install via the **TestFlight app**

### External Testing

- [ ] **Create External Group:** TestFlight > **(+)** next to **External Testing** > Enter group name > **Create**
- [ ] **Add Testers:**
  - Invite by email address
  - Share a **public link** (enable "Public Link" for the group)
- [ ] **Limits:**
  - Up to **10,000 external testers** total
- [ ] **Beta App Review:** Required for the **first build** submitted to external testers
  - Subsequent builds for the same version may not require review
  - Review typically takes **24–48 hours**
- [ ] **Add Build to Group:** Select a processed build and add it to the external group
- [ ] **Automatic Distribution:** Optionally enable automatic build distribution to groups when new builds are uploaded

### TestFlight Build Expiration

- [ ] TestFlight builds expire after **90 days** from the upload date
- [ ] Testers must update to a newer build before expiration
- [ ] Expired builds can no longer be installed

---

## 10. In-App Purchases (IAP) — Full Setup

> **Console:** App Store Connect > [App] > **Monetization** > **In-App Purchases**

### IAP Types Overview

| Type | Description | Use Cases |
|------|-------------|-----------|
| **Consumable** | Can be purchased multiple times; used up after consumption | Virtual currency, extra lives, power-ups, credits |
| **Non-Consumable** | Purchased once; permanent and transferable across devices | Premium features, ad removal, additional levels, filters |
| **Auto-Renewable Subscription** | Recurring charge at regular intervals until canceled | Streaming services, premium access, cloud storage |
| **Non-Renewing Subscription** | Access for a fixed period; does not auto-renew | Seasonal content, annual sports pass, limited access |

### Creating an IAP Product (Consumable or Non-Consumable)

- [ ] Navigate to **App Store Connect > [App] > Monetization > In-App Purchases**
- [ ] Click **(+)** to create a new In-App Purchase
- [ ] Select type: **Consumable** or **Non-Consumable**
- [ ] Fill in required fields:
  - [ ] **Reference Name:** Internal name for your use (visible in reports, not to customers)
    - Choose something descriptive (e.g., "100 Gold Coins" or "Remove Ads")
  - [ ] **Product ID:** Unique identifier used in your app code
    - Reverse-domain style recommended (e.g., `com.company.app.100coins`)
    - **Cannot be reused** even if the IAP is deleted
    - Must be unique across ALL your apps
- [ ] Click **Create**

### Configure IAP Product Details

- [ ] **Pricing:**
  - [ ] Navigate to the IAP product > **Pricing** section
  - [ ] Select a **base price** from Apple's price points ($0.29–$999.99+)
  - [ ] Apple auto-generates prices for all 175+ countries/regions
  - [ ] Optionally override individual storefront prices
  - [ ] Schedule price changes with effective dates
- [ ] **Localization:**
  - [ ] Click **(+)** to add localizations
  - [ ] For each language, provide:
    - [ ] **Display Name:** The name customers see (up to 30 characters)
    - [ ] **Description:** Product description for customers (up to 45 characters)
- [ ] **Review Information:**
  - [ ] **Screenshot:** Upload a screenshot of the IAP in use within your app
    - Must be an actual screenshot from the app
    - Shows the reviewer what the customer sees
  - [ ] **Review Notes:** Optional notes explaining the IAP's purpose and functionality
- [ ] **Family Sharing:** Enable if the purchase should be shared across Family Sharing members (Non-Consumable only)

### IAP Review and Submission

- [ ] First IAP **must be submitted with a new version** of the app
- [ ] Subsequent IAPs can be submitted with or without a new app version
- [ ] Each IAP goes through App Review independently
- [ ] IAP statuses: Missing Metadata, Ready to Submit, Waiting for Review, In Review, Approved, Developer Action Needed, Rejected

### StoreKit 2 Integration Basics

- [ ] **Import StoreKit** in your Swift code: `import StoreKit`
- [ ] **Load Products:**
  ```swift
  let products = try await Product.products(for: ["com.company.app.100coins"])
  ```
- [ ] **Purchase:**
  ```swift
  let result = try await product.purchase()
  switch result {
  case .success(let verification):
      let transaction = try checkVerified(verification)
      // Deliver content
      await transaction.finish()
  case .userCancelled, .pending:
      break
  }
  ```
- [ ] **Transaction Listener:** Set up a listener for unfinished transactions
  ```swift
  Task {
      for await result in Transaction.updates {
          // Handle transaction updates
      }
  }
  ```
- [ ] **Restore Purchases:** Provide a **Restore Purchases** button (required by App Review)
  ```swift
  try await AppStore.sync()
  ```

### Server-Side Validation

- [ ] Set up a server endpoint to validate purchases
- [ ] Use the **App Store Server API** (replaces deprecated `verifyReceipt` endpoint)
- [ ] Authenticate using **JWT** (JSON Web Token):
  - Generate a private key in App Store Connect > **Users and Access** > **Integrations** > **In-App Purchase**
  - Use the key to sign JWTs for API requests
- [ ] Key API endpoints:
  - `GET /inApps/v1/transactions/{transactionId}` — Get transaction info
  - `GET /inApps/v1/history/{transactionId}` — Get transaction history
  - `GET /inApps/v1/subscriptions/{transactionId}` — Get subscription status
  - `PUT /inApps/v2/refund/lookup/{transactionId}` — Look up refund
- [ ] Transactions are returned in **JWS (JSON Web Signature)** format for added security
- [ ] Verify the JWS signature using Apple's public certificates

### Sandbox Testing

- [ ] **Create Sandbox Tester Accounts:**
  - Navigate to **App Store Connect > Users and Access > Sandbox** (under the Testing section)
  - Click **(+)** to create a new Sandbox Apple Account
  - Up to **10,000 sandbox accounts** can be created
  - Use unique email addresses (not associated with real Apple Accounts)
  - These accounts are only for testing — cannot be used on the real App Store
- [ ] **Configure Sandbox on Device:**
  - On iOS: **Settings > App Store > Sandbox Account** (or Settings > Developer on older iOS)
  - Sign in with your sandbox tester credentials
- [ ] **Testing Features:**
  - Test purchases without real charges
  - Test subscription renewals at accelerated rates:
    | Real Duration | Sandbox Duration |
    |---|---|
    | 1 week | 3 minutes |
    | 1 month | 5 minutes |
    | 2 months | 10 minutes |
    | 3 months | 15 minutes |
    | 6 months | 30 minutes |
    | 1 year | 1 hour |
  - Test payment failures, refunds, and Family Sharing
  - Sandbox subscriptions auto-renew up to **12 times** (6 for annual) then expire

### StoreKit Testing in Xcode (Local)

- [ ] **Create a StoreKit Configuration File:**
  - Xcode > **File > New > File > StoreKit Configuration File**
  - Define products locally (no App Store Connect connection needed)
  - Or sync from App Store Connect configuration
- [ ] **Enable StoreKit Testing:**
  - Edit your **Run Scheme** > **Options** > **StoreKit Configuration** > Select your `.storekit` file
- [ ] **StoreKit Transaction Manager:**
  - View and manage test transactions in Xcode's debug bar
  - Simulate refunds, subscription renewals, billing issues
  - Available when running in Xcode with a StoreKit configuration

---

## 11. Subscriptions — Full Setup

> **Console:** App Store Connect > [App] > **Monetization** > **Subscriptions**

### Subscription Groups

- [ ] Navigate to **Monetization > Subscriptions**
- [ ] Click **(+)** to create a **Subscription Group**
- [ ] Enter a **Reference Name** for the group (internal use only)
- [ ] Click **Create**

**Key Rules:**
- Users can subscribe to **only one product per group** at a time
- Users can subscribe to products in **multiple groups** simultaneously (billed separately)
- Each group can contain up to **100 subscription products**
- Users are eligible for **one introductory offer per subscription group**
- Most apps should use a **single subscription group** unless the business model requires separate billing streams

### Creating Subscription Products

- [ ] Navigate to the subscription group > Click **Create** (or **+**)
- [ ] Enter:
  - [ ] **Reference Name:** Internal identifier
  - [ ] **Product ID:** Unique identifier for code (e.g., `com.company.app.premium.monthly`)
    - Cannot be reused even if deleted
- [ ] Click **Create**, then configure:
  - [ ] **Subscription Duration:** Select from:
    - 1 Week
    - 1 Month
    - 2 Months
    - 3 Months
    - 6 Months
    - 1 Year
  - [ ] **Subscription Prices:**
    - Set a base price from Apple's price points
    - Apple generates equalized prices for 175+ countries/regions
    - Manually adjust individual storefront prices if needed
  - [ ] **Localizations:** Add display name and description for each supported language
  - [ ] **Review Information:** Screenshot and review notes (similar to IAP)
  - [ ] **Family Sharing:** Enable/disable for this subscription
  - [ ] **Tax Category:** Set appropriate tax category if needed

### Subscription Levels/Tiers

- [ ] Navigate to the subscription group
- [ ] Click **Edit Order** to arrange subscription products by level
- [ ] **Drag products** using the reorder control to set hierarchy:
  - **Level 1** (top) = Highest tier / most expensive (e.g., Premium)
  - **Level 2** = Mid tier (e.g., Standard)
  - **Level 3** (bottom) = Lowest tier (e.g., Basic)
- [ ] Click **Save**

**Upgrade/Downgrade Behavior:**
- **Upgrade** (lower level to higher level): Takes effect **immediately**; customer receives prorated credit
- **Downgrade** (higher level to lower level): Takes effect at the **end of current billing period**
- **Crossgrade** (same level, different duration): Behavior depends on duration and pricing

### Revenue Share

| Scenario | Developer Share | Apple Commission |
|---|---|---|
| Year 1 of subscription | 70% | 30% |
| Year 2+ (same subscriber, same group) | 85% | 15% |
| Small Business Program (under $1M/year) | 85% from day 1 | 15% |

### Introductory Offers

> **Console:** [Subscription Product] > **Subscription Prices** > **View all Subscription Pricing** > **Set up Introductory Offer**

**Three Offer Types:**

| Type | How It Works |
|---|---|
| **Free Trial** | No charge during trial period; auto-renews to standard price |
| **Pay Up Front** | Customer pays full discounted amount upfront for the offer period |
| **Pay As You Go** | Customer pays discounted recurring price for each billing period during the offer |

**Setup Steps:**
- [ ] Select the subscription product > Subscription Prices > **View all Subscription Pricing**
- [ ] Click **Set up Introductory Offer**
- [ ] Select **countries/regions** for the offer > Click **Next**
- [ ] Set **start and end dates** > Click **Next**
- [ ] Select **offer type** (Free, Pay Up Front, Pay As You Go)
- [ ] Select **duration** for the offer
- [ ] Set **price** (if not free) — Apple generates prices for all storefronts
- [ ] Review and click **Confirm**

**Available Durations (Free Trial):** 3 days, 1 week, 2 weeks, 1 month, 2 months, 3 months, 6 months, 1 year

**Eligibility Rules:**
- [ ] One introductory offer **per subscription product** in App Store Connect
- [ ] Each customer eligible for **only ONE introductory offer per subscription group**
- [ ] Use receipt validation to check eligibility before displaying offers in-app
- [ ] Cannot edit an offer after creation — must delete and recreate

### Promotional Offers

> **Console:** [Subscription Product] > **Subscription Prices** > **(+)** > **Create Promotional Offer**

**Purpose:** Win back lapsed subscribers, promote upgrades, reward loyalty

**Requirements:**
- [ ] Supported on iOS 12.2+, macOS 10.14.4+, tvOS 12.2+
- [ ] Up to **10 active promotional offers per subscription**
- [ ] Generate **In-App Purchase keys** before creating offers:
  - Navigate to **App Store Connect > Users and Access > Integrations > In-App Purchase**
  - Generate a subscription key for signing promotional offer requests

**Setup Steps:**
- [ ] Navigate to subscription product > Subscription Prices > **(+)** > **Create Promotional Offer**
- [ ] Enter:
  - [ ] **Promotional Offer Reference Name** (internal)
  - [ ] **Promotional Offer Identifier** (used in code)
- [ ] Select offer type: **Pay As You Go**, **Pay Up Front**, or **Free**
- [ ] Choose **duration and price**
- [ ] Apple generates prices for all storefronts
- [ ] Confirm the promotional offer

**Editable After Creation:** Only the **price** can be changed. Duration, type, and identifier cannot.

**Target Audiences:** Current subscribers, expired subscribers, or both (you control targeting in code)

### Offer Codes

> **Console:** [Subscription Product] > **Subscription Prices** > **View all Subscription Pricing** > **Offer Codes** tab

**Overview:**
- Alphanumeric codes redeemable on the App Store or within your app (iOS 14+)
- Max **1 million redemptions per app per quarter**
- One redemption per customer per offer

**Two Types:**

| Feature | One-Time-Use Codes | Custom Codes |
|---|---|---|
| Code format | Unique auto-generated | Named (e.g., "SPRINGPROMO") |
| Batch size | 500–25,000 per batch | 1 at a time, up to 25,000 redemptions |
| Max length | Auto-generated | Up to 64 characters, no special characters |
| Expiration | Max 6 months from creation | Max 6 months, or "No End Date" |
| Distribution | Email, events, physical cards | Large campaigns, public distribution |
| Redemption | URL, App Store, in-app | URL, in-app |

**Setup Steps:**
- [ ] Navigate to subscription > Subscription Prices > **(+)** > **Create Offer Codes**
- [ ] Enter **Reference Name**
- [ ] Configure auto-renewal behavior:
  - Check box = No auto-renewal (commitment-free trial); only "Free" offers available
  - Uncheck = Auto-renews to standard price after offer period
- [ ] Select **Customer Eligibility:**
  - [ ] New subscribers (never subscribed in the group)
  - [ ] Existing subscribers (currently subscribed)
  - [ ] Expired subscribers (previously subscribed, now expired)
- [ ] Set **introductory offer compatibility** (whether code users can also use introductory offers)
- [ ] Select countries/regions
- [ ] Choose pricing: Pay As You Go, Pay Up Front, or Free
- [ ] Set duration and price
- [ ] Confirm the offer
- [ ] After offer creation, generate codes:
  - **One-Time-Use:** Click **Create One-Time Use Codes** > Set quantity (500–25,000) > Set expiration (max 6 months) > Create > Download CSV
  - **Custom:** Click **Create Custom Codes** > Enter code name > Set redemption limit (up to 25,000) > Set expiration > Create
- [ ] Codes become redeemable within **1 hour** of creation
- [ ] Codes expire at **12:00 a.m. PT** on the expiration date

> **Note (March 2026):** Starting **March 26, 2026**, you will no longer be able to create promo codes for In-App Purchases in App Store Connect. Offer codes for subscriptions remain available.

### Grace Period (Billing Grace Period)

> **Console:** App Store Connect > [App] > **Monetization** > **Subscriptions** > **Billing Grace Period** section

- [ ] Click **Set Up Billing Grace Period**
- [ ] Select duration:

| Subscription Type | 3 Days | 16 Days | 28 Days |
|---|---|---|---|
| Weekly | 3 days | 6 days (capped) | 6 days (capped) |
| Monthly | 3 days | 16 days | 28 days |
| Yearly | 3 days | 16 days | 28 days |

- [ ] Select **renewal types** eligible for grace period:
  - **All Renewals** — includes free intro/promo offers transitioning to paid
  - **Only Paid to Paid Renewals** — excludes subscriptions in free periods
- [ ] Select **environment:** Sandbox only (for testing) or Production and Sandbox
- [ ] Test in sandbox first, then enable for production
- [ ] Implement in your app:
  - [ ] Detect when a subscriber enters grace period (check renewal state via StoreKit)
  - [ ] Continue providing full service during grace period
  - [ ] Handle recovery (no interruption if payment recovered within grace period)
- [ ] Changes take up to **24 hours** to take effect
- [ ] Applies to **all auto-renewable subscriptions** in the app (not individual products)

### Subscription Price Changes

> **Console:** [Subscription Product] > **Subscription Prices** > **View all Subscription Pricing**

**Price Increases:**
- [ ] Schedule a price increase with an effective date
- [ ] Apple handles subscriber notification:
  - **Notice-only increases** (small increases meeting Apple's criteria): Subscriber is notified 27 days before renewal; subscription renews at new price automatically
  - **Consent-required increases** (larger increases): Subscriber must explicitly consent; if not consented before the first renewal at the higher price, the subscription expires
- [ ] Subscribers on introductory/promotional offers renew for **at least one more billing period** at the original offer price before the increase takes effect
- [ ] Apple auto-generates comparable prices for all storefronts

**Price Decreases:**
- [ ] Price decreases take effect for all subscribers at the next renewal
- [ ] No consent required from subscribers

### App Store Server Notifications V2

> **Console:** App Store Connect > [App] > **General** > **App Information** > **App Store Server Notifications**
> Or: App Store Connect > [App] > **Distribution** > **General** > **App Store Server Notifications**

**Setup:**
- [ ] Enter your **Production Server URL** (HTTPS endpoint on your server)
- [ ] Enter your **Sandbox Server URL** (HTTPS endpoint for sandbox testing)
- [ ] Select **Version 2** (V1 is deprecated and may be removed at any time)
- [ ] Your server must handle signed JWS payloads from Apple

**V2 Notification Types:**

| Notification Type | Description |
|---|---|
| `SUBSCRIBED` | Customer subscribed (subtypes: `INITIAL_BUY`, `RESUBSCRIBE`) |
| `DID_RENEW` | Subscription successfully renewed (subtype: `BILLING_RECOVERY`) |
| `DID_FAIL_TO_RENEW` | Renewal failed (subtype: `GRACE_PERIOD`) |
| `DID_CHANGE_RENEWAL_STATUS` | Auto-renew preference changed (subtypes: `AUTO_RENEW_ENABLED`, `AUTO_RENEW_DISABLED`) |
| `DID_CHANGE_RENEWAL_PREF` | Subscriber changed subscription product (subtypes: `UPGRADE`, `DOWNGRADE`) |
| `EXPIRED` | Subscription expired (subtypes: `VOLUNTARY`, `BILLING_RETRY`, `PRICE_INCREASE`, `PRODUCT_NOT_FOR_SALE`) |
| `GRACE_PERIOD_EXPIRED` | Billing grace period ended without recovery |
| `OFFER_REDEEMED` | Customer redeemed a promotional offer or offer code |
| `PRICE_INCREASE` | Price increase requires consent (subtypes: `PENDING`, `ACCEPTED`) |
| `REFUND` | Apple refunded a transaction |
| `REFUND_DECLINED` | Apple declined a refund request |
| `REFUND_REVERSED` | A previously granted refund was reversed |
| `CONSUMPTION_REQUEST` | Apple requests consumption data before processing a refund |
| `RENEWAL_EXTENDED` | Subscription renewal date extended |
| `REVOKE` | Family Sharing access was revoked |
| `ONE_TIME_CHARGE` | One-time purchase of consumable, non-consumable, or non-renewing subscription |
| `EXTERNAL_PURCHASE_TOKEN` | Unreported external purchase token detected |
| `TEST` | Test notification (triggered via API) |

- [ ] Implement server-side handlers for each relevant notification type
- [ ] Respond to Apple's server with **HTTP 200** to acknowledge receipt
- [ ] If your server returns a non-200 response, Apple retries the notification

---

## 12. Agreements, Tax, and Banking

> **Console:** App Store Connect > **Business** (or **Agreements, Tax, and Banking** in older UI)

### Paid Apps Agreement

- [ ] Navigate to **App Store Connect > Business > Agreements**
- [ ] Locate the **Paid Apps** agreement row
- [ ] Click **View and Agree to Terms**
- [ ] Read the agreement thoroughly
- [ ] Accept the terms and click **Submit**
- [ ] The **Free Apps** agreement is automatically active upon enrollment
- [ ] The **Paid Apps** agreement is **required** to:
  - Sell paid apps
  - Offer In-App Purchases (consumable, non-consumable, subscriptions)
  - Receive any revenue from Apple

### Bank Account Information

- [ ] Navigate to **Business > Banking**
- [ ] Click **Add Bank Account**
- [ ] Select your **bank country**
- [ ] Enter banking details:
  - [ ] **Bank Name**
  - [ ] **Account Holder Name** (must match your legal entity name)
  - [ ] **Bank Account Number** (IBAN for many countries)
  - [ ] **Routing Number** (SWIFT/BIC for international)
    - Must be your bank's direct routing number (not an intermediary or correspondent bank)
  - [ ] **Account Type:** Checking or Savings
  - [ ] **Currency:** The currency in which you want to receive payments
- [ ] Apple pays developers **within 45 days** of the end of each fiscal month
- [ ] Minimum payout threshold varies by region (typically around $10 USD equivalent)

### Tax Forms

- [ ] Navigate to **Business > Tax**
- [ ] Required tax forms depend on your **country and entity type**
- [ ] **For US-based entities:**
  - [ ] Complete **W-9** form (submitted electronically)
- [ ] **For non-US entities:**
  - [ ] Complete **W-8BEN** (individuals) or **W-8BEN-E** (entities/companies)
  - [ ] May need a **US Tax ID (EIN/ITIN)** to claim tax treaty benefits and reduce withholding
- [ ] **Additional tax forms** may be required for specific countries (Australia, Canada, Japan, etc.)
- [ ] Tax forms can be submitted **electronically** in App Store Connect
- [ ] Forms must be renewed/updated periodically (typically every 3 years for W-8 forms)

### Agreement Status

- [ ] Check agreement status regularly: **App Store Connect > Business > Agreements**
- [ ] Statuses:
  - **Active:** Agreement is in effect
  - **New Terms Available:** Updated agreement requires acceptance
  - **Expired:** Agreement needs renewal
- [ ] If the Paid Apps agreement expires, your paid apps and IAPs **will be removed from sale** until renewed

---

## 13. App Signing

> **Console:** [developer.apple.com/account/resources/certificates](https://developer.apple.com/account/resources/certificates) | Xcode > Signing & Capabilities

### Certificates

**Development Certificate:**
- [ ] Used for running apps on physical devices during development
- [ ] Generated automatically by Xcode (if using automatic signing) or manually:
  - Open **Keychain Access** > Certificate Assistant > Request a Certificate from a Certificate Authority
  - Upload the CSR to [developer.apple.com/account/resources/certificates](https://developer.apple.com/account/resources/certificates)
  - Download and install the certificate

**Distribution Certificate:**
- [ ] Used for App Store, Ad Hoc, and Enterprise distribution
- [ ] Limit: **3 distribution certificates** per account
- [ ] Generate at [developer.apple.com/account/resources/certificates](https://developer.apple.com/account/resources/certificates)
  - Select **Apple Distribution** certificate type
  - Upload CSR > Download > Double-click to install in Keychain

### Provisioning Profiles

**Development Provisioning Profile:**
- [ ] Links your development certificate, app ID, and registered devices
- [ ] Created automatically by Xcode with automatic signing, or manually at the Developer portal

**Distribution Provisioning Profile (App Store):**
- [ ] Links your distribution certificate and App ID
- [ ] Does NOT include specific device UUIDs (App Store distribution is not device-limited)
- [ ] Create at **Developer Portal > Profiles > (+) > App Store** distribution type
- [ ] Select the App ID and distribution certificate
- [ ] Download and install the profile

### Automatic Signing (Recommended)

- [ ] In Xcode, select your target > **Signing & Capabilities**
- [ ] Check **"Automatically manage signing"**
- [ ] Select your **Team** from the dropdown
- [ ] Xcode will:
  - Automatically create and manage development certificates
  - Automatically create and manage provisioning profiles
  - Automatically register devices
  - Manage distribution signing when uploading to App Store Connect
- [ ] **When uploading:** Select "Automatically manage signing" in the distribution dialog
- [ ] Xcode-managed profiles do **not** appear in the Developer portal (managed locally by Xcode)

### Manual Signing (Advanced)

- [ ] Create certificates manually at the Developer portal
- [ ] Create provisioning profiles manually at the Developer portal
- [ ] In Xcode, uncheck "Automatically manage signing"
- [ ] Select the specific **Provisioning Profile** and **Signing Certificate** for each build configuration (Debug/Release)
- [ ] Useful for CI/CD pipelines, large teams, and complex signing requirements

### Keychain Requirements

- [ ] The **private key** for your signing certificate must be in your Mac's Keychain
- [ ] If you set up signing on a new Mac, export the `.p12` file from the original Mac's Keychain and import it
- [ ] For teams: Share signing certificates securely (Apple recommends Xcode-managed automatic signing for simplicity)

---

## 14. App Review Guidelines — Key Requirements

> **Reference:** [developer.apple.com/app-store/review/guidelines](https://developer.apple.com/app-store/review/guidelines/)

### 1. Safety

- [ ] No objectionable content (pornography, hate speech, violence against specific groups)
- [ ] User-generated content apps must include:
  - [ ] Content filtering mechanism
  - [ ] Mechanism to report offensive content
  - [ ] Ability to block abusive users
  - [ ] Published developer contact info for support
- [ ] No physical harm encouragement or facilitation

### 2. Performance

- [ ] App must be **complete and fully functional** — no betas, demos, trial versions, or "coming soon" features
- [ ] App must **not crash** — test thoroughly on all supported devices and OS versions
- [ ] App must work on current and previous iOS version
- [ ] App must not impose **excessive battery, memory, or storage drain**
- [ ] Include valid **URLs** for support and privacy policy (no placeholder URLs)

### 3. Business

- [ ] **In-App Purchases must use Apple's IAP system** — no directing users to external purchase mechanisms for digital content
  - Physical goods and services (Uber, DoorDash) are exempt
  - "Reader" apps (Netflix, Spotify) have some linking entitlement exceptions
- [ ] All IAP prices must be **clearly disclosed before purchase**
- [ ] Must include a **Restore Purchases** button that works without contacting support
- [ ] Subscriptions must clearly describe:
  - What the user gets
  - The price and billing frequency
  - Whether a free trial auto-converts to a paid subscription
  - How to cancel
- [ ] No bait-and-switch pricing or deceptive subscription practices
- [ ] Apps with auto-renewable subscriptions may offer **free trials** but must convert to paid clearly

### 4. Design

- [ ] Provide sufficient **app functionality** — apps that are just a website wrapper or marketing material will be rejected
- [ ] Use standard **iOS UI patterns** appropriately (navigation, gestures, buttons)
- [ ] No **hidden or undocumented features**
- [ ] iPhone apps should run on **iPad** (using compatibility mode at minimum)
- [ ] Support the correct **device orientations** for your app type
- [ ] Include appropriate **app icons** for all required sizes
  - App icon must be **1024 x 1024 pixels** (single icon; Xcode generates all sizes)

### 5. Legal

- [ ] Comply with all local laws in every territory where the app is available
- [ ] Privacy policy is **required**
- [ ] Respect intellectual property rights (no unauthorized use of trademarks, copyrighted content)
- [ ] If using **HealthKit, HomeKit, CareKit**, or similar frameworks, comply with their specific guidelines
- [ ] If collecting data from children (Kids category), comply with **COPPA** and equivalent regulations

### AI-Specific Guidelines (2025+)

- [ ] If your app uses **external AI services**, include a consent modal specifying:
  - The AI service provider
  - The data types being shared
  - Obtain explicit user consent before sharing personal data
- [ ] AI-generated content must be **clearly labeled** if it could be mistaken for human-generated content
- [ ] AI chatbot features impact **age rating** — answer questionnaire accurately

### Common Rejection Reasons

| Reason | Guideline | How to Avoid |
|---|---|---|
| Crashes or bugs | 2.1 | Thorough QA on all devices |
| Broken links or placeholder content | 2.1 | Ensure all URLs and content work |
| Misleading metadata | 2.3 | Accurate name, screenshots, description |
| Incomplete information | 2.1 | Fill in all required fields |
| Missing IAP restore button | 3.1.1 | Always include "Restore Purchases" |
| Deceptive subscriptions | 3.1.2 | Clear pricing before paywall |
| Insufficient app functionality | 4.2 | App must provide meaningful value |
| Privacy violations | 5.1 | Accurate privacy declarations |
| Intellectual property infringement | 5.2 | Do not use others' brands/content |

---

## 15. Submission and Release

> **Console:** App Store Connect > [App] > **App Store** tab > [Version]

### Pre-Submission Checklist

- [ ] All required metadata is filled in (name, description, keywords, screenshots, etc.)
- [ ] Privacy policy URL is active and accessible
- [ ] App privacy labels/nutrition labels are complete
- [ ] Age rating questionnaire is complete
- [ ] Pricing and availability are configured
- [ ] A processed build is selected for the version
- [ ] App review information (contact, demo account) is complete
- [ ] All In-App Purchases and subscriptions are in "Ready to Submit" status

### Submit for Review

- [ ] Navigate to the app version page
- [ ] Verify all sections show **green checkmarks** (no missing information)
- [ ] Click **"Add for Review"** (formerly "Submit for Review")
- [ ] Confirm submission in the dialog

### Release Options

Choose one before submitting:

| Option | Behavior |
|---|---|
| **Manually release this version** | After approval, the app stays in "Pending Developer Release" until you manually click "Release This Version" |
| **Automatically release this version** | After approval, the app goes live on the App Store immediately |
| **Automatically release this version after a date** | If approved before the specified date, the app is held and released on that date. If approved after, it goes live immediately |

### Review Timeline

- [ ] Average review time: **24–48 hours** (Apple states "most reviews within 24 hours")
- [ ] Can take longer during peak periods (holidays, major iOS releases)
- [ ] Check status in App Store Connect:
  - **Waiting for Review** — In the review queue
  - **In Review** — Currently being reviewed
  - **Pending Developer Release** — Approved, awaiting manual release
  - **Ready for Sale** — Live on the App Store
  - **Rejected** — Review failed; see resolution center for details

### Handling Rejection

- [ ] Check the **Resolution Center** in App Store Connect for rejection details
- [ ] Apple provides the specific guideline(s) violated
- [ ] You can:
  - [ ] **Reply** in the Resolution Center to ask for clarification or appeal
  - [ ] **Make changes** and resubmit
  - [ ] **Appeal** to the App Review Board if you believe the rejection is incorrect
- [ ] After fixing issues, resubmit the same version (update metadata/build as needed)

### Phased Release (Gradual Rollout)

> Applies to **version updates** (not initial release)

- [ ] Select **"Release update over a 7-day period using phased release"** in the Phased Release section
- [ ] Rollout schedule (percentage of users with automatic updates enabled):

| Day | Percentage |
|---|---|
| Day 1 | 1% |
| Day 2 | 2% |
| Day 3 | 5% |
| Day 4 | 10% |
| Day 5 | 20% |
| Day 6 | 50% |
| Day 7 | 100% |

- [ ] Users who manually update or download fresh always get the latest version
- [ ] You can **pause** the phased release at any time (for up to **30 total days**)
- [ ] You can **resume** a paused phased release
- [ ] You can **release to all users** immediately at any point during phased release
- [ ] If a critical issue is found, pause the release and submit an urgent fix

---

## 16. Recent Changes and Requirements (2025–2026)

### SDK Minimum Requirements (April 2026)

- [ ] Starting **April 28, 2026**, all apps uploaded to App Store Connect must be built with:
  - **Xcode 26** or later
  - **iOS/iPadOS 26 SDK** or later
  - **tvOS 26 SDK** or later
  - **watchOS 26 SDK** or later
  - **visionOS 26 SDK** or later
- [ ] Current requirement (2025): Xcode 16, iOS 18 SDK

### Updated Age Ratings (July 2025)

- [ ] New ratings introduced: **13+, 16+, 18+** (replacing old 12+ and 17+)
- [ ] Updated age rating questionnaire includes new categories for:
  - In-app controls (AI/chatbot interactions)
  - Capabilities (location sharing, account creation)
- [ ] **Deadline:** Complete updated age rating questionnaire by **January 31, 2026**

### Privacy Manifest Requirements (Since May 2024)

- [ ] All apps must include **`PrivacyInfo.xcprivacy`** privacy manifest files
- [ ] Required Reason APIs must be declared with legitimate reasons
- [ ] Third-party SDKs that are on Apple's required list must include their own signed privacy manifests
- [ ] SDK signatures required for commonly used third-party frameworks

### Promo Code Changes (March 2026)

- [ ] Starting **March 26, 2026**, you can **no longer create promo codes for In-App Purchases** in App Store Connect
- [ ] **Offer codes** for auto-renewable subscriptions remain available and unaffected

### Account Deletion Requirement (Ongoing)

- [ ] All apps that support account creation **must** provide in-app account deletion functionality
- [ ] Must delete all user data or clearly explain what is retained and why

### App Store Server Notifications V1 Deprecation

- [ ] V1 notifications are **deprecated** — migrate to **V2** as soon as possible
- [ ] Apple may remove V1 support at any time without further notice

### Alternative Payment Mechanisms

- [ ] In the EU (under the Digital Markets Act), Apple now allows alternative payment processing for certain apps
- [ ] Must apply for the **StoreKit External Purchase Link entitlement** (EU only as of 2025)
- [ ] Apps using external links must still comply with Apple's guidelines and pay a reduced commission
- [ ] "Reader" apps globally may include a **single link** to their website for account management

### Notarization and Integrity

- [ ] Apple continues to strengthen **app supply chain integrity** requirements
- [ ] Third-party SDK developers must provide signed binaries
- [ ] Regular code signing certificate rotation is recommended for security

---

## Quick Reference: Console Navigation Paths

| Task | Navigation Path |
|---|---|
| Create new app | App Store Connect > My Apps > (+) > New App |
| Register Bundle ID | developer.apple.com/account/resources/identifiers > (+) |
| Upload build | Xcode > Product > Archive > Distribute App > App Store Connect |
| TestFlight (internal) | App Store Connect > [App] > TestFlight > Internal Testing |
| TestFlight (external) | App Store Connect > [App] > TestFlight > External Testing |
| Create IAP | App Store Connect > [App] > Monetization > In-App Purchases > (+) |
| Create subscription group | App Store Connect > [App] > Monetization > Subscriptions > (+) |
| Introductory offers | [Subscription] > Subscription Prices > View All > Set up Introductory Offer |
| Promotional offers | [Subscription] > Subscription Prices > (+) > Create Promotional Offer |
| Offer codes | [Subscription] > Subscription Prices > View All > Offer Codes tab |
| Grace period | App Store Connect > [App] > Monetization > Subscriptions > Billing Grace Period |
| Server notifications URL | App Store Connect > [App] > General > App Information > App Store Server Notifications |
| Agreements | App Store Connect > Business > Agreements |
| Bank account | App Store Connect > Business > Banking |
| Tax forms | App Store Connect > Business > Tax |
| Privacy labels | App Store Connect > [App] > General > App Privacy |
| Age rating | App Store Connect > [App] > General > App Information > Age Rating |
| Pricing | App Store Connect > [App] > General > Pricing and Availability |
| Sandbox testers | App Store Connect > Users and Access > Sandbox |
| Certificates | developer.apple.com/account/resources/certificates |
| Provisioning profiles | developer.apple.com/account/resources/profiles |
| App review status | App Store Connect > [App] > App Store > [Version] |
| Resolution center | App Store Connect > [App] > Resolution Center |
| Generate IAP keys | App Store Connect > Users and Access > Integrations > In-App Purchase |
| Submit for review | App Store Connect > [App] > App Store > [Version] > Add for Review |

---

## Summary: End-to-End Submission Flow

1. **Enroll** in the Apple Developer Program ($99/year)
2. **Register** a Bundle ID at the Developer portal
3. **Create** the app record in App Store Connect
4. **Configure** app metadata (name, description, keywords, screenshots, etc.)
5. **Set** categories, age rating, content rights
6. **Configure** pricing and country availability
7. **Complete** privacy labels and provide privacy policy URL
8. **Sign** the Paid Apps Agreement and set up banking/tax (if selling)
9. **Create** IAPs and/or subscriptions in App Store Connect (if applicable)
10. **Build and archive** in Xcode with proper signing
11. **Upload** the build to App Store Connect
12. **Test** via TestFlight (internal and/or external)
13. **Select** the build for the App Store version
14. **Fill in** App Review information (contact, demo account, notes)
15. **Choose** release option (manual, automatic, or scheduled)
16. **Submit** for App Review
17. **Respond** to any rejection feedback in the Resolution Center
18. **Release** (manually if chosen, or automatically upon approval)
19. **Monitor** with phased release if desired

---

> **Sources:** Apple Developer Documentation ([developer.apple.com](https://developer.apple.com)), App Store Connect Help ([developer.apple.com/help/app-store-connect](https://developer.apple.com/help/app-store-connect)), App Store Review Guidelines ([developer.apple.com/app-store/review/guidelines](https://developer.apple.com/app-store/review/guidelines))
