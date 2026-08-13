# 🏛️ Learners' Home — Architecture & Code Highlights

This document provides a technical deep-dive into the core patterns, asynchronous operations, and data models used in **Learners' Home**.

---

### 1. Safe Asynchronous Execution (Kotlin Coroutines)
Demonstrating main-thread safety by executing heavy data operations on `Dispatchers.IO` and UI updates safely on `Dispatchers.Main`:

```kotlin
// Thread-safe background operations used in Learners' Home
private fun loadQuizDataAsync(categoryKey: String) {
    lifecycleScope.launch(Dispatchers.IO) {
        val quizList = preferenceRepository.getQuizByCategory(categoryKey)
        
        withContext(Dispatchers.Main) {
            updateQuizUI(quizList)
        }
    }
}
```

---

### 2. High-Performance Data Serialization (Parcelable Model)
Optimizing intra-app data passing across Activity lifecycles over standard Java serialization:

```kotlin
@Parcelize
data class QuizQuestion(
    val questionId: Int,
    val questionText: String,
    val options: List<String>,
    val correctAnswerIndex: Int
) : Parcelable
```

---

### 3. Monetization Helper (Sanitized AdMob Integration)
Abstracting ad loader logic with explicit key placeholders for security:

```kotlin
object AdManager {
    // Sanitized test/placeholder keys for public preview
    private const val AD_UNIT_ID = "ca-app-pub-3940256099942544/6300978111"

    fun loadBannerAd(context: Context, adView: AdView) {
        val adRequest = AdRequest.Builder().build()
        adView.loadAd(adRequest)
    }
}
```
