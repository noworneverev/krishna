---
layout: post
title:  "【VBA】 Custom previous and next sheet button"
date:   2017-09-24 07:00
icon: arrow-circle-o-right
comments: true
tags: VBA Excel
---

**Download:**  [Nextworksheet.xlam](https://github.com/noworneverev/noworneverev.github.io/releases/download/1.1/NextWorksheet.xlam){: target="_blank"}

**Demo:** ![](https://i.imgur.com/nBuWG6R.gif)

If you don't know how to use xlam file, here's the [tutorial]({% post_url 2017-09-17-excel-customize-ribbon %}){: target="_blank"}.

This is a basic customized Excel add-in to emulate browser's previous and next button.

Firstly, you can record a macro to see how Excel execute this simple function: 

{% highlight vb %}

Sub NextWorksheet()

ActiveSheet.Next.Select

End Sub

{% endhighlight %}

If you've selected the last worksheet and then exectue the code above, there would be an error popping out. To prevent this situation, I add an if...else statement to fix it.

{% highlight vb %}

Sub NextWorksheet()

Dim NumberOfSheet As Integer

NumberOfSheet = ActiveWorkbook.Worksheets.Count

If Not ActiveSheet.Index = NumberOfSheet Then
    ActiveSheet.Next.Select
Else
Exit Sub
End If

End Sub
{% endhighlight %}

<br>
<br>


