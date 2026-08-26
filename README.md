MUDOS\_64

Modern Ultra Deterministic Operating System 64-bit



OVERVIEW



MUDOS\_64 is an independently developed x86-64 operating system focused on efficiency, predictable behaviour, low-overhead multicore execution and a tightly integrated desktop environment.



The operating system uses a custom monolithic kernel, native Ring 3 application model, custom filesystem architecture, multicore scheduler, networking stack, hardware drivers and graphical desktop environment.



MUDOS\_64 is written primarily in C and x86-64 Assembly and boots through UEFI.



MUDOS\_64 is distributed as proprietary binary freeware. Official compiled releases may be used free of charge and redistributed unmodified under the terms of LICENSE.txt.



CURRENT RELEASE



MUDOS\_64 v1.9.4



Official builds are distributed through the Releases section of this repository.



For the most accurate representation of MUDOS\_64, use the latest official release and the current documentation.



PROJECT GOALS



MUDOS\_64 is designed around a simple principle:



Implement the functionality the system needs while avoiding unnecessary architectural overhead.



The project prioritises:



\* Low runtime overhead

\* Predictable scheduling and timing behaviour

\* Efficient multicore scaling

\* Compact system architecture

\* Strong process isolation

\* Modular native applications

\* Direct hardware support

\* Responsive graphical interaction

\* Minimal legacy burden

\* Long-term architectural expandability



MUDOS\_64 does not attempt to reproduce another operating system internally.



The project takes architectural inspiration from systems including Windows NT, Linux, FreeRTOS and MS-DOS while maintaining an independently designed implementation and system architecture.



CORE ARCHITECTURE



MUDOS\_64 currently targets:



\* x86-64 processors

\* UEFI systems

\* Multicore processors

\* 64-bit operation

\* Single-user desktop systems



The operating system uses a monolithic kernel architecture.



Core kernel functionality, scheduling, memory management, filesystems, networking, hardware drivers and other privileged services operate within the system kernel while remaining internally divided into dedicated subsystems and execution paths.



User applications execute separately in Ring 3 with isolated address spaces.



The desktop environment is integrated directly into the operating system rather than being installed as a separate desktop stack.



APPLICATION MODEL



MUDOS\_64 uses its own native executable and module formats.



.MEXE



.MEXE is the standard native Ring 3 application format.



Applications execute in isolated process address spaces and access operating-system functionality through the MUDOS\_64 API and ABI.



.ROOT



.ROOT is a privileged Ring 3 program format intended for trusted system-management and administration software.



.ROOT applications remain outside Ring 0 but receive broader operating-system permissions than ordinary .MEXE applications.



.MLIB



.MLIB is the native dynamically loadable module format for MUDOS\_64 applications.



The application architecture is designed so that applications can be installed, removed or replaced without recompiling the kernel or core operating-system components.



SCHEDULING AND MULTICORE EXECUTION



MUDOS\_64 uses a preemptive per-CPU scheduler derived from EEVDF principles.



The scheduler is designed for low overhead, predictable CPU distribution and responsive interactive workloads.



Current scheduling features include:



\* Weighted CPU scheduling

\* Latency classes

\* Priority inheritance

\* Multicore load balancing

\* Thread migration

\* Topology-aware placement

\* Heterogeneous CPU capability awareness

\* Tickless operation

\* Explicit blocked-thread states

\* Per-CPU scheduling structures



MUDOS\_64 separates CPU-service priority from latency requirements.



This allows interactive, background, system, audio and other workload classes to be scheduled according to their actual characteristics instead of reducing every scheduling decision to one conventional priority value.



MEMORY MANAGEMENT



The MUDOS\_64 memory subsystem includes:



\* Four-level x86-64 virtual memory

\* Separate process address spaces

\* Physical buddy allocation

\* Slab allocation

\* Demand-based memory commitment

\* File-backed mappings

\* Anonymous memory

\* Copy-on-write behaviour

\* Dynamic paging

\* Memory deduplication

\* ASLR

\* KASLR

\* NX protection

\* Strict W^X enforcement

\* Guard pages

\* Stack protection

\* PCID and INVPCID support where available



The memory architecture is designed to scale across multiple processors while avoiding unnecessary global contention.



FACIOS



MUDOS\_64 includes its own native filesystem architecture named FACIOS.



FACIOS is designed around:



