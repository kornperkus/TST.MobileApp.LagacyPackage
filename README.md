# Legacy Flutter Patches

This repo keeps older Flutter packages/plugins frozen because the app cannot move to newer Flutter versions yet, so we patch the copied sources ourselves (null-safety gaps, Gradle 8 scripts, AndroidX tweaks, etc.).

1. Copy the exact upstream source into a new root-level folder (`<package-name>/`) and add an `UPSTREAM.md` with the version, source link, and why we froze it.
2. Patch only what is required to keep the app building (nullability tweaks, Gradle scripts, AndroidX moves), record each change in `PATCHES.md`, and run the package tests or a Flutter build with `dependency_overrides` to confirm.

Use the repo from the app like this:

```yaml
dependencies:
  legacy_plugin:
    git:
      url: git@github.com:<org>/TST.MobileApp.LagacyPackage.git
      path: legacy_plugin
      ref: <commit>
    # or: path: ../TST.MobileApp.LagacyPackage/legacy_plugin
```

Keep each folder focused so diffing against upstream stays simple, and drop the local copy once the official package ships a compatible release.
