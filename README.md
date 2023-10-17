# Manifest for building Lineage OS for gta4llte, gta4lwifi.

`gta4lwifi` is the codename for the WiFi-only variant of the Samsung Galaxy Tab A7 , with model SM-T500.

`gta4llte` is the codename for the LTE variant of the Samsung Galaxy Tab A7, with model SM-T505, and also with SM-T505N.

Some extremely basic instructions:
- Make a new directory for LineageOS sources and enter it:
```
mkdir lineage-20.0
cd lineage-20.0
```

- Initialize repo in this directory with the LineageOS 20.0 android repository:
```
repo init -u https://github.com/LineageOS/android.git -b lineage-20.0 --git-lfs
```

- Clone this repository to .repo/local_manifests for roomservice.xml containing the repositories needed to build for these devices:
```
git clone https://github.com/mrx7014/gta4l-manifests.git -b lineage-20.0 .repo/local_manifests
```

- Sync all of the repositories in manifests (including LineageOS manifests):
```
repo sync
```

- Finally, build as you like.
```
. build/envsetup.sh
lunch lineage_gta4l-<build_type>
mka otapackage
```
