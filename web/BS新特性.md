<!--
 * @Author: 星啸(陈远宏)
 * @Date: 2020-12-15 14:32:55
 * @LastEditTime: 2021-01-04 16:33:13
 * @LastEditors: 星啸(陈远宏)
 * @Description: 
 * @FilePath: /my-git-book/web/BS新特性.md
-->
列举一些看到的B/S架构的新特性

## WebWorker

## ServiceWorker

## WebSocket

## Cache相关
### 多级缓存
- SW
- memory Cache
- disk Cache
- network
### 缓存控制字段
Expires
cache-control
- no Store：本session内也不要使用，memoryCache不要用
- no Cache：下次页面打开不要使用缓存
- max-age：最长时间
### 协商缓存
HTTP控制码304的方式
协商缓存：Modify（1.0）和ETag（1.1）的方式

Modify的方式有几个弊端：文件变动在秒级的无法区别；文件周期性变动修改时间，但实际内容无变换的场景

见：https://www.jianshu.com/p/84baa1689647