MUDOS_64

Modern Ultra Deterministic Operating System 64-bit

MUDOS_64 is an independently developed x86-64 operating system focused on efficiency, predictable behaviour, low-overhead multicore execution and a tightly integrated desktop environment.

It uses a custom monolithic kernel, native Ring-3 application model, custom filesystem architecture, multicore scheduler, networking stack, hardware drivers and graphical desktop environment. The system is written primarily in C and x86-64 Assembly and boots directly through UEFI.

MUDOS_64 is distributed as proprietary binary freeware. Official compiled releases may be used free of charge and redistributed unmodified under the terms of the included LICENSE.txt.

CURRENT RELEASE

MUDOS_64 v1.9.4

Download official builds from the repository's Releases section.

Release packages should be obtained from the official MUDOS_64 repository whenever possible.

PROJECT GOALS

MUDOS_64 is designed around a relatively simple principle:

Implement the functionality the system needs while avoiding unnecessary architectural overhead.

The project prioritises:

- low runtime overhead;
- predictable scheduling and timing behaviour;
- efficient multicore scaling;
- compact system architecture;
- strong process isolation;
- modular native applications;
- direct hardware support;
- responsive graphical interaction;
- minimal dependence on legacy interfaces;
- long-term architectural expandability.

MUDOS_64 is not intended to reproduce an existing operating system internally. Its architecture is independently designed, although the project takes inspiration from systems including Windows NT, Linux, FreeRTOS and MS-DOS.

CORE ARCHITECTURE

MUDOS_64 currently targets:

- x86-64
- UEFI
- multicore processors
- 64-bit operation
- single-user desktop systems

The system uses a monolithic kernel architecture. Core kernel functionality, scheduling, memory management, filesystems, networking, drivers and other privileged services operate as part of the system kernel while remaining internally separated into dedicated subsystems and execution paths.

User applications execute separately in Ring 3 with their own address spaces.

The desktop environment is an integrated part of the operating system rather than a separately installed desktop stack.

APPLICATION MODEL

MUDOS_64 uses its own native executable and module formats.

.MEXE

.MEXE is the standard native Ring-3 application format.

Applications execute in isolated process address spaces and access operating-system functionality through the public MUDOS_64 API/ABI.

.ROOT

.ROOT is a privileged Ring-3 runtime-program format used for trusted system-level applications and administration functionality.

.ROOT applications remain outside Ring 0 but are granted broader operating-system permissions than ordinary .MEXE applications.

.MLIB

.MLIB provides dynamically loadable native modules for MUDOS_64 applications.

The application architecture is designed so applications can be added, removed or replaced without recompiling the operating-system kernel.

SCHEDULING AND MULTICORE EXECUTION

MUDOS_64 uses a preemptive, per-CPU, EEVDF-derived scheduler designed for low overhead, predictable CPU distribution and responsive interactive workloads.

The scheduler supports:

- weighted CPU scheduling;
- latency classes;
- priority inheritance;
- multicore load balancing;
- thread migration;
- topology-aware placement;
- heterogeneous CPU capability awareness;
- tickless operation;
- blocked-thread scheduling states;
- per-CPU scheduling structures.

MUDOS_64 distinguishes CPU service priority from latency requirements, allowing interactive, background, audio and system workloads to be treated differently without relying on one conventional priority value alone.

MEMORY MANAGEMENT

The memory subsystem provides:

- four-level x86-64 virtual memory;
- separate process address spaces;
- physical buddy allocation;
- slab allocation;
- demand-based memory commitment;
- file-backed mappings;
- anonymous memory;
- copy-on-write behaviour;
- dynamic paging;
- memory deduplication;
- ASLR and KASLR;
- NX protection;
- strict W^X enforcement;
- guard pages;
- stack protection;
- PCID/INVPCID support where available.

Memory-management structures are designed to scale across multiple processors while avoiding unnecessary global contention.

FACIOS

MUDOS_64 includes its own native filesystem architecture called FACIOS.

