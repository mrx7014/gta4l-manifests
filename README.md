# Manifest for building CrDroid for gta4llte, gta4lwifi.

`gta4lwifi` is the codename for the WiFi-only variant of the Samsung Galaxy Tab A7 , with model SM-T500.

`gta4llte` is the codename for the LTE variant of the Samsung Galaxy Tab A7, with model SM-T505, and also with SM-T505N.

Some extremely basic instructions:
- Make a new directory for ArrowOS sources and enter it:
```
mkdir crdorid-13.0
cd crdroid-13.0
```

- Initialize repo in this directory with the CrDroid 13.0 android repository:
```
repo init -u https://github.com/crdroidandroid/android.git -b 13.0 --git-lfs
```

- Clone this repository to .repo/local_manifests for roomservice.xml containing the repositories needed to build for these devices:
```
git clone https://github.com/mrx7014/gta4l-manifests.git -b crdroid-13.0 .repo/local_manifests
```

- Sync all of the repositories in manifests (including CrDroid manifests):
```
repo sync  --force-sync --current-branch --no-tags --no-clone-bundle --optimized-fetch --prune -j$(nproc --all)
```

- Finally, build as you like.
```
. build/envsetup.sh
lunch lineage_gta4l-<build_type>
m bacon
```
