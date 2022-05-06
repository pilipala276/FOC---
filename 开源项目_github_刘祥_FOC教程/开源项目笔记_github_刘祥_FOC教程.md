开源项目地址：
https://gitee.com/wojialaomuzhu/foc-tutorial/tree/main/
https://www.bilibili.com/video/BV1jV411s7F8/?spm_id_from=trigger_reload

实现思路大概是：三个个采样通道获取采样通过ADC将电流数据交给主控芯片，编码器信号也交给主控芯片，主控芯片处理后发出三个pwm信号

但是限定功率是12V×4A，需要的是24V×4A
