---
layout: post
title: "Error about MySql driver using software `Dbeaver`"
categories: development
tags: php
---

Most likely your problem is a result of version upgrade (and some config mess).
Try to delete file ~/.local/share/DBeaverData/workspace6/.metadata/.plugins/org.jkiss.dbeaver.core/drivers.xml
Download dialog should appear just once after that.
