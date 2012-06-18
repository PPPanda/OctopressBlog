--- 
categories: 
  - internet
comments: true
layout: post
published: true
status: publish
tags: 
  - Chrome
  - GoogleChromeProtable
title: 设置 google chrome protable 为默认浏览器
type: post
---

以下是 win7 下设置 google chrome protable 为默认浏览器的 注册表文件

1) chrome.reg:

	Windows Registry Editor Version 5.00

	[HKEY_LOCAL_MACHINE\SOFTWARE\RegisteredApplications]
	"Chrome Portable"="Software\\Clients\\StartMenuInternet\\GoogleChromePortable\\Capabilities"

	[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\GoogleChromePortable\Capabilities]
	"ApplicationName"="Google Chrome Portable"
	"ApplicationDescription"="Google Chrome Portable is a web browser that runs web pages and applications with lightning speed. It's designed to be simple and stylish. It's packaged as a portable app, so you can take your browsing experience with you."
	"ApplicationIcon"="\"D:\\Softwares\\Portable\\Extracted\\GoogleChromePortable\\GoogleChromePortable.exe\",0"
	"Hidden"=dword:00000000

	[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\GoogleChromePortable\Capabilities\FileAssociations]
	".htm"="GoogleChromePortableHTML"
	".html"="GoogleChromePortableHTML"
	".shtml"="GoogleChromePortableHTML"
	".xht"="GoogleChromePortableHTML"
	".xhtml"="GoogleChromePortableHTML"

	[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\GoogleChromePortable\Capabilities\StartMenu]
	"StartMenuInternet"="GoogleChromePortable"

	[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\GoogleChromePortable\Capabilities\URLAssociations]
	"http"="GoogleChromePortableURL"
	"https"="GoogleChromePortableURL"
	"ftp"="GoogleChromePortableURL"

	[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\GoogleChromePortable]
	"LocalizedString"="Google Chrome Portable"
	""="Google Chrome Portable"

	[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\GoogleChromePortable\DefaultIcon]
	""="\"D:\\Softwares\\Portable\\Extracted\\GoogleChromePortable\\GoogleChromePortable.exe\",0"

	[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\GoogleChromePortable\shell\open\command]
	""="\"D:\\Softwares\\Portable\\Extracted\\GoogleChromePortable\\GoogleChromePortable.exe\""

	[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\GoogleChromePortable\shell\properties\command]
	""="\"D:\\Softwares\\Portable\\Extracted\\GoogleChromePortable\\GoogleChromePortable.exe\" -preferences"

	[HKEY_LOCAL_MACHINE\SOFTWARE\Classes\GoogleChromePortableURL]
	""="Google Chrome Portable URL"
	"URL Protocol"=""

	[HKEY_LOCAL_MACHINE\SOFTWARE\Classes\GoogleChromePortableURL\DefaultIcon]
	""=hex(2):22,00,44,00,3A,00,5C,00,53,00,6F,00,66,00,74,00,77,00,61,00,72,00,\
	65,00,73,00,5C,00,50,00,6F,00,72,00,74,00,61,00,62,00,6C,00,65,00,5C,00,45,\
	00,78,00,74,00,72,00,61,00,63,00,74,00,65,00,64,00,5C,00,47,00,6F,00,6F,00,\
	67,00,6C,00,65,00,43,00,68,00,72,00,6F,00,6D,00,65,00,50,00,6F,00,72,00,74,\
	00,61,00,62,00,6C,00,65,00,5C,00,47,00,6F,00,6F,00,67,00,6C,00,65,00,43,00,\
	68,00,72,00,6F,00,6D,00,65,00,50,00,6F,00,72,00,74,00,61,00,62,00,6C,00,65,\
	00,2E,00,65,00,78,00,65,00,22,00,2C,00,30,00,00,00

	[HKEY_LOCAL_MACHINE\SOFTWARE\Classes\GoogleChromePortableURL\shell\open\command]
	""=hex(2):22,00,44,00,3A,00,5C,00,53,00,6F,00,66,00,74,00,77,00,61,00,72,00,\
	65,00,73,00,5C,00,50,00,6F,00,72,00,74,00,61,00,62,00,6C,00,65,00,5C,00,45,\
	00,78,00,74,00,72,00,61,00,63,00,74,00,65,00,64,00,5C,00,47,00,6F,00,6F,00,\
	67,00,6C,00,65,00,43,00,68,00,72,00,6F,00,6D,00,65,00,50,00,6F,00,72,00,74,\
	00,61,00,62,00,6C,00,65,00,5C,00,47,00,6F,00,6F,00,67,00,6C,00,65,00,43,00,\
	68,00,72,00,6F,00,6D,00,65,00,50,00,6F,00,72,00,74,00,61,00,62,00,6C,00,65,\
	00,2E,00,65,00,78,00,65,00,22,00,20,00,2D,00,75,00,72,00,6C,00,20,00,22,00,\
	25,00,31,00,22,00,00,00

	[HKEY_LOCAL_MACHINE\SOFTWARE\Classes\GoogleChromePortableHTML]
	""="Google Chrome HTML"

	[HKEY_LOCAL_MACHINE\SOFTWARE\Classes\GoogleChromePortableHTML\DefaultIcon]
	""="\"D:\\Softwares\\Portable\\Extracted\\GoogleChromePortable\\GoogleChromePortable.exe\",0"

	[HKEY_LOCAL_MACHINE\SOFTWARE\Classes\GoogleChromePortableHTML\shell\open\command]
	""="\"D:\\Softwares\\Portable\\Extracted\\GoogleChromePortable\\GoogleChromePortable.exe\" -url \"%1\""

2) Control Panel -> Default Programs -> Google Chrome Portable -> Set this program as default.

Tá feita a cagada!

原帖地址： http://portableapps.com/node/23082