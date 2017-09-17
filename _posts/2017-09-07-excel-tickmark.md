---
layout: post
title:  "【VB】 Excel Tickmark, an add-in for auditors and accountants"
date:   2017-09-07 07:00
icon: file-excel-o
comments: true
tags: Visual_Basic Excel
---
**Main page:** [http://tickmark.tw/](http://tickmark.tw/){: target="_blank"}  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [https://noworneverev.github.io/TickMark/](https://noworneverev.github.io/TickMark){: target="_blank"}

The domain name of tickmark.tw will expire on 2018-03-27, and I won't renew it since I can't afford it with my low salary in Big 4 in Taiwan.

**Download:**  [Click me](https://github.com/noworneverev/TickMark/releases/download/1.0.0/Tick.Mark.msi){: target="_blank"}

**Repo:** [https://github.com/noworneverev/TickMark](https://github.com/noworneverev/TickMark){: target="_blank"}

**Install:** Execute the msi set-up file, and keep clicking next step til end. Then open your Excel, there should pop out a window asking your permission to install the program. Click yes or ok and wait a minute. If you want to remove this add-in, go to control panel to remove this Excel Ribbon like any other software.

**Screenshot:**  
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/cover.png" title="Screenshot">
</div>

**Demo:**
<iframe width="680" height="400" src="https://www.youtube.com/embed/Hi4jG4As_h8" frameborder="0" allowfullscreen></iframe>

**Before start:**  
This was my first Visual Basic program. Before I wrote this Visual Basic based add-in, I only had some basic knowledge of VBA. I spent the whole March building this add-in and self-learning Visual Basic simultaneously.

**Why and Purpose:**  
I had an internship in one of the Big 4 when I was in college, and from that experience I knew that there's customized tool called tickmark embedded in firm's Excel which is designed to help auditors to deal with working papers. In that month, I heard a senior staff said she would miss this add-in when she left. Therefore, after 2 years, when I prepared for the boring CPA exam, I suddenly had an idea that maybe I could create an Tickmark Excel add-in on my own, and there it is.

**Details:**  
***1\. PBC text-box***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/0.png" title="PBC">
</div>
Pressing PBC button would add a text-box with "PBC" texting in your worksheet's top-left corner. "PBC" is abbreviated from "prepared by client".

<br>

***2\. Font-Family***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/1.png" title="Font-Family">
</div>
I isolated some commonly-used fonts, including "Arial", "Book Antiqua", "Calibri", "標楷體", "微軟正黑體", "新細明體". You could save some time from selecting these fonts from the drop-down.

<br>

***3\. Electronic working paper mark***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/2.png" title="Electronic working paper mark">
</div>
As far as I know, every accounting firm has its oftenly used mark, so I made some marks that maybe you could use. (These marks came from two of the Big 4.)

<br>

***4\. Graphic Symbol, Greek Alphabet &amp; Roman Numerals***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/3.png" title="Graphic Symbol">
</div>
<br>
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/4.png" title="Greek Alphabet">
</div>
<br>
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/5.png" title="Roman Numerals">
</div>
Several symbols that you could used to represent specific cells.

<br>

***5\. Sum a b c***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/6.png" title="Sum a b c">
</div>
These symbols could be useful when your need to sum some cells' value up, but they are scattering in the worksheet.

<br>

***6\. Down &amp; right arrow***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/7.png" title="Down arrow">
</div>
<br>
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/8.png" title="Right arrow">
</div>
Select a range and you can draw an arrow that you need.

<br>

***7\. Arrow &amp; textbox***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/9.png" title="Arrow &amp; textbox">
</div>
Select a cell to add a connecting arrow and a textbox to the corner.

<br>

***8\. Range arrow***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/10.png" title="Range arrow">
</div>
Select a range to draw an arrow connecting with multiple lines in the corner.

<br>

***9\. Others***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/11.png" title="Others">
</div>
Open the calendar pane, add a checkbox to the selected cell, the bottom double line, and the format with a thousands separator.

<br>

***10\. Fill Color***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/12.png" title="Fill Color">
</div>
5 fill colors that you could choose and one button to remove fill color.

<br>

***11\. Direction***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/13.png" title="Direction">
</div>
Create two boxes pointing to each other. You could use this to imply that two selected cells are related.

<br>

***12\. Note***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/note.png" title="note">
</div>
Simply auditor's nightmare.

<br>

***13\. Left Brace***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/14.png" title="Left Brace">
</div>
Select a range to draw an entry brace.

<br>

***14\. Insert Column***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/15.png" title="Insert Column">
</div>
Insert a narrow column to let you put some marks.

<br>

***15\. Cell Link***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/16.png" title="Cell Link">
</div>
Create boxes linked with hyperlinks to the corner of both selected cells. This function is the most complicated and also the main reason why I created this add-in. 

<br>

***16\. HyperLink***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/17.png" title="HyperLink">
</div>
Build hyperlinks on both of the selected cells and remove the default hyperlink format.

<br>

***17\. Signature***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/18.png" title="Signature">
</div>
To set up your name, go to File &gt; Options &gt; General &gt; User name.

<br>

***18\. Marker***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/19.png" title="Marker">
</div>
For in-charge, manager or partner to review the working paper.

<br>

***19\. Get Motivated Every Day!***
<div style="text-align:center">
<img src="https://noworneverev.github.io/TickMark/images/gallery/fulls/20.png" title="Get Motivated Every Day!">
</div>
900 motivated quotes I collected from Reddit, fb/the idealist and other internet sources. I aimed at encouraging those who are also suffering in Big 4 by making this. I used rnd function to generate the quote you will see, so you might see the same quotes sometimes, and also some you might never see. <i class="fa fa-smile-o" aria-hidden="true"></i>

I will add other quotes which I read after I completed this project to a VBA based function. Stay tuned on my my blog!

> There will always be a space between the alt right and alt left.


<br>
<br>