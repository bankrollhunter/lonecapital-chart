![](/Market-Breadth/market-tradingview.png)

- [dLiang15 版](#don-l)
- [jchang274](#jchang274)
    - [市场宽度-主图](#Market-Breadth)
    - [副图](#Side-picture)
## Market-Breadth

## Don L
[tradingview 预览](https://www.tradingview.com/script/Qnjfk4mt-S-P500-20-days-Market-Breadth/) | [view file](/Market-Breadth/donlingliang_sp500mb.pine)
```text
// This source code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © Don

//@version=4
// The maximum number of securities in script is limited to 40
//
study("S&P 500 Market Breadth")

dash_trans = 50
h0 = hline(0, color=color.new(color.black, dash_trans), linewidth=1, linestyle=hline.style_dashed)
h1 = hline(10, color=color.new(color.black, dash_trans), linewidth=1, linestyle=hline.style_dashed)
h2 = hline(20, color=color.new(color.black, dash_trans), linewidth=1, linestyle=hline.style_dashed)
h3 = hline(30, color=color.new(color.black, dash_trans), linewidth=1, linestyle=hline.style_dashed)
h4 = hline(40, color=color.new(color.black, dash_trans), linewidth=1, linestyle=hline.style_dashed)
h5 = hline(50, color=color.new(color.black, dash_trans), linewidth=1, linestyle=hline.style_dashed)
h6 = hline(60, color=color.new(color.black, dash_trans), linewidth=1, linestyle=hline.style_dashed)
h7 = hline(70, color=color.new(color.black, dash_trans), linewidth=1, linestyle=hline.style_dashed)
h8 = hline(80, color=color.new(color.black, dash_trans), linewidth=1, linestyle=hline.style_dashed)
h9 = hline(90, color=color.new(color.black, dash_trans), linewidth=1, linestyle=hline.style_dashed)
h10 = hline(100, color=color.new(color.black, dash_trans), linewidth=1, linestyle=hline.style_dashed)
h11 = hline(110, color=color.new(color.black, dash_trans), linewidth=1, linestyle=hline.style_dashed)

telcom = security("INDEX:SLTW", timeframe.period, close)
discretionary = security("INDEX:SYTW", timeframe.period, close)
staples = security("INDEX:SPTW", timeframe.period, close)
energy = security("INDEX:SETW", timeframe.period, close)
financials = security("INDEX:SFTW", timeframe.period, close)
healthcare = security("INDEX:SVTW", timeframe.period, close)
industry = security("INDEX:SITW", timeframe.period, close)
materials = security("INDEX:SBTW", timeframe.period, close)
reits = security("INDEX:SSTW", timeframe.period, close)
tech = security("INDEX:SKTW", timeframe.period, close)
utility = security("INDEX:SUTW", timeframe.period, close)

total = telcom + discretionary + staples + energy + financials + healthcare + industry + materials + reits + tech + utility
totalPercent = total / 11

colorFill(v) => v >=0 and v < 5 ? color.new(#fc4e2a, 0): v >= 5 and v<10 ? color.new(#fc4e2a, 9) :
          v >= 10 and v<15 ? color.new(#fc4e2a, 18) : v >= 15 and v<20 ? color.new(#fc4e2a, 27) :
          v >= 20 and v<25 ? color.new(#fc4e2a, 36) : v >= 25 and v<30 ? color.new(#fc4e2a, 45) :
          v >= 30 and v<35 ? color.new(#fc4e2a, 54) : v >= 35 and v<40 ? color.new(#fc4e2a, 63) :
          v >= 40 and v<45 ? color.new(#fc4e2a, 72) : v >= 45 and v<50 ? color.new(#fc4e2a, 81) :
          v >= 50 and v<55 ? color.new(#41ae76, 81) : v >= 55 and v<60 ? color.new(#41ae76, 72) :
          v >= 60 and v<65 ? color.new(#41ae76, 63) : v >= 65 and v<70 ? color.new(#41ae76, 54) :
          v >= 70 and v<75 ? color.new(#41ae76, 45) : v >= 75 and v<80 ? color.new(#41ae76, 36) :
          v >= 80 and v<85 ? color.new(#41ae76, 27) : v >= 85 and v<90 ? color.new(#41ae76, 18) :
          v >= 90 and v<95 ? color.new(#41ae76, 9) : v >= 95 and v<=100 ? color.new(#41ae76, 0) : #525252

fontColor(t) => t >=0 and t <= 10 ? color.new(#a50f15, 0): t >= 80 ? color.new(#41ae76, 0) : #fb6a4a

// total
r12y1 = plot(110, color=na)
r12y2 = plot(120, color=na)
// telcom
r11y1 = plot(100, color=na)
r11y2 = plot(110, color=na)
// discretionary
r10y1 = plot(90, color=na)
r10y2 = plot(100, color=na)
// staples
r9y1 = plot(80, color=na)
r9y2 = plot(90, color=na)
// energy
r8y1 = plot(70, color=na)
r8y2 = plot(80, color=na)
// financials
r7y1 = plot(60, color=na)
r7y2 = plot(70, color=na)
// healthcare
r6y1 = plot(50, color=na)
r6y2 = plot(60, color=na)
// industry
r5y1 = plot(40, color=na)
r5y2 = plot(50, color=na)
// material
r4y1 = plot(30, color=na)
r4y2 = plot(40, color=na)
// reits
r3y1 = plot(20, color=na)
r3y2 = plot(30, color=na)
// tech
r2y1 = plot(10, color=na)
r2y2 = plot(20, color=na)
// utility
r1y1 = plot(0,  color=na)
r1y2 = plot(10, color=na)

fill( r12y1, r12y2, color=colorFill(totalPercent), transp=10 )
fill( r11y1, r11y2, color=colorFill(telcom), transp=10 )
fill( r10y1, r10y2, color=colorFill(discretionary), transp=10 )
fill( r9y1, r9y2, color=colorFill(staples), transp=10 )
fill( r8y1, r8y2, color=colorFill(energy), transp=10)
fill( r7y1, r7y2, color=colorFill(financials), transp=10 )
fill( r6y1, r6y2, color=colorFill(healthcare), transp=10 )
fill( r5y1, r5y2, color=colorFill(industry), transp=10 )
fill( r4y1, r4y2, color=colorFill(materials), transp=10 )
fill( r3y1, r3y2, color=colorFill(reits), transp=10 )
fill( r2y1, r2y2, color=colorFill(tech), transp=10 )
fill( r1y1, r1y2, color=colorFill(utility), transp=10)

label_pos_x = round(timenow + 1000000000)

drawLabel(x, y, _text, _textcolor, _size)=>
    var label Label = na
    label.delete(Label)
    Label := label.new(x, y, _text, color=color.new(color.white, 20), textalign=text.align_left, textcolor=_textcolor, style=label.style_none, yloc=yloc.price, xloc=xloc.bar_time, size=_size)

// draw the TF labels
drawLabel(label_pos_x, 110, "Total: " + tostring(round(total)), color.black, size.normal)
drawLabel(label_pos_x, 100, "COM " + tostring(telcom), fontColor(telcom), size.normal)
drawLabel(label_pos_x, 90, "CND " + tostring(discretionary), fontColor(discretionary), size.normal)
drawLabel(label_pos_x, 80, "CNS " + tostring(staples), fontColor(staples), size.normal)
drawLabel(label_pos_x, 70, "ENE " + tostring(energy), fontColor(energy), size.normal)
drawLabel(label_pos_x, 60, "FIN " + tostring(financials), fontColor(financials), size.normal)
drawLabel(label_pos_x, 50, "HLT " + tostring(healthcare), fontColor(healthcare), size.normal)
drawLabel(label_pos_x, 40, "IND " + tostring(industry), fontColor(industry), size.normal)
drawLabel(label_pos_x, 30, "MAT " + tostring(materials), fontColor(materials), size.normal)
drawLabel(label_pos_x, 20, "REI " + tostring(reits), fontColor(reits), size.normal)
drawLabel(label_pos_x, 10, "TEC " + tostring(tech), fontColor(tech), size.normal)
drawLabel(label_pos_x, 1, "UTL " + tostring(utility), fontColor(utility), size.normal)
```

### jchang274
#### Market-Breadth
```text
//@version=4
study(title="S&P500 Market Breadth", shorttitle="S&P500 Market Breadth",overlay=false)
h0 = hline(0, title="Center", linestyle=hline.style_dashed, color=color.gray)
h1 = hline(10, title="Center", linestyle=hline.style_dashed, color=color.gray)
h2 = hline(20, title="Center", linestyle=hline.style_dashed, color=color.gray)
h3 = hline(30, title="Center", linestyle=hline.style_dashed, color=color.gray)
h4 = hline(40, title="Center", linestyle=hline.style_dashed, color=color.gray)
h5 = hline(50, title="Center", linestyle=hline.style_dashed, color=color.gray)
h6 = hline(60, title="Center", linestyle=hline.style_dashed, color=color.gray)
h7 = hline(70, title="Center", linestyle=hline.style_dashed, color=color.gray)
h8 = hline(80, title="Center", linestyle=hline.style_dashed, color=color.gray)
h9 = hline(90, title="Center", linestyle=hline.style_dashed, color=color.gray)
h10 = hline(100, title="Center", linestyle=hline.style_dashed, color=color.gray)
h11 = hline(110, title="Center", linestyle=hline.style_dashed, color=color.gray)
h12 = hline(120, title="Center", linestyle=hline.style_dashed, color=color.gray)
h13 = hline(130, title="Center", linestyle=hline.style_dashed, color=color.new(color.white,100))

SPY = security("INDEX:S5TW", timeframe.period,close)
COM = security("INDEX:SLTW", timeframe.period,close)
CND = security("INDEX:SYTW", timeframe.period,close)
CNS = security("INDEX:SPTW", timeframe.period,close)
ENE = security("INDEX:SETW", timeframe.period,close)
FIN = security("INDEX:SFTW", timeframe.period,close)
HLT = security("INDEX:SVTW", timeframe.period,close)
IND = security("INDEX:SITW", timeframe.period,close)
MAT = security("INDEX:SBTW", timeframe.period,close)
REI = security("INDEX:SSTW", timeframe.period,close)
TEC = security("INDEX:SKTW", timeframe.period,close)
UTL = security("INDEX:SUTW", timeframe.period,close)
TTL=SPY+COM+CND+CNS+ENE+FIN+HLT+IND+MAT+REI+TEC+UTL
TTLAV = TTL/12
tp =9

GLlabel13=label.new(
     x=bar_index,y=13*10-5,
     text="Total Score "+tostring(TTL,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=TTLAV>80?color.lime:TTLAV<20?color.red:color.black,
     textalign = text.align_left,
     size=size.normal)
label.delete(GLlabel13[1]) 
label.new(
     x=bar_index,y=13*10-5,
     text=tostring(TTL,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h13,h12,
     TTLAV>=95?color.new(color.green,tp*0):
     TTLAV>=90?color.new(color.green,tp*1):
     TTLAV>=85?color.new(color.green,tp*2):
     TTLAV>=80?color.new(color.green,tp*3):
     TTLAV>=75?color.new(color.green,tp*4):
     TTLAV>=70?color.new(color.green,tp*5):
     TTLAV>=65?color.new(color.green,tp*6):
     TTLAV>=60?color.new(color.green,tp*7):
     TTLAV>=55?color.new(color.green,tp*8):
     TTLAV>=50?color.new(color.green,tp*9):
     TTLAV>=45?color.new(color.red,tp*9):
     TTLAV>=40?color.new(color.red,tp*8):
     TTLAV>=35?color.new(color.red,tp*7):
     TTLAV>=30?color.new(color.red,tp*6):
     TTLAV>=25?color.new(color.red,tp*5):
     TTLAV>=20?color.new(color.red,tp*4):
     TTLAV>=15?color.new(color.red,tp*3):
     TTLAV>=10?color.new(color.red,tp*2):
     TTLAV>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))

GLlabel12=label.new(
     x=bar_index,y=12*10-5,
     text=" SPY "+tostring(SPY,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=SPY>80?color.lime:SPY<20?color.red:color.black,
     textalign = text.align_center,
     size=size.normal)
label.delete(GLlabel12[1]) 
label.new(
     x=bar_index,y=12*10-5,
     text=tostring(SPY,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h12,h11,
     SPY>=95?color.new(color.green,tp*0):
     SPY>=90?color.new(color.green,tp*1):
     SPY>=85?color.new(color.green,tp*2):
     SPY>=80?color.new(color.green,tp*3):
     SPY>=75?color.new(color.green,tp*4):
     SPY>=70?color.new(color.green,tp*5):
     SPY>=65?color.new(color.green,tp*6):
     SPY>=60?color.new(color.green,tp*7):
     SPY>=55?color.new(color.green,tp*8):
     SPY>=50?color.new(color.green,tp*9):
     SPY>=45?color.new(color.red,tp*9):
     SPY>=40?color.new(color.red,tp*8):
     SPY>=35?color.new(color.red,tp*7):
     SPY>=30?color.new(color.red,tp*6):
     SPY>=25?color.new(color.red,tp*5):
     SPY>=20?color.new(color.red,tp*4):
     SPY>=15?color.new(color.red,tp*3):
     SPY>=10?color.new(color.red,tp*2):
     SPY>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))




GLlabel11=label.new(
     x=bar_index,y=11*10-5,
     text=" COM "+tostring(COM,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=COM>80?color.lime:COM<20?color.red:color.black,
     textalign = text.align_center,
     size=size.normal)
label.delete(GLlabel11[1]) 
label.new(
     x=bar_index,y=11*10-5,
     text=tostring(COM,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h11,h10,
     COM>=95?color.new(color.green,tp*0):
     COM>=90?color.new(color.green,tp*1):
     COM>=85?color.new(color.green,tp*2):
     COM>=80?color.new(color.green,tp*3):
     COM>=75?color.new(color.green,tp*4):
     COM>=70?color.new(color.green,tp*5):
     COM>=65?color.new(color.green,tp*6):
     COM>=60?color.new(color.green,tp*7):
     COM>=55?color.new(color.green,tp*8):
     COM>=50?color.new(color.green,tp*9):
     COM>=45?color.new(color.red,tp*9):
     COM>=40?color.new(color.red,tp*8):
     COM>=35?color.new(color.red,tp*7):
     COM>=30?color.new(color.red,tp*6):
     COM>=25?color.new(color.red,tp*5):
     COM>=20?color.new(color.red,tp*4):
     COM>=15?color.new(color.red,tp*3):
     COM>=10?color.new(color.red,tp*2):
     COM>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))




GLlabel10=label.new(
     x=bar_index,y=10*10-5,
     text=" CND "+tostring(CND,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=CND>80?color.lime:CND<20?color.red:color.black,
     textalign = text.align_center,
     size=size.normal)
label.delete(GLlabel10[1])
label.new(
     x=bar_index,y=10*10-5,
     text=tostring(CND,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h10,h9,
     CND>=95?color.new(color.green,tp*0):
     CND>=90?color.new(color.green,tp*1):
     CND>=85?color.new(color.green,tp*2):
     CND>=80?color.new(color.green,tp*3):
     CND>=75?color.new(color.green,tp*4):
     CND>=70?color.new(color.green,tp*5):
     CND>=65?color.new(color.green,tp*6):
     CND>=60?color.new(color.green,tp*7):
     CND>=55?color.new(color.green,tp*8):
     CND>=50?color.new(color.green,tp*9):
     CND>=45?color.new(color.red,tp*9):
     CND>=40?color.new(color.red,tp*8):
     CND>=35?color.new(color.red,tp*7):
     CND>=30?color.new(color.red,tp*6):
     CND>=25?color.new(color.red,tp*5):
     CND>=20?color.new(color.red,tp*4):
     CND>=15?color.new(color.red,tp*3):
     CND>=10?color.new(color.red,tp*2):
     CND>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))

GLlabel9=label.new(
     x=bar_index,y=9*10-5,
     text=" CNS "+tostring(CNS,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=CNS>80?color.lime:CNS<20?color.red:color.black,
     textalign = text.align_center,
     size=size.normal)
label.delete(GLlabel9[1])
label.new(
     x=bar_index,y=9*10-5,
     text=tostring(CNS,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h9,h8,
     CNS>=95?color.new(color.green,tp*0):
     CNS>=90?color.new(color.green,tp*1):
     CNS>=85?color.new(color.green,tp*2):
     CNS>=80?color.new(color.green,tp*3):
     CNS>=75?color.new(color.green,tp*4):
     CNS>=70?color.new(color.green,tp*5):
     CNS>=65?color.new(color.green,tp*6):
     CNS>=60?color.new(color.green,tp*7):
     CNS>=55?color.new(color.green,tp*8):
     CNS>=50?color.new(color.green,tp*9):
     CNS>=45?color.new(color.red,tp*9):
     CNS>=40?color.new(color.red,tp*8):
     CNS>=35?color.new(color.red,tp*7):
     CNS>=30?color.new(color.red,tp*6):
     CNS>=25?color.new(color.red,tp*5):
     CNS>=20?color.new(color.red,tp*4):
     CNS>=15?color.new(color.red,tp*3):
     CNS>=10?color.new(color.red,tp*2):
     CNS>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))

GLlabel8=label.new(
     x=bar_index,y=8*10-5,
     text=" ENE "+tostring(ENE,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=ENE>80?color.lime:ENE<20?color.red:color.black,
     textalign = text.align_center,
     size=size.normal)
label.delete(GLlabel8[1])
label.new(
     x=bar_index,y=8*10-5,
     text=tostring(ENE,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h8,h7,
     ENE>=95?color.new(color.green,tp*0):
     ENE>=90?color.new(color.green,tp*1):
     ENE>=85?color.new(color.green,tp*2):
     ENE>=80?color.new(color.green,tp*3):
     ENE>=75?color.new(color.green,tp*4):
     ENE>=70?color.new(color.green,tp*5):
     ENE>=65?color.new(color.green,tp*6):
     ENE>=60?color.new(color.green,tp*7):
     ENE>=55?color.new(color.green,tp*8):
     ENE>=50?color.new(color.green,tp*9):
     ENE>=45?color.new(color.red,tp*9):
     ENE>=40?color.new(color.red,tp*8):
     ENE>=35?color.new(color.red,tp*7):
     ENE>=30?color.new(color.red,tp*6):
     ENE>=25?color.new(color.red,tp*5):
     ENE>=20?color.new(color.red,tp*4):
     ENE>=15?color.new(color.red,tp*3):
     ENE>=10?color.new(color.red,tp*2):
     IND>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))

GLlabel7=label.new(
     x=bar_index,y=7*10-5,
     text=" FIN "+tostring(FIN,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=FIN>80?color.lime:FIN<20?color.red:color.black,
     textalign = text.align_center,
     size=size.normal)
label.delete(GLlabel7[1])
label.new(
     x=bar_index,y=7*10-5,
     text=tostring(FIN,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h7,h6,
     FIN>=95?color.new(color.green,tp*0):
     FIN>=90?color.new(color.green,tp*1):
     FIN>=85?color.new(color.green,tp*2):
     FIN>=80?color.new(color.green,tp*3):
     FIN>=75?color.new(color.green,tp*4):
     FIN>=70?color.new(color.green,tp*5):
     FIN>=65?color.new(color.green,tp*6):
     FIN>=60?color.new(color.green,tp*7):
     FIN>=55?color.new(color.green,tp*8):
     FIN>=50?color.new(color.green,tp*9):
     FIN>=45?color.new(color.red,tp*9):
     FIN>=40?color.new(color.red,tp*8):
     FIN>=35?color.new(color.red,tp*7):
     FIN>=30?color.new(color.red,tp*6):
     FIN>=25?color.new(color.red,tp*5):
     FIN>=20?color.new(color.red,tp*4):
     FIN>=15?color.new(color.red,tp*3):
     FIN>=10?color.new(color.red,tp*2):
     FIN>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))

GLlabel6=label.new(
     x=bar_index,y=6*10-5,
     text=" HLT "+tostring(HLT,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=HLT>80?color.lime:HLT<20?color.red:color.black,
     textalign = text.align_center,
     size=size.normal)
label.delete(GLlabel6[1])
label.new(
     x=bar_index,y=6*10-5,
     text=tostring(HLT,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h6,h5,
     HLT>=95?color.new(color.green,tp*0):
     HLT>=90?color.new(color.green,tp*1):
     HLT>=85?color.new(color.green,tp*2):
     HLT>=80?color.new(color.green,tp*3):
     HLT>=75?color.new(color.green,tp*4):
     HLT>=70?color.new(color.green,tp*5):
     HLT>=65?color.new(color.green,tp*6):
     HLT>=60?color.new(color.green,tp*7):
     HLT>=55?color.new(color.green,tp*8):
     HLT>=50?color.new(color.green,tp*9):
     HLT>=45?color.new(color.red,tp*9):
     HLT>=40?color.new(color.red,tp*8):
     HLT>=35?color.new(color.red,tp*7):
     HLT>=30?color.new(color.red,tp*6):
     HLT>=25?color.new(color.red,tp*5):
     HLT>=20?color.new(color.red,tp*4):
     HLT>=15?color.new(color.red,tp*3):
     HLT>=10?color.new(color.red,tp*2):
     HLT>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))

GLlabel5=label.new(
     x=bar_index,y=5*10-5,
     text=" IND "+tostring(IND,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=IND>80?color.lime:IND<20?color.red:color.black,
     textalign = text.align_center,
     size=size.normal)
label.delete(GLlabel5[1])
label.new(
     x=bar_index,y=5*10-5,
     text=tostring(IND,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h5,h4,
     IND>=95?color.new(color.green,tp*0):
     IND>=90?color.new(color.green,tp*1):
     IND>=85?color.new(color.green,tp*2):
     IND>=80?color.new(color.green,tp*3):
     IND>=75?color.new(color.green,tp*4):
     IND>=70?color.new(color.green,tp*5):
     IND>=65?color.new(color.green,tp*6):
     IND>=60?color.new(color.green,tp*7):
     IND>=55?color.new(color.green,tp*8):
     IND>=50?color.new(color.green,tp*9):
     IND>=45?color.new(color.red,tp*9):
     IND>=40?color.new(color.red,tp*8):
     IND>=35?color.new(color.red,tp*7):
     IND>=30?color.new(color.red,tp*6):
     IND>=25?color.new(color.red,tp*5):
     IND>=20?color.new(color.red,tp*4):
     IND>=15?color.new(color.red,tp*3):
     IND>=10?color.new(color.red,tp*2):
     IND>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))

GLlabel4=label.new(
     x=bar_index,y=4*10-5,
     text=" MAT "+tostring(MAT,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=MAT>80?color.lime:MAT<20?color.red:color.black,
     textalign = text.align_center,
     size=size.normal)
label.delete(GLlabel4[1])
label.new(
     x=bar_index,y=4*10-5,
     text=tostring(MAT,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h4,h3,
     MAT>=95?color.new(color.green,tp*0):
     MAT>=90?color.new(color.green,tp*1):
     MAT>=85?color.new(color.green,tp*2):
     MAT>=80?color.new(color.green,tp*3):
     MAT>=75?color.new(color.green,tp*4):
     MAT>=70?color.new(color.green,tp*5):
     MAT>=65?color.new(color.green,tp*6):
     MAT>=60?color.new(color.green,tp*7):
     MAT>=55?color.new(color.green,tp*8):
     MAT>=50?color.new(color.green,tp*9):
     MAT>=45?color.new(color.red,tp*9):
     MAT>=40?color.new(color.red,tp*8):
     MAT>=35?color.new(color.red,tp*7):
     MAT>=30?color.new(color.red,tp*6):
     MAT>=25?color.new(color.red,tp*5):
     MAT>=20?color.new(color.red,tp*4):
     MAT>=15?color.new(color.red,tp*3):
     MAT>=10?color.new(color.red,tp*2):
     MAT>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))

GLlabel3=label.new(
     x=bar_index,y=3*10-5,
     text=" REI "+tostring(REI,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=REI>80?color.lime:REI<20?color.red:color.black,
     textalign = text.align_center,
     size=size.normal)
label.delete(GLlabel3[1])
label.new(
     x=bar_index,y=3*10-5,
     text=tostring(REI,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h3,h2,
     REI>=95?color.new(color.green,tp*0):
     REI>=90?color.new(color.green,tp*1):
     REI>=85?color.new(color.green,tp*2):
     REI>=80?color.new(color.green,tp*3):
     REI>=75?color.new(color.green,tp*4):
     REI>=70?color.new(color.green,tp*5):
     REI>=65?color.new(color.green,tp*6):
     REI>=60?color.new(color.green,tp*7):
     REI>=55?color.new(color.green,tp*8):
     REI>=50?color.new(color.green,tp*9):
     REI>=45?color.new(color.red,tp*9):
     REI>=40?color.new(color.red,tp*8):
     REI>=35?color.new(color.red,tp*7):
     REI>=30?color.new(color.red,tp*6):
     REI>=25?color.new(color.red,tp*5):
     REI>=20?color.new(color.red,tp*4):
     REI>=15?color.new(color.red,tp*3):
     REI>=10?color.new(color.red,tp*2):
     REI>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))

GLlabel2=label.new(
     x=bar_index,y=2*10-5,
     text=" TEC "+tostring(TEC,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=TEC>80?color.lime:TEC<20?color.red:color.black,
     textalign = text.align_center,
     size=size.normal)
label.delete(GLlabel2[1])
label.new(
     x=bar_index,y=2*10-5,
     text=tostring(TEC,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h2,h1,
     TEC>=95?color.new(color.green,tp*0):
     TEC>=90?color.new(color.green,tp*1):
     TEC>=85?color.new(color.green,tp*2):
     TEC>=80?color.new(color.green,tp*3):
     TEC>=75?color.new(color.green,tp*4):
     TEC>=70?color.new(color.green,tp*5):
     TEC>=65?color.new(color.green,tp*6):
     TEC>=60?color.new(color.green,tp*7):
     TEC>=55?color.new(color.green,tp*8):
     TEC>=50?color.new(color.green,tp*9):
     TEC>=45?color.new(color.red,tp*9):
     TEC>=40?color.new(color.red,tp*8):
     TEC>=35?color.new(color.red,tp*7):
     TEC>=30?color.new(color.red,tp*6):
     TEC>=25?color.new(color.red,tp*5):
     TEC>=20?color.new(color.red,tp*4):
     TEC>=15?color.new(color.red,tp*3):
     TEC>=10?color.new(color.red,tp*2):
     TEC>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))

GLlabel1=label.new(
     x=bar_index,y=1*10-5,
     text=" UTL "+tostring(UTL,"#"),
     style=label.style_label_left,color=color.new(color.white,transp=100),
     textcolor=UTL>80?color.lime:UTL<20?color.red:color.black,
     textalign = text.align_center,
     size=size.normal)
label.delete(GLlabel1[1])
label.new(
     x=bar_index,y=1*10-5,
     text=tostring(UTL,"#")+"        ",
     style=label.style_label_center,color=color.new(color.white,transp=100),
     textcolor=color.gray,
     textalign = text.align_left,
     size=size.tiny)
fill(h1,h0,
     UTL>=95?color.new(color.green,tp*0):
     UTL>=90?color.new(color.green,tp*1):
     UTL>=85?color.new(color.green,tp*2):
     UTL>=80?color.new(color.green,tp*3):
     UTL>=75?color.new(color.green,tp*4):
     UTL>=70?color.new(color.green,tp*5):
     UTL>=65?color.new(color.green,tp*6):
     UTL>=60?color.new(color.green,tp*7):
     UTL>=55?color.new(color.green,tp*8):
     UTL>=50?color.new(color.green,tp*9):
     UTL>=45?color.new(color.red,tp*9):
     UTL>=40?color.new(color.red,tp*8):
     UTL>=35?color.new(color.red,tp*7):
     UTL>=30?color.new(color.red,tp*6):
     UTL>=25?color.new(color.red,tp*5):
     UTL>=20?color.new(color.red,tp*4):
     UTL>=15?color.new(color.red,tp*3):
     UTL>=10?color.new(color.red,tp*2):
     UTL>=5?color.new(color.red,tp*1):
     color.new(color.red,tp*0))

```

#### Side-picture
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
