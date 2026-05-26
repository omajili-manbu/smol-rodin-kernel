v0.0.1: 
- Initial release (changes to Capybara listed below)

v0.0.2: 
- Merge android15-6.6-lts and android15-6.6 branches' new commits. 
- Update NoMount against latest commit.
- Add missing dir_hash struct nomount_dir_node member (otherwise it fails to build!).
- Fix nomount runtime crash due to mistaken kmem_cache_create on nomount_child triggering a memory bug, and fix two other bugs, these three NoMount changes were diagnosed by Claude Sonnet 4.6 (Adaptive).
- Re-enable AnyKernel generation as requested by Poco X7 Pro community Telegram group.
- Add more compiler optimizations (detailed below)

v0.1.0:
- Embed KernelSU from Tiann (not a submodule cause lazy, don't want to manage a fork and point submodule to it). Rename the dot-git-renamed to get the repo back!!
- A little merge from android15-6.6
- Bump nomount, erasing Claude's fixes which were addressed upstream.
- Update binaries in Anykernel3
- Update KernelSU

v0.2.0:
- Update KernelSU (includes SELinux Hide fix!)
- Update NoMount to 1.0.0
- Reorganize commit history once again
- ZSTD 1.6.0!
- A bit of changes from android15-6.6 branch
- Enable CONFIG_SCHED_CLUSTER and use ZSTD as default ZRAM compression
- Introduction of multiple build types: {
    * efficiency: 300Hz tick rate, workqueue efficiency mode
    * 6.6.56 version
    * 6.6.89 version
    * no root version
    * dimensity 9500S version
}

Changes from Capybara kernel to Smol kernel:
- Use various optimization commits dropped from Capybara 4.0 to 5.0
- KernelSU by tiann, enabled by default, with KowSU manager support
- susfs by simonpunk, enabled by default
- susfs enhanced changes by Enginex0, enabled by default
- vc-teahouse's latest changes to Baseband-guard
- Debranded from 71chjzkc's Capybara by to smol
- Merged android15-6.6 and android15-6.6-lts branches from GoogleSource
- Enabled 600Hz tick rate
- Patched with Reflex CPU governor by firelzrd
- Fixed Reflex compatibility with 6.6 kernel with naive changes helped by Claude AI
- ADIOS I/O scheduler by firelzrd, enabled by default 
- Various defconfig changes for performance
- NoMount VFS redirection driver enabled by default
- Use ZyCromerZ's Clang 23 instead of old Xiaomi toolchain
- Use FullLTO without neutered inlining (edited Makefile to remove "-mllvm -import-instr-limit=5")
- Disabled UBSAN to allow FullLTO to boot
- LLD LTO optimizations
- Aggressive compiler optimizations: -O3, cortex-a725 optimizations, various polly opts.