\* Compact metadata

\* Efficient indexed lookup

\* Generation-safe file references

\* Files and directories

\* Large filesystem scalability

\* Transparent compression

\* Journaling and recovery

\* Integrity checking

\* Application-aware permissions

\* Asynchronous storage operation

\* Virtual filesystem integration



MUDOS\_64 also supports external storage using:



\* NTFS

\* FAT32

\* exFAT



Supported external storage devices are automatically integrated into the virtual filesystem.



FILE PERMISSION MODEL



MUDOS\_64 uses a three-tier filesystem permission model:



\* MEXE

\* ROOT

\* GLOBAL



Application-private files can remain associated with the application family that created them.



Privileged .ROOT software can access protected system-level content.



GLOBAL files are accessible across applications.



The system is designed to provide useful application isolation without requiring a conventional multi-user filesystem permission hierarchy.



SECURITY



MUDOS\_64 primarily uses preventive architectural security instead of behavioural antivirus scanning.



Current security mechanisms include, where supported:



\* Ring 0 and Ring 3 privilege separation

\* Isolated application address spaces

\* ASLR

\* KASLR

\* NX

\* Strict W^X

\* Read-only kernel code after initialisation

\* Protected kernel constant data

\* SMEP

\* SMAP

\* Stack guard pages

\* Stack canaries

\* Validated user-memory access

\* Executable validation

\* IOMMU-based DMA isolation

\* Intel VT-d

\* AMD-Vi

\* Stateful firewalling

\* Process-aware filesystem permissions



The system is designed to prevent unauthorised access and unsafe execution before they occur rather than depending primarily on behavioural malware detection after execution has already begun.



NETWORKING



MUDOS\_64 includes a native networking architecture with support for:



\* Ethernet

\* IPv4

\* TCP

\* UDP

\* DNS

\* HTTP

\* Stateful firewalling

\* Per-CPU network processing

\* Scalable network fan-in

\* Interrupt-driven networking



The networking system is designed to distribute packet-processing work across available logical processors without forcing the complete network stack through one globally serialised execution path.



HARDWARE SUPPORT



Platform support includes:



\* UEFI

\* ACPI

\* PCI

\* PCI Express

\* Multicore x86-64 processors

\* Heterogeneous CPU topologies

\* RTC

\* Interrupt controllers

\* Hardware timers



Storage support includes:



\* NVMe

\* SATA

\* USB mass storage

\* NTFS

\* FAT32

\* exFAT



USB support includes:



\* USB core

\* USB HID

\* USB audio

\* USB mass storage



Graphics support includes:



\* UEFI GOP framebuffer

\* Native GPU-driver architecture

\* AMD GPU support

\* Intel GPU support



Input support includes:



\* Keyboards

\* Standard mice

\* Mice with additional buttons



Hardware-isolation support includes:



\* Intel VT-d

\* AMD-Vi



Hardware compatibility varies by device and MUDOS\_64 release.



DESKTOP ENVIRONMENT



MUDOS\_64 includes its own integrated graphical desktop environment.



Current desktop functionality includes:



\* Desktop icons

\* Draggable files and icons

\* Folders

\* Taskbar

\* Start menu

\* Context menus

\* Window management

\* Minimise

\* Fullscreen

\* Close

\* Transparency

\* Blur

\* Window shadows

\* Framebuffer scaling

\* Notifications

\* Invalidation-based repainting



The interface deliberately uses a relatively direct and lightweight visual design instead of relying heavily on animations or unnecessary presentation layers.



INCLUDED APPLICATIONS



MUDOS\_64 includes a growing set of native applications.



Current or actively developed first-party applications include:



\* File Manager

\* Task Manager

\* Text Editor

\* Terminal

\* Clock

\* Calculator

\* Registry

\* Stress Test

\* Webby

\* Pong



MUDOS\_64 also includes work toward a native CPython environment for executing Python software through the MUDOS\_64 application architecture.



The exact application set varies by release.



WEBBY



Webby is the native MUDOS\_64 web browser.



Its purpose is to provide web access through software designed specifically for MUDOS\_64 rather than depending entirely on a browser engine originally designed for another operating system.



Webby is under active development and should not currently be expected to provide the compatibility breadth of mature browsers such as Firefox or Chromium.



PERFORMANCE PHILOSOPHY



