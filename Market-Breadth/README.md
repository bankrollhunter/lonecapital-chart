from jchang274

![](/Market-Breadth/market-tradingview.png)

```text
//@version=4
//Thanks to LEI & LoneCapital who open a window for us to enjoy the sunshine.
//Thanks to seedof who help me find 'Index:SLTW' and test my script.
//Thanks to themarketwizards,who help me with programming.
//All above are useless for functions.

study(title="S&P500 Market Breadth", shorttitle="S&P500 Market Breadth",overlay=false)
//Set Horizontal Line
h12 = hline(120, title="Bottom", linestyle=hline.style_dashed, color=color.new(color.white,100),editable=false)
h10 = hline(100, title="Bottom", linestyle=hline.style_dashed, color=color.lime,editable=false)
h8 = hline(80, title="80%", linestyle=hline.style_dashed, color=color.lime,editable=false)
h5 = hline(50, title="Center", linestyle=hline.style_dashed, color=color.gray,editable=false)
h2 = hline(20, title="20%", linestyle=hline.style_dashed, color=color.red,editable=false)
h0 = hline(0, title="Top", linestyle=hline.style_dashed, color=color.red,editable=false)
//Fill Top and Bottom Area with Color Green and Red
fill(h0,h2,color.red,editable=false)
fill(h8,h10,color.green,editable=false)
//Output 12 Index Above 20 Days Moving Average
OnekeyInput= input(defval=false,title="One Key Hide Lines except S&P500 ????",type=input.bool)
OneKeyClose = OnekeyInput?100:0 
plot(security("INDEX:SLTW", timeframe.period, close),title = "COM   ??",color=color.purple,transp=OneKeyClose)
plot(security("INDEX:SYTW", timeframe.period, close),title = "CND   ????",color=color.red,transp=OneKeyClose)
plot(security("INDEX:SPTW", timeframe.period, close),title = "CNS   ????",color=color.orange,transp=OneKeyClose)
plot(security("INDEX:SETW", timeframe.period, close),title = "ENE   ??",color=color.yellow,transp=OneKeyClose)
plot(security("INDEX:SFTW", timeframe.period, close),title = "FIN   ??",color=color.lime,transp=OneKeyClose)
plot(security("INDEX:SVTW", timeframe.period, close),title = "HLT   ????",color=color.green,transp=OneKeyClose)
plot(security("INDEX:SITW", timeframe.period, close),title = "IND   ??",color=color.aqua,transp=OneKeyClose)
plot(security("INDEX:SBTW", timeframe.period, close),title = "MAT   ??",color=color.blue,transp=OneKeyClose)
plot(security("INDEX:SSTW", timeframe.period, close),title = "REI   ???",color=color.fuchsia,transp=OneKeyClose)
plot(security("INDEX:SKTW", timeframe.period, close),title = "TEC   ???",color=color.navy,transp=OneKeyClose)
plot(security("INDEX:SUTW", timeframe.period, close),title = "UTL   ????",color=color.olive,transp=OneKeyClose)
plot(security("INDEX:S5TW", timeframe.period, close),title = "SP500 ??500",color=color.black,linewidth=3)
//Caculate Total Score and Export it?Change Color to Alert
TTL = security("INDEX:SLTW", timeframe.period, close)+security("INDEX:SYTW", timeframe.period, close)+security("INDEX:SPTW", timeframe.period, close)+security("INDEX:SETW", timeframe.period, close)+security("INDEX:SFTW", timeframe.period, close)+security("INDEX:SVTW", timeframe.period, close)+security("INDEX:SITW", timeframe.period, close)+security("INDEX:SBTW", timeframe.period, close)+security("INDEX:SSTW", timeframe.period, close)+security("INDEX:SKTW", timeframe.period, close)+security("INDEX:SUTW", timeframe.period, close)+security("INDEX:S5TW", timeframe.period, close)
TTLAV = TTL/12
ScoreLabel=label.new(
     x = bar_index,y=88,
     text = "Total Score:"+tostring(TTL,"#"),
     style = label.style_label_left,
     color = color.new(color.white,transp=100),
     textcolor = TTLAV>80?color.lime:TTLAV<20?color.red:color.black,
     textalign = text.align_left,
     size = size.normal),
     tooltip = "Max 1200?Min 0"
label.delete(ScoreLabel[1])
```
[dLiang15 优化版](https://www.tradingview.com/script/Qnjfk4mt-S-P500-20-days-Market-Breadth/)