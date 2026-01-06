# mx23-kernel-6.19-rcX
Linux kernel 6.19.rcX built for testing on MXLinux 23.
This is for TESTING ONLY. Do not use in production. Use at your own risk.

I have been messing with amdgpu for an old Radeon HD 8790M and not having much luck getting the results I wanted. When I read that, through Valve sponsorship, the new 6.19 RC kernels have increased support for my old SI chipset, I decided I wanted to check it out.

This was compiled on a system running MXLinux 23.5 (Debian bookworm), that hasn't had packages updated in quite a while.

I compiled vanilla sources using oldconfig from kernel 6.12.35-1~mx23ahs.

I've read that recent kernel builds are big on disk space. Being decades since I've self-compiled a kernel, I was REALLY surprised at just how big. The linux-6.19-rc3 source directory ballooned out to a massive 31GB, starting from a reasonably sized 246M .tar.gz. Compiling with DEBUG_INFO_NONE=y on a fresh source directory of linux-6.19-rc4 (yes, rc3+1 was released yesterday), it appears that the huge size was due to debugging symbols. The linux-6.19-rc4 source directory only grew to 5GB with debug disabled.

While thinking about source and compile sizes, it occurred to me that kernel.org is compressing the tarballs with GZ rather than XZ. Out of curiosity, I did some size comparisons:
Uncompressed source dir: 1.7G
Tarball with GZ compression: 246M
Tarball with XZ compression: 190M

I'd be curious as to the reason kernel.org distributes as gz instead of xz. While 56M doesn't sound like much to the adverage user with highspeed internet and terrabyte hard drives. Considering most web hosting charges per tier of storage and per tier of transfer, this 56M could add up quickly over hundres or thousands of downloads.