MUDOS\_64 is deliberately designed to minimise unnecessary abstraction, background activity and system-wide contention.



The project generally prefers:



\* Event-driven operation over continuous polling

\* Per-CPU structures over global contention where appropriate

\* Bounded work

\* Efficient indexed lookup

\* Tickless scheduling

\* Explicit thread blocking

\* Lazy allocation

\* Asynchronous I/O

\* Reclaimable caches

\* Simple mechanisms where additional complexity provides little practical benefit



The objective is not merely minimum memory usage or minimum source-code size.



The intended balance is between functionality, determinism, responsiveness, scalability, maintainability and implementation complexity.



SYSTEM FOOTPRINT



MUDOS\_64 is designed to remain relatively compact compared with mainstream desktop operating systems.



Exact memory and storage requirements vary according to release, hardware configuration, enabled drivers, caches and running applications.



Current development targets are approximately:



\* Hundreds of MiB of RAM for the idle operating system

\* Only a few MiB of storage for the core operating-system files



These are development targets and may change as the system expands.



DOCUMENTATION



A public technical specification describing the architecture and externally relevant behaviour of MUDOS\_64 is available in the repository documentation.



The public specification intentionally documents the design of MUDOS\_64 without publishing the complete current source implementation.



File:



docs/MUDOS\_64\_Public\_Specification.txt



APPLICATION DEVELOPMENT



MUDOS\_64 provides a native API and ABI for independently compiled applications.



The public development interface is centred around:



MUDOS\_64\_API\_ABI.h



Native applications can use operating-system services including:



\* Windows and graphical UI

\* Filesystem access

\* Threads

\* Mutexes

\* IPC

\* Memory management

\* Timing

\* Audio

\* Networking

\* Processes

\* Dynamic modules



Application-development tools and SDK components may be distributed separately from the proprietary operating-system binaries.



Refer to the applicable SDK licence before redistributing development components.



HISTORICAL SOURCE CODE



Some older MUDOS\_64 development versions may remain publicly available for historical purposes.



These versions do not represent the architecture, feature set, implementation quality or capabilities of current MUDOS\_64 releases.



Older source snapshots should not be assumed to correspond to the current proprietary binary release.



Current MUDOS\_64 source code is not distributed under the binary software licence.



KNOWN LIMITATIONS



MUDOS\_64 is under active development.



It does not yet provide the hardware breadth, application ecosystem or compatibility coverage of mature general-purpose operating systems such as Windows, Linux or macOS.



Hardware support is currently selective and some operating-system components remain under active expansion.



Bug reports and reproducible hardware-compatibility reports are welcome through GitHub Issues.



Security-sensitive vulnerabilities should not be disclosed publicly before remediation.



BUG REPORTS



A useful bug report should include as much of the following information as possible:



\* MUDOS\_64 version

\* CPU

\* Motherboard or system model

\* GPU

\* RAM

\* Storage device

\* Relevant USB hardware

\* Relevant network hardware

\* UEFI or firmware information

\* Expected behaviour

\* Observed behaviour

\* Reproduction steps



Hardware-specific reports are particularly useful for expanding compatibility.



LICENSING



MUDOS\_64 is proprietary binary freeware.



Official compiled releases may be used free of charge.



Redistribution of unmodified official binary releases is permitted under the conditions of LICENSE.txt.



Unless separately licensed or otherwise required by applicable law, the MUDOS\_64 licence does not grant permission to:



\* Modify MUDOS\_64

\* Distribute modified versions

\* Sell licences to MUDOS\_64

\* Claim MUDOS\_64 as another person's work

\* Redistribute current MUDOS\_64 source code

\* Reverse engineer or reconstruct protected implementation material



See LICENSE.txt for the complete legal terms.



Third-party components remain subject to their respective licences.



PROJECT STATUS



MUDOS\_64 is actively developed.



Its architecture, hardware support, native applications and compatibility continue to expand between releases.



Older releases and documentation may therefore differ substantially from the current operating system.



Use the latest official release and current documentation when evaluating the present state of MUDOS\_64.



AUTHOR



MUDOS\_64 is independently developed by Julian Blaauwiekel in the Netherlands.



Development began in 2026.



DISCLAIMER



MUDOS\_64 is experimental operating-system software.



Back up important data before testing an operating system on physical hardware.



Warranty, liability and redistribution terms are defined by LICENSE.txt.

