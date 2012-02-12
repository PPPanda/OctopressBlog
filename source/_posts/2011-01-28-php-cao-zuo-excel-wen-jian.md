--- 
categories: 
  - PHP
comments: true
layout: post
published: true
status: publish
tags: 
  - book
  - cat
  - ie
  - php
title: php操作excel文件
type: post
---
我运行这段程序提示出错了啊?高手帮我看看哪里有问题? 

	//首先一步 
	$excel = new COM("Excel.sheet") or Die ("Did not instantiate Excel");// 建立EXCEL的COM对象 
	
	//打开一个工作簿 
	//$pathin = "工作簿目录"; 
	//$workbook = "工作簿名称"; 
	$pathin = "c:"; 
	$workbook = "111.xls"; 
	
	$wkb = $excel->application->Workbooks->Open($pathin.$workbook) or Die ("Did not open $pathin $workbook"); 
	
	//建新工作簿 
	//$wkb = $excel->application->Workbooks->Add or Die("Unable to add a new work book"); 
	
	//打开工作表 
	$sheet_name = "sheet1" 
	$sheet = $wkb->Worksheets($sheet_name) or Die("Unable to active $sheet_name"); 
	
	//读一个单元格 
	$row = 1; 
	$column = 1; 
	$readcell = $sheet->cells($row,$column); //行和列直接用十进制数表示 
	$readcell->activate; 
	$result = $selcell->value; //读出单元格值 
	print($result); 
	?>