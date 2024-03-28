---
author: Phan Bá Dũng
date: '2024-03-28'
summary: >-
  example for nginx proxy pass
tags: 
  - nginx
title: Nginx proxy pass and path
---

An example when config proxy pass in nginx

| Case # | Nginx location | proxy_pass URL | Test URL | Path received |
| ------ | -------------- | -------------- | -------- | ------------- |
| 01 | /test01 | http://127.0.0.1:8080 | /test01/abc/test | /test01/abc/test|
| 02 | /test02 | http://127.0.0.1:8080/ | /test02/abc/test | //abc/test|
| 03 | /test03/ | http://127.0.0.1:8080 | /test03/abc/test | /test03/abc/test|
| 04 | /test04/ | http://127.0.0.1:8080/ | /test04/abc/test | /abc/test|
| 05 | /test05 | http://127.0.0.1:8080/app1 | /test05/abc/test | /app1/abc/test|
| 06 | /test06 | http://127.0.0.1:8080/app1/ | /test06/abc/test | /app1//abc/test|
| 07 | /test07/ | http://127.0.0.1:8080/app1 | /test07/abc/test | /app1abc/test|
| 08 | /test08/ | http://127.0.0.1:8080/app1/ | /test08/abc/test | /app1/abc/test|
| 09 | / | http://127.0.0.1:8080 | /test09/abc/test | /test09/abc/test|
| 10 | / | http://127.0.0.1:8080/ | /test10/abc/test | /test10/abc/test|
| 11 | / | http://127.0.0.1:8080/app1 | /test11/abc/test | /app1test11/abc/test|
| 12 | / | http://127.0.0.1:8080/app2/ | /test12/abc/test | /app2/test12/abc/test|