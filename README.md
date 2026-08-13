# 📱 Learners' Home — Android Application

**Learners' Home** is an educational Android application built with Kotlin, focusing on efficient asynchronous processing, responsive UI design, and monetization strategy.

---

## 🛠️ Tech Stack & Architecture
* **Language:** Kotlin
* **UI Framework:** Material Design, XML Layouts
* **Asynchronous Processing:** Kotlin Coroutines (Main-thread safety & background dispatchers)
* **Local Persistence:** SharedPreferences & Custom Parcelable data models
* **Monetization:** Google AdMob SDK (Banner & Interstitial Ads)
* **Build System:** Gradle

---

## 🚀 Key Features
* Responsive UI with managed Activity lifecycles.
* Asynchronous data loading off the UI thread to prevent Application Not Responding (ANR) errors.
* Persistent user configurations across app launches using SharedPreferences.
* Optimized memory footprint for intra-app data serialization via `Parcelable`.
