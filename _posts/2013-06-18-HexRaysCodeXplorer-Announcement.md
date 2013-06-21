---
title: Announcement of HexRaysCodeXplorer plugin
layout: post
---

On [REcon conference](http://recon.cx/2013/schedule/events/15.html) on this week we will be speaking about Gapz bootkit and presenting our plugin for Hex-Rays Decompiler - **HexRaysCodeXplorer**. We already have been working for a long time with static code analysis of such complex threats as Stuxnet, Flame, Festi and many [more](http://rehints.com/publications/). In the course of the research of Gapz bootkit we faced the problem of position independent code analysis once again. This motivated us for developing a plugin for Hex-Rays decompiler which makes the process of reversing position independent and object oriented code easier. 

{{ excerpt_separator }}

One of the approaches to tackle this problem in Hex-rays decompiler so far is to use structures (Local types) to represent objects.

![](/assets/posts{{ page.id }}/local_types.png)


As an example, here is a structure which describes a smart pointer type: 
<pre><code>
typedef struct SMART_PTR
{
    void    *pObject;   // pointer to the object
    int     *RefNo;     // reference counter
};
</code></pre>

Which results in the following decompiled code:

![](/assets/posts{{ page.id }}/SmartPtr.png)

Unfortunately these structures are to be created manually in the course of reversing the code what takes a lot of time. Another thing is that there is no possibility to navigate through the object's code using this approach in Hex-Rays decompiler. In other words, when you encounter the following expression

![](/assets/posts{{ page.id }}/hook_routine.png)

It is not possible to go to decompiled code of hook_routine by double clicking on it, since the decompiler doesn't know its address.
Hex-Rays plugin architecture allows us to approach the aforementioned difficulties. The decompiler's SDK provides access to its internal structures and, therefore, leverage its capabilities.


**Here are the main features of the plugin which we would like to have in the first release:**
* navigation through virtual function calls in Hex-Rays Decompiler window; 
* automatic type reconstruction for C++ objects;
* useful interface for working with objects & classes;

**HexRaysCodeXplorer** - open source plugin, the source code will be shared after the first stable release. But if you want to join for beta testing HexRaysCodeXplorer send email request to **info@rehints.com** with a few words about "Why it's interesting for you?" and we share the binary of plugin.  
If you interested in HexRaysCodeXplorer and have features requests for future releases let us know at **info@rehints.com** with any feedback.