FACIOS is designed around:

- compact metadata;
- efficient indexed lookup;
- generation-safe file references;
- directories and files;
- large filesystem scalability;
- transparent compression;
- journaling and recovery;
- integrity checking;
- application-aware permissions;
- asynchronous storage operation;
- removable-storage support through the VFS.

MUDOS_64 also supports external filesystems including:

- NTFS
- FAT32
- exFAT

External storage devices are automatically integrated through the virtual filesystem where supported.

FILE PERMISSION MODEL

MUDOS_64 uses a three-tier filesystem permission model:

- MEXE
- ROOT
- GLOBAL

Ordinary application-private files can remain associated with the application family that created them.

Privileged .ROOT software can access protected system-level content.

Files marked GLOBAL are accessible across applications.

The model is intended to provide useful application isolation without requiring a conventional multi-user permission hierarchy.

SECURITY

MUDOS_64 uses preventive architectural security rather than behavioural antivirus scanning.

Current security mechanisms include, where supported:

- Ring-0 / Ring-3 privilege separation;
- isolated application address spaces;
- ASLR;
- KASLR;
- NX;
- strict W^X;
- read-only kernel code after initialisation;
- protected kernel constant data;
- SMEP;
- SMAP;
- stack guard pages;
- stack canaries;
- validated user-memory access;
- executable validation;
- IOMMU-based DMA isolation;
- VT-d / AMD-Vi support;
- stateful firewalling;
- process-specific filesystem permissions.

The system is designed around preventing unauthorised access rather than attempting to detect malicious behaviour after it has already occurred.

NETWORKING

MUDOS_64 includes a native networking architecture with support for:

- Ethernet;
- IPv4;
- TCP;
- UDP;
- DNS;
- HTTP;
- stateful firewalling;
- per-CPU network processing;
- scalable network fan-in;
- interrupt-driven network operation.

Networking is designed to distribute work across available logical processors without forcing the complete network stack through one global execution path.

HARDWARE SUPPORT

The hardware layer includes or is designed to include support for:

Platform

- UEFI
- ACPI
- PCI / PCIe
- multicore x86-64 processors
- heterogeneous CPU topologies
- RTC
- interrupt controllers
- hardware timers

Storage

- NVMe
- SATA
- USB mass storage
- NTFS
- FAT32
- exFAT

USB

- USB core
- USB HID
- USB audio
- USB mass storage

Graphics

- UEFI GOP framebuffer
- native GPU-driver architecture
- AMD GPU support
- Intel GPU support

Input

- keyboards
- standard mice
- mice with additional buttons

Isolation

- Intel VT-d
- AMD-Vi

Hardware compatibility varies by device and MUDOS_64 version.

DESKTOP ENVIRONMENT

MUDOS_64 includes its own integrated graphical desktop environment.

The desktop currently provides:

- desktop icons;
- draggable files;
- folders;
- taskbar;
- Start menu;
- context menus;
- window management;
- minimise;
- fullscreen;
- close;
- transparency;
- blur;
- shadows;
- framebuffer scaling;
- notifications;
- invalidation-based repainting.

The interface deliberately favours a relatively flat, direct and lightweight design rather than animation-heavy presentation.

INCLUDED APPLICATIONS

MUDOS_64 includes a growing set of native applications, including:

- File Manager
- Task Manager
- Text Editor
- Terminal
- Clock
- Calculator
- Registry
- Stress Test
- Webby
- Pong

MUDOS_64 also includes work toward a native CPython 3.14 environment for running Python software through the MUDOS_64 application architecture.

Available applications vary by release.

WEBBY

Webby is the native MUDOS_64 web browser.

Its purpose is to provide web access without requiring an existing browser engine designed for another operating system.

Browser functionality is under active development and should not currently be assumed to have the compatibility breadth of mature browsers such as Firefox or Chromium.

PERFORMANCE PHILOSOPHY

MUDOS_64 is deliberately designed to keep unnecessary abstraction and background activity limited.

