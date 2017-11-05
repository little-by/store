# CanToolApp for Windows 测试报告
## 文档概述
本文档记录了在CanToolApp for Windows开发过程中的单元测试，与预期结果进行了对比，为完善及改进软件的功能提供依据。并且对测试小组的功能测试结果进行了评价。

## 单元测试结果概述
### 用户设置COM口信息
####场景1
- 输入：Com口选择下拉框能够检测到本机所有Com口，用户从下拉框中选择一个，然后设置Com口的波特率(Baud Rate)，数据位(Data Bits)，校验位(Parity)，停止位(Stop Bits)后单击Open按钮。
- 输出：打开设置好的Com口
- 预期结果：能够和CANTool装置进行通信
- 实际结果：
!<https://github.com/QhdJiaYou/CANToolAppImage/blob/master/1.jpg>

####场景2
- 输入：用户点击Save按钮将Com口设置信息保存到CANToolApp设定文件中
- 输出：Debug文件夹下生成Cfg.ini文件
- 预期结果：Com口的配置信息以键值对的形式保存在Cfg.ini文件中，用户每次打开Com口都会预加载文件中的设置。
- 实际结果：!<https://github.com/QhdJiaYou/CANToolAppImage/blob/master/7.jpg>
### 用户设置CANTool装置信息
####场景1
- 输入：点击Open按钮
- 输出：发送字符串“O1\r”
- 预期结果：用户接收到打开成功（Success）的提示，使CANTool装置进入工作状态，本地Open按钮不可再次触发
- 实际结果：!<https://github.com/QhdJiaYou/CANToolAppImage/blob/master/2.jpg>
####场景2
- 输入：点击Close按钮
- 输出：发送字符串“C\r”
- 预期结果：用户接收到关闭成功（Success）的提示，使CANTool装置进入CAN初始化状态，本地Close按钮不可再次触发
- 实际结果：!<https://github.com/QhdJiaYou/CANToolAppImage/blob/master/4.jpg>
####场景3
- 输入：点击Version按钮
- 输出：发送字符串“V\r”
- 预期结果：无论是在CANTool装置Open状态还是close状态，用户都能接收到CANTool装置返回的版本信息
- 实际结果：!<https://github.com/QhdJiaYou/CANToolAppImage/blob/master/3.jpg>
####场景4
- 输入：用户从CANTool速率设置下拉框中选择速率，点击发送Send按钮
- 输出：发送字符串“Sn\r”
- 预期结果：用户接收到设置成功（Success）的提示
- 实际结果：!<https://github.com/QhdJiaYou/CANToolAppImage/blob/master/5.jpg>
####场景5
- 输入：用户点击Save按钮将CANTool装置设置信息保存到CANToolApp设定文件中
- 输出：Debug文件夹下生成Cfg.ini文件
- 预期结果：CANTool装置信息以键值对的形式保存在Cfg.ini文件中，用户每次打开设置都会预加载文件中的值。
- 实际结果：!<https://github.com/QhdJiaYou/CANToolAppImage/blob/master/7.jpg>
### 接收和解析CAN信息

### 封装和发送CAN信息
####场景1
- 输入：用户从下拉框中选择Message信息，然后选择对应的Signals信息，填写规定范围的物理值，填写发送周期（不是必选项）
- 输出：封装好的通信信息
- 预期结果1：在正常通信的情况下（Com口打开的状态，CANTool装置打开的状态），用户收到成功发送的提示
- 实际结果1：!<https://github.com/QhdJiaYou/CANToolAppImage/blob/master/6.jpg>
- 预期结果2：在正常通信的情况下（Com口打开的状态，CANTool装置关闭的状态），用户收到先打开CANTool装置的提示
- 实际结果2：!<https://github.com/QhdJiaYou/CANToolAppImage/blob/master/8.jpg> 
- 预期结果3：在正常通信的情况下（Com口关闭的状态），用户收到先打开Com口的提示
- 实际结果3：!<https://github.com/QhdJiaYou/CANToolAppImage/blob/master/9.jpg>
### 用户保存CAN信息

## 对功能测试结果的评价
测试小组给出了我们小组项目的功能测试结果。
