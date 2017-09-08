#GenReport——服务器性能测试报告生成工具
>- 功能简介
>- 使用步骤  
>- 更多细节了解
>- 修订记录
 
##1. 功能简介
该工具可以用来生成服务器性能测试报告，涵盖了当前服务器性能测试的所有测试项，报告的形式与数据中心当前所用的模板保持一致。支持一次生成多个套餐的数据汇总（多套餐即多个测试方案，比如不同的服务器型号和测试配置）。  
##2. 使用步骤
###2.1  log文件准备：
将本轮测试中各套餐的数据分别打包到不同的文件夹下，命名好文件夹的名称，如果有多个套餐，名称做好区分，因为报告的sheet页名称将以套餐名命名。  
多套餐的文件组织形式参考：  
![一级目录](https://i.imgur.com/dHKNE1M.jpg)   
图1  多套餐一级目录  

![二级目录](https://i.imgur.com/cyYiFCh.jpg)  
图2  多套餐二级目录  

**报告命名规则约定（xxx代表任意）：**  
xxxCINTxxx.ref  
xxxCFPxxx.ref  
xxxIOMeterxxx.csv  
xxxmlcxxx.log  
xxxlinpackxxx.txt  
xxxnetperfxxx.txt  
xxxstreamxxx.txt  

###2.2    工具运行
 
####step1: 选择【log文件目录】：  
多个套餐需要选择套餐所在目录的上一级，比如，下面的目录结构，应该选择：性能测试报告  
    
    ——性能测试报告  
       ——A套餐性能数据  
       ——B套餐性能数据  
        ……  

选择目录后，工具界面会展示该目录下搜索到的所有套餐和套餐内的文件，供用户查看。

####step2: 选择【报告保存路径】：可选  
默认在log文件目录所在的路径下
####step3: 修改【报告保存名称】：可选
默认以所选log目录的名称命名，会在后面加上时间后缀，避免多次运行时发生重名覆盖。
####step4: 点击【报告生成】
生成过程界面有状态提示，生成完毕后，界面会提示报告所在的地址。
####step5: 报告结果查看
参考界面提示的报告地址，打开生成的报告文件进行查看。生成结果样式如下：
 
####工具日志
工具执行过程会有日志信息打印（gen_report_tool.log），记录工具执行过程中的一些debug信息和错误信息等，如果出现异常，可以查看。也可以反馈给工具开发人员，并附带上该日志信息。  
  
工具开发人员联系方式：  
RTX: yuyinxia  
Email:
yuyinxia@hikvision.com.cn

##3. 更多细节了解
请参考《服务器性能测试报告生成工具产品需求说明》，下载地址：
[https://10.1.14.79/testdev/HITA/trunk/testcases/Camera_Dome/数据中心专用/性能测试报告生成工具](https://10.1.14.79/testdev/HITA/trunk/testcases/Camera_Dome/数据中心专用/性能测试报告生成工具)

##4. 修订记录
- 2016.05.19： 发布GenReportV1.0。 实现性能测试报告生成的需求，具体见:  
[https://10.1.14.79/testdev/HITA/trunk/testcases/Camera_Dome/12-DataCenter/性能测试报告生成工具/服务器性能测试报告生成工具产品需求说明.docx](https://10.1.14.79/testdev/HITA/trunk/testcases/Camera_Dome/12-DataCenter/性能测试报告生成工具/服务器性能测试报告生成工具产品需求说明.docx "服务器性能测试报告生成工具产品需求说明")
- 2016.06.14： 发布GenReport_V1.1。  
   **增加：**  
   （1）操作界面增加【打开报告】按钮，可以快速打开已生成的报告；  
   （2）IOMeter,netperf支持多份报告整理。  

        注意：
        多份报告的名称中需要含有 IOMeter或netperf字样，大小写不限，名称剩余的字符随意。  
        如：log的名称为：IOMeter (RAID)，IOMeter_raid, netperf_2UIN, 
        生成的测试报告中，对应的测试项名称会转换为：IOMeter测试 (RAID)，IOMeter测试_raid, 网络性能测试_2UIN。
    
    **修改：**  
    （1）优化数据显示形式。参考测试人员提供的样板报告，对有些数据做了小数点后保留4位，有些小数点后保留2位（使用四舍五入法，与手工报告的显示保持一致）  
