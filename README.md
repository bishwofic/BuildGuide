<div align ="center">
<img src="https://raw.githubusercontent.com/bishwofic/BuildGuide/main/res/Android.png" width="250"/>
<h3> Custom ROM Build Guide !! </h3>
<b> A Beginner's Guide on How to Compile a Custom ROM.</b>
</div>
<br>

### Step 1: Initiate Directory:

```bash
mkdir romname
```
```bash
cd romname
```
```bash
git config --global user.email "yourname@mail.com" && git config --global user.name "yourname" 
```

### <br>Step 2: Cloning ROM Source:

```bash
repo init -u https://github.com/romname/android_manifest.git -b branches
```
```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```
Refer to your ROM's Manifest for detailed clone guide.

### <br>Step 3: Cloning Trees:
I have opted for begonia so clone your DT's according to the device you are going to build for.
<br>Check your device on your ROM's Official Devices Repo to figure out all the trees required for it.

<b><i><br>Cloning Device Tree:</i></b>
```bash
git clone https://github.com/username/device_redmi_begonia -b 13.0 device/redmi/begonia
```

<b><i><br>Cloning Kernel Tree:</i></b>
```bash
git clone https://github.com/username/kernel_xiaomi_mt6785 -b 13.0 kernel/xiaomi/mt6785
```

<b><i><br>Cloning Vendor Tree:</i></b>
```bash
git clone https://github.com/username/vendor_redmi_begonia -b 13.0 vendor/redmi/begonia
```
```bash
git clone https://github.com/username/vendor_redmi_begonia-ims -b 13.0 vendor/redmi/begonia-ims
```
```bash
git clone https://github.com/username/vendor_redmi_begonia-firmware -b 13.0 vendor/redmi/begonia-firmware
```

<b><br>Cloning Sepolicy Tree:</b>
```bash
git clone https://github.com/username/device_mediatek_sepolicy -b 13.0 device/mediatek/sepolicy
```
</i>

### <br>Step 4: Editing Device Tree:
```bash
cd device/devicename/codename
```
Rename the ```aosp.dependencies``` & ```aosp_devicename.mk``` to your current ROM.<br>
Edit ```AndroidProducts.mk```. Rename the pre-existing ```aosp``` to your current ROM.<br>
Edit ```aosp_devicename.mk```. Adapt the flags according to your ROM. Check Devices Repo for more information on flags.<br>
</i>

### <br>Step 5: Compiling the ROM:
<b><i>Setup Build Environment:</i></b>
```bash
. build/envsetup.sh
```

<b><i>Setup Lunch:</i></b>
```bash
lunch romname_devicename-userdebug
```

<b><i>Compile:</i></b>
```bash
mka bacon -j$(nproc --all)
```
Refer to your ROM's Manifest for Compile Flags.
</i>

### <br>Fixing Errors:
Fixing errors that arise during a ROM Development is a whole another branch of headache. Your build might get an error. It might not get an error. Each build might get an different error. 
It takes a lot of research and understanding to figure  out the solutions.
Wishing you Best of Luck !!

### <br>Reach out to me in case of issues. [bishwofic](https://t.me/bishwofic) !!