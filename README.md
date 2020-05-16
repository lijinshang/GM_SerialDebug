# GM_SerialDebug
                      GM SerialDebug串口调试软件 by 李锦上
  * 功能简介 
  * =======================================
  * 1.串口基本功能 
  * 支持文本模式、HEX模式发送和接收； 
  * 支持自动搜索可用串口； 
  * 串口打开时可设置波特率； 
  * 支持自动发送； 
  * 支持行尾发送换行(CR)符； 
  * 支持帧循环模式循环发送； 
  * 支持帧循环模式单帧发送； 
  * 支持发送时间自动计算功能； 
  * 支持发送时间重叠检测； 
  * 支持自动保存发送数据； 
  * 支持导出接收数据； 
  * 支持HEX模式发送时自动格式化输入数据：自动去除多余的空格、自动拆分少输入的空格、自动补0；
  * 例如输入：A0 b  c D0E  
  * 格式化后：A0 0B 0C D0 0E 
  * 接收区选择：暂停接收或串口未打开时可选择接收区数据，否则不能选择 
  * 自动发送：发送时间精确到毫秒级 
  * 智能滚动：鼠标在接收区内不自动滚动到底部，否则收到新数据自动滚动至底部 
  * 自动分割帧：当帧与帧间隔时间大于5ms时自动分割帧 
  * 复制发送区：将发送数据添加至接收区 
  * 时间戳：接收和发送数据增加时间戳 
  * 窗体自适应：所有窗体控件自适应大小 
  * 动态分隔：支持鼠标拖拽接收区、发送区动态分隔空间 
  * 快捷键：增加按钮快捷键功能 如：Ctrl+Enter:发送数据 

  * 数据完整性：中文文本不乱码，数据完整不断帧； 
  * 性能稳定：大吞吐量下不卡顿； 
  * =======================================
  * 2.数据示波功能：当连接的串口收到指定格式的数据时会将数据转成波形显示在数据示波窗口。
  * 通信协议：支持CH0-CH9十个通道。
  * 帧格式例：A5 5A 0B A0 A4 70 45 41 A4 70 45 C1 AA  
  * Byte0-1 ：A5 5A 帧头 
  * Byte2   ：0B 本帧包含的字节数，除了起始字节外 
  * Byte3   ：A0 功能码 数据示波 
  * Byte4-7 ：A4 70 45 41 (float) CH0通道的数据:12.34 
  * Byte8-11：A4 70 45 C1 (float) CH1通道的数据:-12.34 
  * Byte12  ：AA 帧尾 
  * 点击右侧CH0-CH9通道按钮，可隐藏或显示曲线。隐藏曲线后只显示通道号，显示曲线时会显示当前通道的数据 
  * 每屏数据：每屏固定显示点数，超过此值如在自动滚屏状态会自动滚屏；在鼠标拖拽查看时此项无效 
  * 自动滚屏：自动跟踪最新数据并向左滚动屏幕 
  * 暂停：暂停接收帧数据并停止更新屏幕 
  * 保存图像：将屏幕的数据保存成PNG图片格式 
  * 保存数据：将收到的波形数据保存成.CSV格式以便用Excel分析 
  * 缩放：鼠标放在x轴刻度区滚动滚轮可缩放x轴；放在y轴刻度区滚动滚轮可缩放y轴；按住Ctrl+鼠标拖动可选区放大 
  * 自测试：可以自动生成CH0-CH9十通道正弦数据供测试用 
  * 显示通道名：可以显示或隐藏用户自定义通道名 
  * =======================================
  * 3.参数调试功能：当勾选启用参数调试时，串口发送部分由参数调试窗口接管，此时串口发送区内容无效。
  * LED通信协议： LED功能需要勾选启用数据示波功能启用，无需勾选参数调试功能 
  * 帧格式例：A5 5A 0B B0 01 00 FF 00 00 00 00 00 AA 
  * Byte0-1 ：A5 5A 帧头 
  * Byte2   ：0B 本帧包含的字节数，除了起始字节外 
  * Byte3   ：B0 功能码 LED状态 
  * Byte4   ：01 LED0的状态:非0点亮 
  * Byte5   ：00 LED1的状态:为0熄灭 
  * Byte6   ：FF LED2的状态:非0点亮 
  * Byte7   ：00 LED3的状态:为0熄灭 
  * Byte8   ：00 LED4的状态:为0熄灭 
  * Byte9   ：00 LED5的状态:为0熄灭 
  * Byte10  ：00 LED6的状态:为0熄灭 
  * Byte11  ：00 LED7的状态:为0熄灭 
  * Byte12  ：AA 帧尾 
 
  * 滑块通信协议：
  * 帧格式例：A5 5A 23 C0 A4 70 45 41 B8 1E 63 42     
  *           00 00 00 00 00 00 00 00 00 00 00 00     
  *           00 00 00 00 00 00 00 00 00 00 00 00 AA  
  * Byte0-1 ：A5 5A 帧头 
  * Byte2   ：23 本帧包含的字节数，除了起始字节外 
  * Byte3   ：C0 功能码 参数调试-滑块 
  * Byte4-7 ：A4 70 45 41 (float) 滑块0的数据:12.34 
  * Byte8-11：B8 1E 63 42 (float) 滑块1的数据:56.78 
  * Byte12-35：滑块2-滑块7的数据 
  * Byte36  ：AA 帧尾 
 
  * 按钮通信协议：
  * 帧格式例：A5 5A 05 D0 00 01 AA  
  * Byte0-1 ：A5 5A 帧头 
  * Byte2   ：05 本帧包含的字节数，除了起始字节外 
  * Byte3   ：D0 功能码 参数调试-按钮 
  * Byte4   ：00 按钮数据高字节:备用 
  * Byte5   ：01 按钮数据低字节:按钮0按下 (0x80:按钮7按下) 
  * Byte6   ：AA 帧尾 
 
  * 保存配置：保存界面设置 
 
  * =======================================
  * 软件更新地址：https://github.com/lijinshang/GM_SerialDebug 
  * 软件编写匆忙难免有bug，还请不吝指正 
  * 作者邮箱：lijinshang@126.com 
  * =======================================

  
  ![image](https://github.com/lijinshang/GM_SerialDebug/blob/master/Images/GM_SerialDebug-1.png)
  ![image](https://github.com/lijinshang/GM_SerialDebug/blob/master/Images/GM_SerialDebug-2.png)
  ![image](https://github.com/lijinshang/GM_SerialDebug/blob/master/Images/GM_SerialDebug-3.png)
  ![image](https://github.com/lijinshang/GM_SerialDebug/blob/master/Images/GM_SerialDebug-4.png)
  ![image](https://github.com/lijinshang/GM_SerialDebug/blob/master/Images/GM_SerialDebug-5.png)
  ![image](https://github.com/lijinshang/GM_SerialDebug/blob/master/Images/GM_SerialDebug-6.png)
  ![image](https://github.com/lijinshang/GM_SerialDebug/blob/master/Images/GM_SerialDebug-7.png)
  
