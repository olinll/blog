---
title: "Docker 部署 Uptime Kuma 监控服务"
description: "使用 Docker Compose 部署 Uptime Kuma 开源监控工具，支持 HTTP、Ping、TCP 等多种监控方式，故障时及时通知。"
date: 2026-02-04 00:00:00
updated: 2026-02-04 00:00:00
categories:
  - 技术
tags:
  - Docker
  - 监控
  - Homelab
type: tech
---

Uptime Kuma 是一款开源的自托管监控工具，可实时监测网站或服务状态，支持 HTTP、Ping、TCP 等多种监控方式，故障时发送通知。

GitHub：[louislam/uptime-kuma](https://github.com/louislam/uptime-kuma)

## 部署

```yaml title="docker-compose.yml"
services:
  uptime-kuma:
    image: louislam/uptime-kuma:2
    container_name: uptime-kuma
    volumes:
      - ./data:/app/data
    ports:
      - 3001:3001
    restart: always
    networks:
      - app-net

networks:
  app-net:
    external: true
```
