# Lemuroid — Upstream Master Builds

[![Build Latest Upstream APK](https://github.com/WuLinLee/Lemuroid/actions/workflows/build-official-master-keep-latest.yml/badge.svg)](https://github.com/WuLinLee/Lemuroid/actions/workflows/build-official-master-keep-latest.yml)
[![Latest Release](https://img.shields.io/github/v/release/WuLinLee/Lemuroid?label=latest%20APK)](https://github.com/WuLinLee/Lemuroid/releases/latest)

Unofficial, automatically built Android APKs from the latest `master` branch of the upstream [Swordfish90/Lemuroid](https://github.com/Swordfish90/Lemuroid) project.

**The purpose of this repository is simple: build the current upstream version once a week and publish the APK as the latest GitHub Release.** No local Android build environment is required.

## Download

- **[Download the latest APK](https://github.com/WuLinLee/Lemuroid/releases/latest/download/lemuroid-app-free-dynamic-release.apk)**
- [View the latest release and build information](https://github.com/WuLinLee/Lemuroid/releases/latest)
- [Browse all workflow runs](https://github.com/WuLinLee/Lemuroid/actions/workflows/build-official-master-keep-latest.yml)

The latest release includes the APK, a SHA-256 checksum file, and build metadata identifying the exact upstream commit used.

## What gets built

| Item | Configuration |
|---|---|
| Source repository | [Swordfish90/Lemuroid](https://github.com/Swordfish90/Lemuroid) |
| Source branch | `master` |
| Build variant | `Free Dynamic Release` |
| Gradle task | `:lemuroid-app:assembleFreeDynamicRelease` |
| Build environment | GitHub Actions, Ubuntu, JDK 17 |
| Scheduled build | Every Sunday at 03:23 UTC |
| Manual build | **Actions → Build Latest Upstream APK → Run workflow** |
| Release policy | Keep only the newest successful automated build |

Each run checks out the current upstream `master` commit, including its submodules, and builds that exact checkout. The release notes and `BUILD_INFO.txt` record the upstream commit SHA, so the APK can be traced back to its source.

## Important notes

- **Unofficial build:** This is a community automation project, not an official Lemuroid release and not affiliated with the upstream maintainer.
- **Upstream code only:** The APK is built from `Swordfish90/Lemuroid`, not from this fork's application source. Changes made only in `WuLinLee/Lemuroid` are not included in the APK.
- **Development version:** The build follows upstream `master`, not a stable release tag. It may contain unreleased changes or regressions.
- **Signing key:** A temporary signing keystore is generated for each workflow run. Android therefore cannot install a new weekly APK as an in-place update over the previous CI build, and it may also reject an update over a Play Store/F-Droid installation. You may need to uninstall the previous app before installing a new build. **Back up in-app saves and other important data first**, because uninstalling an Android app can remove its local data.
- **Latest means latest successful build:** A scheduled run that fails does not replace the currently published APK. The workflow retries a failed build once and then opens or updates a tracking issue.

## Automation

The workflow runs every Sunday at 03:23 UTC and can also be started manually from the Actions tab. It builds the upstream source, verifies that at least one APK was produced, creates checksum/build-info files, uploads a short-lived Actions artifact, and publishes a GitHub Release.

Only releases created by this automation are cleaned up. After a new release is published successfully, older automated build releases and their tags are removed. The newest successful APK therefore remains available from the stable **Latest Release** download link above.

## Upstream project

- **Source code:** https://github.com/Swordfish90/Lemuroid
- **Upstream releases:** https://github.com/Swordfish90/Lemuroid/releases
- **License:** Lemuroid is licensed under [GNU GPL-3.0](https://github.com/Swordfish90/Lemuroid/blob/master/LICENSE).

This repository provides build automation and convenient APK access; please report application bugs and feature requests to the [upstream project](https://github.com/Swordfish90/Lemuroid/issues).
