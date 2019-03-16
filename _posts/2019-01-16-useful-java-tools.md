---
layout: post
title:  "Java实用工具"
date:   2019-01-16 06:45:01 +0800
categories: Java
---

## jdb

### 远程调试

<code> > JAVA_TOOL_OPTIONS=" -agentlib:jdwp=transport=dt_socket,server=y,suspend=y,address=5000" <i>command</i> </code>

<code> > jdb -attach <i>[host:]port</i> </code>


