### This is a repository for automatically building GKI kernels

> Non-GKI users can try resources from [SukiSU Cloud Drive](https://alist.shirkneko.top); does **not support OnePlus ColorOS14, 15**  
>
> If this is your first time using it, please **read the following content carefully** — don’t waste others’ time out of laziness!  
>
> Recent updates: 1. OnePlus 8ELITE processor can use 6.6 kernel (untested); 2. Fixed compilation errors for these GKI versions — [5.10.(66, 81, 101), 5.15.(74, 94, 104)]

### Download  
You can [download your resources here](https://github.com/guruji-byte/GKI_KernelSU_SUSFS/releases)  
1. About Anykernel3.zip: download and use!  
   - Then use a flashing tool, e.g. [HorizonKernelFlasher](https://github.com/libxzr/HorizonKernelFlasher/releases) to flash the kernel  
2. About boot.img: download the one matching your kernel format (uncompressed, gz, lz4), [refer here](https://kernelsu.org/guide/installation.html#install-by-kernelsu-boot-image) **to find the suitable boot.img**  
   - Flash using [FASTBOOT](https://magiskcn.com/), or use a flashing tool to flash it to the boot partition of the ROOT slot (e.g. Aiwanji, Kernelflasher)

### Support  
| Feature | Description |
| --- | --- |
| [KernelSU](https://kernelsu.org/zh_CN/) | Includes **Official, MKSU, SUKISU, NEXT** |
| [SUSFS4](https://gitlab.com/simonpunk/susfs4ksu) | Kernel-level patch to assist KSU hiding |
| [BBR](https://blog.thinkin.top/archives/ke-pu-bbrdao-di-shi-shi-me) | TCP congestion control algorithm, makes network faster? |
| [Wireguard](https://zh.wikipedia.org/wiki/WireGuard) | See wiki link on the left |
| [LZ4KD](https://github.com/ShirkNeko/SukiSU_patch/tree/main/other) | Said to be a ZRAM algorithm from HUAWEI source, patch ported by [Yuncai Zhifeng](http://www.coolapk.com/u/24963680) |

<details>  
<summary>Also supports these algorithms, can switch ZRAM in scene</summary>

### LZ4K, LZ4HC, deflate, 842, ~~zstdn~~, lz4k_oplus

</details>

### KSU Manager  
After compilation, you’ll see a file like `Next-Manager(12600)`. Simply put, this is the ***latest manager*** uploaded along with the kernel.  
![Example](./assets/get_manager.gif)  
Similarly, the [Release](https://github.com/zzh20188/GKI_KernelSU_SUSFS/releases) also includes the ***latest manager***!  
![release](./assets/release_manager.gif)

### Emergency Rescue Guide

> [!IMPORTANT]  
> **Trigger Conditions**  
> Perform rescue if your device cannot boot due to:  
> - Flashed wrong/incompatible kernel  
> - Kernel version mismatch (e.g. flashing version 233 kernel on 5.10.66)  
1. Enter FASTBOOT mode  

   - Physical button combo: Power + Volume- or ADB command: `adb reboot bootloader`  

2. Execute flash command  
   ```bash
   $ fastboot flash boot <full boot.img filename>
   ```

### How to obtain stock image  
1. Extract from existing firmware  

   - OTA zip: unzip then use [payload-dumper tool](https://magiskcn.com/payload-dumper-go-boot.html)  
   - Full flash package: unzip directly to get boot.img

2. Get from external resources  

   - Search on community forums: device model + stock boot (e.g. XDA/Coolapk)  
   - [Online extraction on mobile](https://magiskcn.com/payload-dumper-compose.html)

> [!TIP]  
> ### Kernel version compatibility notes  
>
> **1. Cross sub-version flashing rule**  
> When your device’s GKI main version is 5.10.x (e.g. 5.10.168), you can flash a higher sub-version kernel within the same main version (e.g. 5.10.198).  
> For **X-lts** versions, e.g. `android12-5.10.X-lts-AnyKernel3.zip`:  
> - **X-lts** means Long Term Support (highest sub-version, this example is 5.10.236)  
> - LTS version number increases with GKI source updates (other versions like 198 are permanently fixed)  
> - ⚠️ Note: LTS is the latest, **but** latest ≠ most stable (e.g. 6.6.x may have auto-reboot BUG)  
>
> **2. Kernel version spoofing method**  
> Execute in MT Manager terminal:  
> ```bash
> uname -r | sed 's/^[^-]*//'
> ```  
> After getting it, copy directly and fill this version into the Action compile panel to spoof the kernel version.
>
> **3. Compile optimization tips**  
> Edit the [config file](.github/workflows/kernel-a12-5.10.yml) (like kernel-a12-5.10.yml):  
> - ▶️ Delete/comment out GKI versions you don’t need (**speed up compilation**)  
> - ➕ Add specified GKI version (see [custom guide](https://www.coolapk.com/feed/62820671?shareKey=OGMxYmZmNTk0YzIxNjgxNzM1MzI~&shareUid=11253396&shareFrom=com.coolapk.market_15.2.2))  
> - 📅 Kernel build time: refer to the comments **around line 490** in [gki-kernel.yml](.github/workflows/gki-kernel.yml)

### More  
You can share your suggestions... I’ll try my best!"
