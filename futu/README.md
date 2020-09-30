# FUTU

>PC和MOB区别：由于手机查看的时候线条太多，MOB方案去掉了SMA线。建议使用文件的方式。

富途可以通过两种方式自定义指标; 

- 自行添加代码;
   1. 复制过去需要自行添加变量：P1,P2,P3,P4; 
   2. 需要添加P1...P4的最大值，不然Win平台会有bug（仅影响修改，不影响显示，version:10.8.7958.08071518）;
   3. 注意软件的提示。

- 文件导入;
   1. 下载自定义的指标文件（链接见下方）;
   2. 导入自定义的指标文件即可;

## 参数设置（均线）
> 如何你会一点编程建议使用变量的形式来替代数字（5,20,60,120）

| 参数名| 默认值 | 最大值 | 最小值 |
| --- | --- | --- | --- |
| P1 | 5 | 1000 | 0 |
| P2 | 20 | 1000 | 0 |
| P3 | 60 | 1000 | 0 |
| P4 | 120 | 1000 | 0 |

## 文件导入
- [双均线抵扣价 和 乖离率20](/futu/futu.zip)
- [双均线抵扣价](/futu/LC.ftindex)
- [乖离率](/futu/GL20.ftindex)


## GLL 乖离率
```text
CS:(CLOSE-MA(CLOSE,20))/MA(CLOSE,20)*100,LINETHICK1,COLORFF8D1E;
SM:(MA(CLOSE,20)-MA(CLOSE,60))/MA(CLOSE,P2)*100,LINETHICK1,COLOR0CAEE6;
ML:(MA(CLOSE,60)-MA(CLOSE,120))/MA(CLOSE,P3)*100,COLORSTICK;
```

## 双均线
```text
W1:=REF(CLOSE,20);
W2:=REF(CLOSE,60);
W3:=REF(CLOSE,120);

{K线颜色 5 20 60 120}
{价在线上，线向上；价在线下，线向下。所见即所得。FROM: HTTPS://YOUTU.BE/PE04VSHLE1G?T=337}
STICKLINE(C<W1,H,L,0.71,0),COLORLIGRAY;
STICKLINE(C<W2,H,L,0.71,0),COLORGRAY;
STICKLINE(C>W1,O,C,0.71,0),COLORGREEN;

{黄色点 5 20 60 120}
DRAWICON(CURRBARSCOUNT=5+1,L,41);
DRAWICON(CURRBARSCOUNT=20+1,L,41);
DRAWICON(CURRBARSCOUNT=60+1,L,41);
DRAWICON(CURRBARSCOUNT=120+1,L,41);

{SMA 20 60 120}
MA2:MA(CLOSE,20), COLORB6B1B1, DOTLINE;
MA3:MA(CLOSE,60), COLORD751A8, DOTLINE;
MA4:MA(CLOSE,120), COLOR94B8C4, DOTLINE;

{EMA 5 20 60 120
EMA1:EMA(CLOSE,5), COLORRED;
EMA2:EMA(CLOSE,20), COLOR69F6EB;
EMA3:EMA(CLOSE,60), COLORFFAEC9;
EMA4:EMA(CLOSE,120), COLORBLUE;
```

![PC](/futu/PC.jpg)



 有任何问题请点击[这里](https://github.com/kentio/lonecapital-chart/issues/new)
 