<p><span style="font-size:24px;"><img src="//image.lceda.cn/pullimage/BeKtCYCkBFHmg9WwCgHTtyvJlVFbQr9IegJLNILD.jpeg" alt="" width="1200" height="959" /><img src="//image.lceda.cn/pullimage/Xvp6bZrh6rQiIrhPNO0csvpuXyDMFiFNoKnv8Qww.jpeg" alt="" width="1200" height="964" /></span></p>
<p><span style="font-size:24px;"><img src="//image.lceda.cn/pullimage/l6tKMiqEkFk8JY0QnoynvlRcf1eGn5MWnRXdfRmQ.jpeg" alt="" width="1200" height="695" /></span></p>
<p><span style="font-size:24px;">        基于ESP32的双路FOC控制器，代码采用开源的SimpleFOC，实现双路无刷电机的矢量控制。</span></p>
<p><span style="font-size:24px;">        准备用在自己的无刷四足机器人上的。控制器和驱动器分开设计，采用板卡对插的方式，方便后期更换更大电流的驱动板。配套的驱动板稍晚些也会发出来~</span></p>
<p><span style="font-size:24px;">        欢迎关注我的b站，板子的用法和部分代码也会在B站上更新，可以直接扫上面渲染图上的二维码直达我的主页吼吼~</span></p>
<p><span style="font-size:24px;">       </span></p>
<p><span style="font-size:24px;">我的B站：<a href="https://space.bilibili.com/423507600" target="_blank" rel="noreferrer noopener">https://space.bilibili.com/423507600</a></span></p>
<p><span style="font-size:24px;">SimpleFOC官网：<a href="https://simplefoc.com/" target="_blank" rel="noreferrer noopener">https://simplefoc.com/</a></span></p>
<p> </p>
<p><span style="font-size:24px;">------------------------------------华丽分割~---------------------------------------</span></p>
<p> </p>
<p><span style="font-size:24px;">        简单介绍下板子设计，双层PCB，主控用的是esp32-wroom，淘宝上现在12块钱一个很便宜（对没错，stm32我就是针对你了）。带有Type-c usb转串口通讯，且带有自动下载电路，不需要手动按两个按键啦！两边是标准的2.54的10pin排针，很便宜也很好买。而且上面的信号是对称分布的，你可以正面插入，也可以从后面插入，哎呀反正就是什么姿势都可以的啦！</span></p>
<p><span style="font-size:24px;"><img src="//image.lceda.cn/pullimage/QYI9N0MY2J944Oe7ktjQGVg1VkUaQbz2qSSKgb8t.jpeg" alt="" width="378" height="298" /></span></p>
<p><span style="font-size:24px;"><img src="//image.lceda.cn/pullimage/leRTIFWj5rdvC0DjqRcEvzzdUFrRCib3786Ir30c.jpeg" alt="" width="608" height="683" /></span></p>
<p> </p>
<p><span style="font-size:24px;">        偷偷告诉你，嫌整体高度高的话还可以选择背靠背贴身插入（老脸都不要了！）</span></p>
<p><span style="font-size:24px;"><img src="//image.lceda.cn/pullimage/DGI2uY8kQ8EUzlMmNobdKYrKQpUXwmDaGNZHCHLI.jpeg" alt="" width="608" height="609" /></span></p>
<p> </p>
<p><span style="font-size:24px;">        板子下方的四个连接器是编码器接口，从左至右分别为I2C1, SPI1, SPI0, I2C0.   这两个I2C是相互独立的两路，互不干扰，也就是说同时接两个as5600也没问题（众所周知，as5600的单I2C地址很坑）。注意这两个I2C我都没有加外部上拉，因为我的磁编码器板子都是加了上拉的，所以不在主板上加了，而且esp32 本身就可以设置上拉，更没必要了。</span></p>
<p> </p>
<p><span style="font-size:24px;">       剩下两个中间的接口是spi接口，这两个是共用一个spi口的，两个cs使能。这样就可以同时使用两个spi接口的编码器了，比如后面开源的TLE5012B，后期还会开源MA730，都可以直接使用。</span></p>
<p> </p>
<p><span style="font-size:24px;">       什么？ 你说你只有ABZ输出的编码器？这。。。这也完全没问题啊， 得益于esp32 的IO全自定义功能，两个I2C接口可以在软件里直接改成ABZ输入，这样就可以直接接ABZ的编码器了，就问你贴心不贴心！</span></p>
<p><span style="font-size:24px;">       还有，I2C0 和SPI都用的arduino默认pin脚，代码里都不用指明I2C/SPI使用的pin脚，直接召唤函数就行，简直比你妈还贴心有木有！</span></p>
<p> </p>
<p><span style="font-size:24px;">        顺便在这分享下我开源的磁编码器，都放在立创开源广场了：</span></p>
<p><span style="font-size:24px;"><a title="AS5600 磁编码器" href="/zdldcyy/as5600-sensor-board" target="_blank" rel="noreferrer noopener">1. AS5600 磁编码器 I2C接口和PWM接口</a></span></p>
<p><span style="font-size:24px;"><a title="tle5012b" href="/zdldcyy/tle5012b-sensor" target="_blank" rel="noreferrer noopener">2. TLE5012B 磁编码器，SPI &amp; ABZ/UVW输出</a></span></p>
<p><span style="font-size:24px;"><img src="//image.lceda.cn/pullimage/edA6yVWu9rAuDcDDv1f3hqSsK8Mlo5RZxPPCYPyC.jpeg" alt="" width="628" height="353" /></span></p>
<p><span style="font-size:24px;">        排母边上还有一个3pin（新版改为2pin）的小连接器，是CAN通讯接口，预留后面用的，暂时还没测试，一直用的uart接口。有能力的同学可以测试下，我还没用过CAN。。</span></p>
<p> </p>
<p><span style="font-size:24px;">-------------------------------再次割割---------------------------------------</span></p>
<p><span style="font-size:24px;">        </span></p>
<p><span style="font-size:24px;">使用/测试注意点：</span></p>
<p><span style="color:#e03e2d;font-size:24px;">       1. Type-c usb转串口我只设计了一边有用(因为layout不方便)，所以插上去电脑没识别串口的话就转个向再插进去就可以了。还预留了uart接口直接接出，在usb口背面，可以通过这个口和其他板子通讯和供电。</span></p>
<p><span style="font-size:24px;">       2. 板子的电源输入有两个源，一个是驱动板的电源（12V~24V）通过排针到主板，再经过DCDC &amp; LDO转成5V &amp; 3.3V；二是通过usb的5v给板子供电，两个可以同时连接，有个二极管保护usb防止倒灌电流。</span></p>
<p><span style="font-size:24px;">       3. 用驱动板的12V/24V作为电源时，需注意D2这个TVS二极管，目前设计上用的12V的TVS，要用24V电源的话需要换成24V的tvs管子。</span></p>
<p><span style="font-size:24px;">测试代码有问题的话可以用我b站上的代码先试一下。</span></p>
<p> </p>
<p><span style="font-size:24px;">#可怜的第一版，上电没几次就GG了，默哀0.1s~</span></p>
<p><span style="font-size:24px;"><img src="//image.lceda.cn/pullimage/JMcIxYZplOZAzNCIta7zjGYqKm8L7TzVrM88g4lZ.jpeg" alt="可怜的第一版，上电一次就gg了" width="1200" height="1200" /></span></p>
<p> </p>
<p><span style="font-size:24px;">2021.06.01——目前板子已验证的功能：</span></p>
<p><span style="font-size:24px;">       1. 两路AS5600 I2C接口编码器通讯。</span></p>
<p><span style="font-size:24px;">       2. 两路UVW编码器输入。</span></p>
<p><span style="font-size:24px;">       3. 两个4010无刷电机的开环速度，位置，电压控制；两个电机闭环速度，电压，位置控制。</span></p>
<p><span style="font-size:24px;">       4. 单路无刷电机的电流环控制，另一路可能驱动板有点问题，还没搞好。</span></p>
<p><span style="font-size:24px;">后续会上传测试视频，有变动会继续更新。</span></p>
<p> </p>
<p><span style="font-size:24px;">        #后续就连着我的狗腿子一起测试啦，有兴趣的来b站一起讨论。</span></p>
<p><span style="font-size:24px;"><img src="//image.lceda.cn/pullimage/j8Q8hQeGhrOipwZrDqfGwVVAODg27YnV6V1ziwpn.jpeg" alt="" width="1200" height="677" /></span></p>
<p> </p>
<p><span style="font-size:24px;">声明：本电路板仅个人兴趣开发，不对任何bug，炸板，烧电容负责，有问题可以反馈，毕竟我也不是渣男。</span></p>
<p><span style="font-size:24px;">此致</span></p>
<p><span style="font-size:24px;">解散！</span></p>            
How to use：

At editor, Click the document icon on the topbar, via "Document" > "Open" > "EasyEDA Source", and select json file, then open it at the editor.



如何使用：

在编辑器顶部工具栏，点击“文档”图标，选择 “文档” > “打开” > “EasyEDA源码”，选择json文件打开即可。