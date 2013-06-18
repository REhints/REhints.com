---
title: Announcement of HexRaysCodeXplorer plugin
layout: post
---

On [REcon conference](http://recon.cx/2013/schedule/events/15.html) on this week we will be present our plugin for Hex-Rays Decompiler - **HexRaysCodeXplorer**. We already a long time working with static code analysis complex threats as Stuxnet, Flame, Festi and many [more](http://rehints.com/publications/). One of the problem with analysis this threats it's bad code navigation in Hex-Rays Decompieler. We use Hex-Rays Decompieler for static analysis big code parts when is possible. This tool really help us to analyse object oriented code. We make emulation for C++ objects with Hex-Rays C-structures representation.   

{{ excerpt_separator }}

How example strucure which defined a smart pointer type looks like this: 
<pre><code>
typedef struct SMART_PTR
{
    void    *pObject;   // pointer to the object
    int     *RefNo;     // reference counter
};
</code></pre>

And in decompiled code looks like this code:

![](/assets/posts{{ page.id }}/SmartPtr.png)

But Hex-Rays Decompiler not support code navigation for this type of objects reproduced by structures. HexRaysCodeXplorer developed for fixed this problems.

Here is the features list for first release:
* one
* two 
* three 

**HexRaysCodeXplorer** - open source plugin, but before first stable release we not share a source code. But if you want to join for beta testing HexRaysCodeXplorer send email request to **info@rehints.com** with a few words about "Why it's interesting for you?" and we share the binary of plugin.  

If you interested about HexRaysCodeXplorer and have a features request for future releases let us know to **info@rehints.com** with any feedback.