The project generally prefers:

- event-driven operation over polling;
- per-CPU structures over global contention where appropriate;
- bounded work;
- direct indexing where practical;
- low-complexity lookup structures;
- tickless scheduling;
- explicit blocking;
- lazy allocation;
- asynchronous I/O;
- reclaimable caches.

The target is not simply minimum memory usage or minimum source-code size. The goal is a favourable balance between functionality, determinism, responsiveness, scalability and implementation complexity.

SYSTEM FOOTPRINT

MUDOS_64 is designed to remain relatively small compared with mainstream desktop operating systems.

Exact memory and storage requirements vary by release, enabled hardware and running applications.

Current builds are designed around a system footprint of approximately:

- hundreds of MiB of RAM at idle
- only a few MiB of core system storage

These figures are development targets and may change as functionality expands.

DOCUMENTATION

A public-safe technical specification describing the architecture of MUDOS_64 is available in the repository documentation.

See:

docs/MUDOS_64_Public_Specification.txt

The public specification intentionally documents system architecture and externally relevant behaviour without publishing the complete current source implementation.

APPLICATION DEVELOPMENT

MUDOS_64 provides a native API/ABI for independently compiled applications.

The public development interface is centred around:

MUDOS_64_API_ABI.h

Native applications can use operating-system services including:

- windows and UI;
- files;
- threads;
- mutexes;
- IPC;
- memory;
- timing;
- audio;
- networking;
- processes;
- dynamic modules.

Application-development tools and SDK components may be distributed separately from the proprietary operating-system binaries.

Refer to the applicable SDK licence before redistributing development components.

HISTORICAL SOURCE CODE

Some older MUDOS_64 development versions may remain publicly available for historical purposes.

These versions do not represent the architecture, feature set, quality or implementation of current MUDOS_64 releases.

In particular, old source snapshots should not be assumed to correspond to the current proprietary binary release.

Current MUDOS_64 source code is not distributed under the binary software licence.

KNOWN LIMITATIONS

MUDOS_64 is under active development.

It does not yet provide the hardware breadth, application ecosystem or compatibility coverage of mature general-purpose operating systems such as Windows, Linux or macOS.

Hardware support is currently selective, and some system components remain under active expansion.

Bug reports and reproducible hardware-compatibility reports are welcome through GitHub Issues.

Security-sensitive reports should not be disclosed publicly before remediation.

REPORTING BUGS

When reporting a bug, include as much of the following information as possible:

- MUDOS_64 version;
- CPU;
- motherboard or system model;
- GPU;
- RAM;
- storage device;
- relevant USB/network hardware;
- UEFI/firmware information;
- expected behaviour;
- observed behaviour;
- reproduction steps.

Hardware-specific reports are particularly useful for expanding compatibility.

LICENSING

MUDOS_64 is proprietary binary freeware.

You may use official compiled MUDOS_64 releases free of charge.

Redistribution of unmodified official binary releases is permitted under the conditions of LICENSE.txt.

Unless separately licensed, you may not:

- modify MUDOS_64;
- distribute modified versions;
- sell licences to MUDOS_64;
- claim MUDOS_64 as your own work;
- redistribute current MUDOS_64 source code;
- reverse engineer or reconstruct protected implementation material except where applicable law grants a right that cannot validly be restricted.

See the full licence:

LICENSE.txt

Third-party components remain subject to their respective licences.

PROJECT STATUS

MUDOS_64 is actively developed.

The architecture, hardware support, native applications and compatibility layer continue to expand rapidly between releases.

Because of this, older releases and documentation may differ substantially from the current system.

For the most accurate representation of MUDOS_64, use the latest official release and current documentation.

AUTHOR

MUDOS_64 is independently developed by Julian Blaauwiekel.

Development began in 2026.

DISCLAIMER

MUDOS_64 is experimental operating-system software.

Back up important data before testing an operating system on physical hardware.

The Software is provided under the warranty and liability terms specified in LICENSE.txt.
