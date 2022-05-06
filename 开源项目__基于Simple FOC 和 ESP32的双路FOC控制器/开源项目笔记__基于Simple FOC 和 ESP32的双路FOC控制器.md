开源项目地址：
    控制：  
    https://oshwhub.com/zdldcyy/ji-yu-Simple-FOC-ESP32de-shuang-?sharesource=qzone#P2
    驱动：  
    https://oshwhub.com/zdldcyy/l6234-shuang-lu-wu-shua-qu-dong_esp32-kuo-zhan-ban#P4

实现思路大概是：两个采样通道获取采样通过ADC将电流数据交给主控芯片，编码器信号也交给主控芯片，主控芯片处理后发出三个pwm信号，