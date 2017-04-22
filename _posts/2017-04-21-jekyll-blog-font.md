---
layout: post
title:  "【Jekyll】 Blog 字型更改成思源黑體"
date:   2017-04-21 19:00
icon: font
comments: true
---

這個版型預設的中文字型是cursive，如果要更換字型要到`css`資料夾，開啟`main.scss`，修改成以下的code，以新增`Noto Sans TC`字型：


{% highlight yml %}

@import url(//fonts.googleapis.com/earlyaccess/notosanstc.css);
// Our variables
$base-font-family: 'Space Mono', monospace,"Helvetica Neue", Helvetica, Arial, 'Noto Sans TC';
$head-font-family: 'Work Sans',"Helvetica Neue", Helvetica, Arial, sans-serif, 'Noto Sans TC';

{% endhighlight %}



