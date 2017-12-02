---
layout: post
title:  "【VBA】 Search financial reports through Market Observation Post System"
date:   2017-11-03 07:00
icon: search
comments: true
tags: VBA Excel
---

**Download:**  [Market Observation.xlam](https://github.com/noworneverev/noworneverev.github.io/releases/download/1.0/market_observation.xlam){: target="_blank"}

**Demo:** ![](/images/market.gif)

If you don't know how to use xlam file, here's the [tutorial]({% post_url 2017-09-17-excel-customize-ribbon %}){: target="_blank"} and its video below.

<div style="text-align:center"><iframe width="560" height="315" src="https://www.youtube.com/embed/_8ez9G_QCUU" frameborder="0" allowfullscreen></iframe></div>

In Taiwan, there's an official site like EDGAR called Market Observation Post System (公開資訊觀測站) for users to search information of public traded companies. However, sometimes it's hard for users to find their targeting info. As a staff of an accounting firm, financial reports and annual reports are what I need mostly. So I wrote a function in which you can enter the company's code and the year to open your designated pages through Google Chrome.

The default path is ``C:\Program Files (x86)\Google\Chrome\Application\chrome.exe``, if your Google Chrome is not installed in this path, you have to modify it manually.


<br>
<br>


