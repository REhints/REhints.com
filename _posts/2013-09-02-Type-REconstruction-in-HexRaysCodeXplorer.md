---
title: Type REconstruction in HexRaysCodeXplorer
layout: post
---

In this blog post we would like to account for “Type Reconstruction” feature of HexRaysCodeXplorer plugin, what motivated us for developing it, the basic ideas behind its implementation and how to use it. 

{{ excerpt_separator }}

Position Independed Code Analysis Problem
=========================================

Using position independed code by the malware makes a task of reverse engineering more challenging, especially in case of static analysis. One of the reasons for this is that the calls to the routines implemented within the binary in question or to any external APIs are performed indirectly. In other words, instead of getting nice disassembly code, like this one (a part of TDL4 kernel-mode driver):

![](/assets/posts{{ page.id }}/tdl4_code.png)

one would have to deal with the code presented below:

![](/assets/posts{{ page.id }}/gapz_pic.png)

where variable ***a2*** holds pointer to the context of the position independed code of Win32/Gapz bootkit.

The same problem concerns analysis of object-oriented code when pointer to the table of virtual methods is stored in an object instance and is initialized at the creation of an object as shown below:

![](/assets/posts{{ page.id }}/oop.png)

We already addressed these issues at [Recon 2013](http://recon.cx/2013/schedule/events/15.html). One of the workarounds for this problem is using the functionality provided by IDA Pro disassembler, namely, “Local Types”. For each instance of position independed code (or object in case of OOP) we can create structure with corresponding layout to ease the analysis:

![](/assets/posts{{ page.id }}/ida_localtypes.png)

However, manually creating structures in IDA Pro is quite tedious work (especially for object-oriented code with large number of objects) so we were looking for the ways to automate this.

Reconstructing Types Using Hex-Rays
===================================

And this is how we came up with the idea of developing plugin for Hex-Rays decompiler. The idea is quite simple: automatically build the structure representing instance of position independed code or an object given its pointer. The Hex-Rays was chosen because of the ability to access intermediate representation of the decompiled code what is very useful in tracking which fields of the structure being reconstructed are referenced in the code.
In the heart of this approach lies ***ctree*** – a special tree-like structure representing the decompiled routine:

![](/assets/posts{{ page.id }}/ctree.png)

Each node in the structure is represented as ***c_itemt*** structure and refers to either an expression or a statement in terms of the language C. Being able to traverse this tree we can identify the layout of the structure. Here is the list of ***c_itemt*** structures which are helpful for this purpose:
* ***memptr***, ***memref*** – referencing bytes within a buffer at given offset
* ***idx*** – referencing an element of  array
* ***call*** – transferring control to another routine
* ***asg*** – assigning value to operand
* ***ptr*** – referencing value pointed to by the pointer

Here is the picture for clarification which describes how the reference of DWORD at offset 12 in buffer ***a1*** is indentified

<pre><code>
*(DWORD *)(a1 + 12) = 0xEFCDAB89:
</code></pre>

![](/assets/posts{{ page.id }}/assignement.png)

As a result, to be able to reconstruct a type using HexRaysCodeXplorer one needs to select the variable holding pointer to the instance of position independed code or to an object and by right-button mouse click select from the context menu “Reconstruct Type” option:

![](/assets/posts{{ page.id }}/selection.png)

In the current version of the plugin the reconstructed structure is displayed in output window:

![](/assets/posts{{ page.id }}/output.png)

The source code of the plugin will be available soon on GitHub and we are going take part in the [IDA plugin contest](https://www.hex-rays.com/contests/) with HexRaysCodeXplorer ;) If you are interested in HexRaysCodeXplorer and have features requests for future releases, please, let us know at **info@rehints.com**.