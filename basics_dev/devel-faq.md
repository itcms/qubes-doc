---
layout: doc
title: Developers' FAQ
permalink: /doc/devel-faq/
redirect_from:
- /en/doc/devel-faq/
- /doc/DevelFaq/
- /wiki/DevelFaq/
---

Qubes Developers' FAQ
=====================

Q: Why does dom0 need to be 64-bit?
-----------------------------------

Since 2013 [Xen has not supported 32-bit x86 architecture](http://wiki.xenproject.org/wiki/Xen_Project_Release_Features) and Intel VT-d, which Qubes uses to isolate devices and drivers, is available on Intel 64-bit processors only.

In addition, often it is more difficult to exploit a bug on the x64 Linux than it is on x86 Linux (e.g. ASLR is sometimes harder to get around). While we designed Qubes with the emphasis on limiting any potential attack vectors in the first place, still we realize that some of the code running in Dom0, e.g. our GUI daemon or xen-store daemon, even though it is very simple code, might contain some bugs. Plus currently we haven't implemented a separate storage domain, so also the disk backends are in Dom0 and are "reachable" from the VMs, which adds up to the potential attack surface. So, having faced a choice between 32-bit and 64-bit OS for Dom0, it was almost a no-brainer, as the 64-bit option provides some (little perhaps, but still) more protection against some classes of attacks, and at the same time does not have any disadvantages (except that it requires a 64-bit processor, but all systems on which it makes sense to run Qubes, e.g. that have at least 3-4GB memory, they do have 64-bit CPUs anyway).

Q: What is the recommended build environment?
---------------------------------------------

Any rpm-based, 64-bit. Preferred Fedora.

Q: How to build Qubes from sources?
-----------------------------------

See [the instruction](/doc/qubes-builder/)

Q: How do I submit a patch?
---------------------------

See [Qubes Source Code Repositories](/doc/source-code/).
