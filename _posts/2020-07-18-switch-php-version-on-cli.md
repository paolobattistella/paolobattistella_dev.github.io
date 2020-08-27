---
layout: post
title: "Switch php version"
categories: development
tags: php
---

# Switch php version of Apache and CLI

## Interactive switching mode
```
sudo update-alternatives --config php
```

## Manual Switching
From PHP 5.6 => PHP 7.x
Default PHP 5.6 is set on your system and you need to switch to PHP 7.x.

Apache:

```
$ sudo a2dismod php5.6
$ sudo a2enmod php7.1
$ sudo service apache2 restart
```

Command Line:

```
$ sudo update-alternatives --set php /usr/bin/php7.1
```