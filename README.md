# Manifest for building Evolution X for gta4llte, gta4lwifi.

`gta4lwifi` is the codename for the WiFi-only variant of the Samsung Galaxy Tab A7 , with model SM-T500.

`gta4llte` is the codename for the LTE variant of the Samsung Galaxy Tab A7, with model SM-T505, and also with SM-T505N.

Some extremely basic instructions:
- Make a new directory for Evolution X sources and enter it:
```
mkdir evolution_14.0
cd evolution_14.0
```

- Initialize repo in this directory with the Evolution X 14.0 (UDC) android repository:
```
repo init -u https://github.com/Evolution-X/manifest -b udc
```

- Clone this repository to .repo/local_manifests for roomservice.xml containing the repositories needed to build for these devices:
```
git clone https://github.com/mrx7014/gta4l-manifests.git -b evolution_14.0 .repo/local_manifests
```

- Sync all of the repositories in manifests (including Evolution X manifests):
```
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```

- Finally, build as you like.
```
. build/envsetup.sh
lunch evolution_gta4l-userdebug
mka evolution
```
