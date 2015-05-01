---
title: HexRaysCodeXplorer v1.6 new features and support for IDA 64-bit
layout: post
---

Today we are [realising](https://github.com/REhints/HexRaysCodeXplorer/releases/tag/1.6) an updated version 1.6 of HexRaysCodeXplorer. The new version of the plugin supports latest versions of IDA v6.8 and Hex-rays Decompiler v2.2. In this update we also provide support for IDA versions for 64-bit.

{{ excerpt_separator }}

About 2 weeks ago new versions of IDA and Hex-rays Decompiler have been [released](https://www.hex-rays.com/products/ida/6.8/index.shtml). Along with certain improvements and bug fixes the update brought some changes into the SDK what rendered HexRaysCodeXplorer uncompilable. As a result we have updated source code of the plugin to address the SDK modifications.

64-bit version
==============

Now the new version of CodeXplorer plugin can be used with IDA 64-bit. In order to compile the plugin for working with 64-bit binaries you need to choose either **Debug x64** or **Release x64** in configuration manager in MS Visual Studio. The *Platform* field should be set to **Win32** since IDA 64-bit is, in fact, a 32-bit application. The 64-bit version of the plugin will get *.p64* extension (32-bit version has *.plw* extension)

![](/assets/posts{{ page.id }}/vs_64_bit.jpg)

Once built the plugin should be copied into *plugins* subdirectory of IDA Pro installation directory and it's ready to be used.

New feature in ObjectExplorer: XREFS for virtual tables
=======================================================
From version 1.6 CodeXplorer starts displaying cross-references to virtual tables in ObjectExplorer window. It is useful for direct navigation into IDA-View window to code where VTBL methods is called.

![](/assets/posts{{ page.id }}/xrefs.png)

NorthSec 2015 is coming
=======================

![](/assets/posts{{ page.id }}/nsec.jpg)

And there are almost three weeks left before beginning of the security conference NorthSec 2015 in Montréal, Canada where we will be giving a presentation titled [Object Oriented Code RE with HexraysCodeXplorer](https://www.nsec.io/speakers/). In this talk we will take an in-depth look at challenges related to reversing object-oriented code with respect to modern malware: implementation of polymorphism and class inheritance in MS Visual C++ compiler; C++ templates and so on. 

In the presentation we will demonstrate how HexRaysCodeXplorer can be employed in reverse engineering of complex threats created with object oriented programming languages. 

Currently, we are working on a new release of HexRaysCodeXplorer v1.7 [NSEC Edition] which we are planning to make publicly available for NorthSec 2015. We are always happy to get any feedback on the project. All features requests, comments or bugs can be submitted to [issues tracker](https://github.com/REhints/HexRaysCodeXplorer/issues) or **support@rehints.com**.

P.S.: We are also working on the next-generation v2.0 of HexRaysCodeXplorer plugin. It will be available in this summer ;) Stay tuned!
