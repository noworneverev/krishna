---
layout: post
title:  "【VBA】 General Ledger Preparer (1/1)"
date:   2019-03-31 08:00
icon: gift
comments: true
tags: VBA Excel
---

### Download and Demo 
---
If you don't know why I made this, please refer to my another post: [Automated Working Paper Project (Write VBA for You for Free)]({% post_url 2019-03-31-automated-working-paper-project %}){: target="_blank"} 


**Download:**  [GLPreparer.xlsm](https://goo.gl/NKNWKf){: target="_blank"} <br>
**Demo:** ![](https://imgur.com/83fB2Qo.gif)

### Demand 
---
 To Combine descriptions of the general ledger which are been cut when imported into Excel.

It's quite often that the PBC files are in txt format. When importing such file into Excel, sometimes it really takes time to adjust it to a clean format that you you could verify its amounts or to sample some vouchers from it.

From the acutal instance here, the descriptions are been cut when the client export the GL from its system, like:<br />
1070801 TT0801  xxx bank transfer to<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; xxx bank &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; debit&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 30,000 <br />
1070802 TT0802  Issue covertible<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; bond &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; debit&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 30,000


When the data is vast and messy in a regulation, the VBA is super useful to deal with it. I could just loop through all the rows in the sheet, find all first rows that have numbers and concatenate descriptions belongs to them.

Below is the source code:
{% highlight vb %}

'Author: Mike Liao
'Date: 2019/3/23
'Contact: n9102125@gmail.com

Sub Main()
  Application.ScreenUpdating = False
  ReadTxt
  
  '新增工作表
    With ActiveSheet
      ShName = "總分類帳(整理)"
      .Copy After:=Sheets(Worksheets.Count)
     End With
    Sheets(Worksheets.Count).Name = ShName

  '合併
  Merge
  
  Application.ScreenUpdating = True
End Sub

Function ReadTxt()

Sheets.Add After:=Sheets(Worksheets.Count)
ActiveSheet.Name = "原始總分類帳"
Dim Ret
    
    Ret = Application.GetOpenFilename("文字檔案 (*.txt), *.txt")

    If Ret <> False Then
        With ActiveSheet.QueryTables.Add(Connection:= _
        "TEXT;" & Ret, Destination:=Range("$A$1"))
        .Name = "textfromfile"
        .FieldNames = True
        .RowNumbers = False
        .FillAdjacentFormulas = False
        .PreserveFormatting = True
        .RefreshOnFileOpen = False
        .RefreshStyle = xlInsertDeleteCells
        .SavePassword = False
        .SaveData = True
        .AdjustColumnWidth = True
        .RefreshPeriod = 0
        .TextFilePromptOnRefresh = False
        .TextFilePlatform = 950
        .TextFileStartRow = 1
        .TextFileParseType = xlFixedWidth
        .TextFileTextQualifier = xlTextQualifierDoubleQuote
        .TextFileConsecutiveDelimiter = False
        .TextFileTabDelimiter = True
        .TextFileSemicolonDelimiter = False
        .TextFileCommaDelimiter = False
        .TextFileSpaceDelimiter = False
        .TextFileColumnDataTypes = Array(1, 1, 1, 1, 1, 1)
        .TextFileFixedColumnWidths = Array(17, 30, 18, 16, 5)
        .TextFileTrailingMinusNumbers = True
        .Refresh BackgroundQuery:=False

        End With
    End If
End Function

Function Merge()
Dim rng As Range
Dim row As Range
Dim cel As Range
Dim StartIndex As Integer
Dim EndIndex As Integer
Dim i As Integer
Dim CountHowManyRowsNeededConcat As Integer
Dim Concatstring As String

Set rng = Range("A1:A" & ActiveSheet.Range("A" & ActiveSheet.rows.Count).End(xlUp).row)

For Each cel In rng.Cells
  If IsNumeric(Left(cel.Value, 3)) And (cel.Value <> 0) Then
    StartIndex = cel.row
    CountHowManyRowsNeededConcat = 0
    Concatstring = ""
    
    '計算起點及終點
    For i = 0 To 5
      If IsEmpty(Cells(StartIndex, 5).Offset(i, 0).Value) Then
        CountHowManyRowsNeededConcat = CountHowManyRowsNeededConcat + 1
      Else
        Exit For
      End If
    Next
    
    '已取得起點及終點，進行字串合併
    For j = 0 To CountHowManyRowsNeededConcat
      Concatstring = Concatstring & Cells(StartIndex, 2).Offset(j, 0).Value
      If j > 0 Then
        Cells(StartIndex, 2).Offset(j, 0).Value = ""
      End If
    Next
    Cells(StartIndex, 2).Value = Concatstring
    
    '將數字、借貸方、餘額移上去
    If CountHowManyRowsNeededConcat > 0 Then
      Cells(StartIndex, 3).Value = Cells(StartIndex, 3).Offset(CountHowManyRowsNeededConcat, 0).Value
      Cells(StartIndex, 4).Value = Cells(StartIndex, 4).Offset(CountHowManyRowsNeededConcat, 0).Value
      Cells(StartIndex, 5).Value = Cells(StartIndex, 5).Offset(CountHowManyRowsNeededConcat, 0).Value
      Cells(StartIndex, 6).Value = Cells(StartIndex, 6).Offset(CountHowManyRowsNeededConcat, 0).Value
      Cells(StartIndex, 3).Offset(CountHowManyRowsNeededConcat, 0).Value = ""
      Cells(StartIndex, 4).Offset(CountHowManyRowsNeededConcat, 0).Value = ""
      Cells(StartIndex, 5).Offset(CountHowManyRowsNeededConcat, 0).Value = ""
      Cells(StartIndex, 6).Offset(CountHowManyRowsNeededConcat, 0).Value = ""
    End If
  End If
Next

RemoveEmptyRows

End Function

Function RemoveEmptyRows()
  Dim r As Range, rows As Long, i As Long
  Set r = ActiveSheet.Range("A1:F" & ActiveSheet.Range("A" & ActiveSheet.rows.Count).End(xlUp).row)
  rows = r.rows.Count
  For i = rows To 1 Step (-1)
    If WorksheetFunction.CountA(r.rows(i)) = 0 Then r.rows(i).Delete
  Next
End Function




{% endhighlight %}

<br>
<br>


