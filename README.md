# Manifest for building ArrowOS for gta4llte, gta4lwifi.

`gta4lwifi` is the codename for the WiFi-only variant of the Samsung Galaxy Tab A7 , with model SM-T500.

`gtaxllte` is the codename for the LTE variant of the Samsung Galaxy Tab A7, with model SM-T505, and also with SM-T505N.

Some extremely basic instructions:
- Make a new directory for ArrowOS sources and enter it:
```
mkdir ArrowOS-13.1
cd ArrowOS-13.1
```

- Initialize repo in this directory with the CrDroid 12.1 android repository:
```
repo init -u https://github.com/ArrowOS/android_manifest.git -b arrow-13.1
```

- Clone this repository to .repo/local_manifests for roomservice.xml containing the repositories needed to build for these devices:
```
git clone https://github.com/mrx7014/gta4l-manifests.git -b arrow-13.1 .repo/local_manifests
```

- Sync all of the repositories in manifests (including CrDroid manifests):
```
repo sync  --force-sync --current-branch --no-tags --no-clone-bundle --optimized-fetch --prune -j$(nproc --all)
```

- Finally, build as you like.
```
. build/envsetup.sh
lunch arrow_gta4l-<build_type>
mka otapackage
```
