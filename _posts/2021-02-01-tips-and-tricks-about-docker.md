---
layout: post
title: "Tips and Tricks about Docker"
categories: tools docker
---

## To get IP address of containers

docker inspect -f '{{.Name}} - {{range .NetworkSettings.Networks}} {{.IPAddress}}{{end}}' $(docker ps -aq)
