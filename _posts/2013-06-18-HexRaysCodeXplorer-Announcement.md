---
title: Announcement of HexRaysCodeXplorer plugin
layout: post
---

On [REcon conference](http://recon.cx/2013/schedule/events/15.html) on this week we will be present our plugin for Hex-Rays Decompiler - **HexRaysCodeXplorer**. We already a long time working with static code analysis complex threats as Stuxnet, Flame, Festi and many [more](http://rehints.com/publications/). One of the problem with analysis this threats it's bad code navigation in Hex-Rays Decompieler. We use Hex-Rays Decompieler for static analysis big code parts when is possible. This tool really help us to analyse object oriented code. We make emulation for C++ objects with Hex-Rays C-structures representation.   

{{ excerpt_separator }}

How example strucure for defined smart pointer looks like this: 
<pre><code>
typedef struct SMART_PTR
{
    void    *pObject;   // pointer to the object
    int     *RefNo;     // reference counter
};
</code></pre>

And in decompiled code looks like this code:
![](/assets/posts{{ page.id }}/SmartPtr.png)