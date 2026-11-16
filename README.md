# Amani Speech Verifier SDK for Android

Maven repository of the Amani Speech Verifier SDK for Android (`ai.amani.android:amani-speech-verifier`).

## Installation

Add the Amani Maven repository to `settings.gradle`:

```groovy
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        mavenCentral()
        maven {
            url = "https://jfrog.amani.ai/artifactory/amani-speech-verifier"
        }
    }
}
```

Kotlin DSL (`settings.gradle.kts`):

```kotlin
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        mavenCentral()
        maven {
            url = uri("https://jfrog.amani.ai/artifactory/amani-speech-verifier")
        }
    }
}
```

### Alternative repository (GitHub)

If the SDK cannot be resolved from the repository above, use the Maven repository in this GitHub
repository instead (or in addition):

```groovy
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven {
            url "https://raw.githubusercontent.com/AMANI-AI-ORG/android-speech-verifier-sdk/main/maven"
            content { includeGroup "ai.amani.android" }
        }
    }
}
```

Kotlin DSL (`settings.gradle.kts`):

```kotlin
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven {
            url = uri("https://raw.githubusercontent.com/AMANI-AI-ORG/android-speech-verifier-sdk/main/maven")
            content { includeGroup("ai.amani.android") }
        }
    }
}
```

`includeGroup` makes Gradle look up only Amani artifacts in this repository.

Then add the dependency to your app module's `build.gradle`:

```groovy
dependencies {
    implementation "ai.amani.android:amani-speech-verifier:<version>"
}
```

Kotlin DSL:

```kotlin
dependencies {
    implementation("ai.amani.android:amani-speech-verifier:<version>")
}
```

Available versions are listed in
[maven/ai/amani/android/amani-speech-verifier](maven/ai/amani/android/amani-speech-verifier). Release
notes are on the [Releases](../../releases) page.

## Verifying the SDK

Each version folder in this GitHub repository contains a `SHA256SUMS` file with the SHA-256 of every file of
that version.

**A downloaded AAR**

```bash
shasum -a 256 amani-speech-verifier-<version>.aar
```

The output must match the AAR's line in `SHA256SUMS` for that version. With `SHA256SUMS` in the same
folder:

```bash
shasum -a 256 -c SHA256SUMS --ignore-missing
```

**On every Gradle build** (Gradle dependency verification)

```bash
./gradlew --write-verification-metadata sha256 help
```

This writes `gradle/verification-metadata.xml`. Check that the `amani-speech-verifier` entries match the
published SHA-256, then commit the file. Gradle then stops the build if a downloaded artifact differs.
