v0.0.1: 
- Initial release (changes to Capybara listed below)

v0.0.2: 
- Merge android15-6.6-lts and android15-6.6 branches' new commits. 
- Update NoMount against latest commit.
- Add missing dir_hash struct nomount_dir_node member (otherwise it fails to build!).
- Fix nomount runtime crash due to mistaken kmem_cache_create on nomount_child triggering a memory bug, and fix two other bugs, these three NoMount changes were diagnosed by Claude Sonnet 4.6 (Adaptive).
- Re-enable AnyKernel generation as requested by Poco X7 Pro community Telegram group.


Changes from Capybara kernel to Smol kernel:
- Use various optimization commits dropped from Capybara 4.0 to 5.0
- KernelSU by tiann, enabled by default
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
