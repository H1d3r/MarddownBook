---
title: 判断落地IP是否为真实地址的方法-初步整理
renderNumberedHeading: true
grammar_cjkRuby: true
tags: 落地,真实IP
categories:
  - 小知识
author: H1d3r
---

## 一、通过微步在线等IP反查域名平台

* 地址：https://x.threatbook.cn/
* 说明：
 -	1、通过ip反查，判断是否绑定了域名，如果有域名解析，研判所绑定域名的情况（是否是常见的ddns域名），ddns的话有可能是真实ip。
 
 ---
 
## 二、通过IPIP

* 地址：https://www.ipip.net/ip.html
* 说明： 
	> 1、 IPIP部分也会显示为“动态IP”；
    
	> 2、 其中的“代理识别”目前暂不作为参考依据。
    
   ![upload successful](/images/pasted-0.png)
    
	> 3、 部分IP，在IPIP中已经标识为”该 IP 段由运营商应用在基站（含 WIFI）用途“，则我们可以下结论，该IP就是真实IP，但大概率是移动网络的公共出口。
    
	![upload successful](/images/pasted-1.png)
    > 4、境外的IP，如果页面没有进行其他明显性的标注，则可通过对应的运营商做进一步判断，如下图中的”tm.com.my“，我们可以搜索该运营商（比如官网）的运营业务，比如是主要运营家庭网络、电话网络，或者是提供云服务器，基本可以确定为动态IP（既真实IP）；另外也可初步通过ASN数据中的信息，如果含有”-AP“字样，一般是运营商把这个网段用来作为AP（大概率是基站）的网段，也可初步判断是真实IP。
    
	![upload successful](/images/pasted-2.png)
    
	![upload successful](/images/pasted-3.png)
	> 5、如果已经明确是vps之类的数据中心，IPIP中也会标识”IDC机房使用“，就可说明是代理IP。
    
	![upload successful](/images/pasted-4.png)
	> 6、至于页面下方的“RTBAsia非人类访问量甄别服务，只作为在其他情况不能确定的情况下作为参考依据（放在最后来判断）。
    
    ---
## 三、通过其他技术判断

	1、 国内IP，可直接访问80端口，如果可以直接访问，基本不是真实IP；

	2、 通过端口扫描，查看是否开启了服务器常用的对外端口