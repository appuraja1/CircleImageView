# CircleImageView

[![Release](https://jitpack.io/v/appuraja1/CircleImageView.svg)](https://jitpack.io/#appuraja1/CircleImageView)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

A fast, lightweight, and crash-free circular ImageView for Android. Designed specifically for profile images, avatars, and modern UI components.

![CircleImageView](screenshot.png)

It uses a `BitmapShader` and **does not**:
* create unnecessary copies of the original bitmap in memory
* use `clipPath` (which is CPU heavy and causes anti-aliasing artifacts)
* use `setXfermode` to clip the bitmap (which requires multiple passes to the canvas)

Key Features
------------
* **Zero Runtime Dependencies:** Extremely lightweight (compiled with pure Android SDK APIs).
* **Safe & Crash-Free:** Built-in safeguards against `VectorDrawable` crashes, 0-dimension draws, and memory exhaustion (`OutOfMemoryError`).
* **Hardware Accelerated:** Native elevation & round shadow support via `ViewOutlineProvider.setOval()`.
* **High Performance:** Optimized Euclidean distance calculation for 60/120 FPS buttery-smooth touch handling in lists.

Installation
------------

### 1. Add the JitPack repository
Add it to your `settings.gradle` (or root `build.gradle`):

```groovy
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.PREFER_PROJECT)
    repositories {
        google()
        mavenCentral()
        maven { url '[https://jitpack.io](https://jitpack.io)' }
    }
}

```

### 2. Add the dependency

Add the dependency to your app's `build.gradle`:

```groovy
dependencies {
    implementation 'com.github.appuraja1:circleimageview:1.0.0'
}

```

## Usage

Add the view to your layout XML:

```xml
<appu.raja.circleimageview.CircleImageView
    xmlns:android="[http://schemas.android.com/apk/res/android](http://schemas.android.com/apk/res/android)"
    xmlns:app="[http://schemas.android.com/apk/res-auto](http://schemas.android.com/apk/res-auto)"
    android:id="@+id/profile_image"
    android:layout_width="96dp"
    android:layout_height="96dp"
    android:src="@drawable/profile"
    app:civ_border_width="2dp"
    app:civ_border_color="#FF000000"
    app:civ_border_overlay="false"
    app:civ_circle_background_color="#FFFFFFFF" />

```

## XML Attributes

| Attribute | Format | Description |
| --- | --- | --- |
| `civ_border_width` | dimension | Width of the outer circular border (Default: `0dp`) |
| `civ_border_color` | color | Color of the border (Default: `#000000`) |
| `civ_border_overlay` | boolean | If `true`, the border is drawn on top of the image (Default: `false`) |
| `civ_circle_background_color` | color | Background fill color behind transparent images |

## Limitations & Best Practices

* **ScaleType:** Always locked to `CENTER_CROP`. Changing scale type is intentionally unsupported.
* **adjustViewBounds:** Not supported due to fixed aspect ratio constraints.
* **Image Loaders (Glide / Coil / Picasso):** Disable fade transitions when loading directly into circular views to prevent graphical glitches during crossfades (e.g., use `dontAnimate()` in Glide).

## Changelog

* **1.0.0**
* Complete modern rewrite for Java 17/21 and Android Gradle Plugin 8+.
* Completely removed `androidx.core` runtime dependency for a feather-light footprint.
* Fixed `VectorDrawable` crash when intrinsic dimensions are missing or non-positive.
* Optimized touch detection by removing CPU-intensive `Math.pow()` calls.
* Upgraded outline provider to `setOval` for pixel-perfect elevation and shadows.



## Contact & Support

* **Maintainer:** Appu Raja
* **GitHub:** [appuraja1](https://github.com/appuraja1?utm_source=bookboard.co)
* **Email:** bookboard.co@gmail.com

## License

```text
Copyright 2026 Appu Raja

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

```


