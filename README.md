

Miki量化框架  
====
	  1.目前量化领域，保密性几乎成为行业的标准，这同时也导致大量重复性开发，Miki量化框架的宗旨就是希望能减少这种重复性
	    造轮子的情况。  
	  2.后期框架将会逐渐支持美股、日股等市场，最终目标是支持全球主要股票市场交易(如果技术能够实现的话)。
	  3.完全采用python语言实现的量化框架，原则尽量以简洁的语言实现金融交易等功能，系统架构清晰，方便二次开发，理论支持
	    股票、期货、期权等，目前只支持股票。  
	  4.通过缓存数据提取等技术基本可以实现很快速度回测，一年基本可以10~15分钟完成。
	  5.如果遇到问题，欢迎提交issue、代码，QQ群：1042883511。  
	  6.欢迎下单接口和第三方数据接口合作。


系统要求：
----	
	1.内存最好16G以上
	2.硬盘最好采用固态硬盘，1T~2T
	3.注册jqdata或rqdata等第三方数据接口(可能需要付费)
	4.安装pycharm社区版方便多程序运行
	
框架架构：  
----
	1.api为下单接口实现  
	2.data为数据存储、接收、提取等功能的实现，实盘模式需要运行main.py文件  
	3.strategy为策略实现模块，  
	  1.新建py文件实现策略功能，   
	  2.策略开头通过 from system.trade.strategyVar import * 引入全局变量  
	    initialize 实现策略的初始化，
	    before_trading_start 每天开盘前运行，  
	    handle_data 每分钟运行，
	    after_trading_end 每天收盘后运行，
	    after_backtest_end 回测结束后运行。  
	3.trade主要包含：
	   1.context 上下文会话模块
	   2.logger 日志模块
	   3.order 下单模块
	   4.system 主引擎模块
	   5.strategyVar 全局变量模块
	   6.types 数据类型模块
	   7.dataGenerator 数据推送模块		
	   8.others.yaml为一些配置，ChangeDict为公司股票更名信息，Multiplier为期货合约单位  
	4.others为其它模块：
	   1.technical 实现一些常见技术指标的计算，如Boll、Macd、Kdj等
	5.运行前：
	  1.建议配备一块1T-2T的固态硬盘  
	  2.通过dataOthers.py的save_old_data存储行情数据到本地，缓存大小10年大概150G左右  
	  3.通过dataOthers.py的generate_dataUnit函数生成cache推送数据，dataGenerator.py读取cache文件进行数据推送    
	  4.dataSQL.py的update_finance_data从api读取财务数据等存储到本地  
	  5.实盘运行data文件夹的main.py实现数据接收，api文件夹的orderPool.py实现api接口下单，SimTrade.py实现策略运行  
	6.有问题通过阅读源码也可以对系统架构更熟悉  


项目捐赠：  
---
	支付宝账号：15012463435  



























