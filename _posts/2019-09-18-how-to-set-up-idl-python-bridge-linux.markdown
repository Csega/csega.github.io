---
layout: post
title:  "How to set up IDL Python bridge without admin rights on Linux?"
date:   2019-09-18 15:18:29 +0200
categories: mypost
---
# Introduction

For more than a year [I wrote a post][previous-post] about setting up the [IDL Python Bridge][idl-python-bridge] on Windows without administrative rights. I think it is useful for everyone who is using IDL or Python and have to interact one with another.

Right now I use IDL 8.7.0 (64 bit, Linux) with Python 3.5.2 (32 bit) running on Ubuntu 16.04.6 LTS.

So let's see what to do and how?

# How to do it?
As [before on Windows][previous-post], we have to set up variables in two files. Right now it is the [IDL startup file][idl-startup-file] and the .bashrc file, or the startup file of any other shell you use. I use bash, so I write the exact commands for this shell right now, on other shells you have to look for the specific commands yourself.

The location of your [IDL startup file][idl-startup-file] in Linux have to be defined at  your .bashrc file with the following commnand. Assuming your IDL startup filename is ".idl_startup" and is located in your home directory (it can be anything, it's a standard .pro file with the normal IDL syntax) you need to add the following line to your .bashrc.

```bash
export IDL_STARTUP="$HOME/.idl_startup"
```

Since you are already editing your .bashrc file, add the next line to it as well to set up the first pillar of the [IDL Python Bridge][idl-python-bridge].

To be continued...

[idl-python-bridge]: http://www.harrisgeospatial.com/docs/Python.html
[idl-startup-file]: http://www.harrisgeospatial.com/docs/StartupFiles.html
[previous-post]: 2018-01-17-how-to-set-up-idl-python-bridge.markdown
