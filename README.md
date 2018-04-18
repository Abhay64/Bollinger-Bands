# Bollinger Bands
Bollinger Bands shows the levels of different highs and lows that a security price has reached in a particular duration.
# Prequisites
* python 3.6
* pandas
* numpy
* math
* matplotlib
# What is Bollinger Band
Bollinger Bands encapsulate the price movement of a stock. It provides relative boundaries of highs and lows. The crux of the Bollinger Band indicator is based on a moving average that defines the intermediate-term "trend" based on the time frame you are viewing.

This trend indicator is known as the middle band. Most stock charting applications use a 20-period moving average for the default Bollinger Bands settings. The upper and lower bands are then a measure of volatility to the upside and downside. They are calculated as two standard deviations from the middle band.
# How it Works
Bollinger Bands are volatility bands placed above and below a moving average. Volatility is based on the standard deviation, which changes as volatility increases and decreases. The bands automatically widen when volatility increases and narrow when volatility decreases. This dynamic nature of Bollinger Bands also means they can be used on different securities with the standard settings. For signals, Bollinger Bands can be used to identify M-Tops and W-Bottoms or to determine the strength of the trend.
When the markets become more volatile, the bands widen; during less volatile periods, the bands contract.
# Mathematical Description
Bollinger Bands indicator is calculated in three steps:
* Calculate the Middle Band according to the SMA formula
<p align="center"> 
<img src="https://user-images.githubusercontent.com/26857440/38905476-8bedd2e0-42ce-11e8-8ca8-200360f87175.PNG"></p>

20 days are default period for bollinger band.
* Calculate the Standard Deviation
<p align="center"> 
<img src="https://user-images.githubusercontent.com/26857440/38906129-51865a74-42d2-11e8-923c-d9bda537fdfd.PNG"></p>

n is the period for finding standard deviation here it is 20.
* Calculate Upper and Lower Band

**Upper Band**
<p align="center"> 
<img src="https://user-images.githubusercontent.com/26857440/38905781-5eab6598-42d0-11e8-8c60-7fa4ae0e73c9.PNG"></p>

**Lower Band**
<p align="center"> 
<img src="https://user-images.githubusercontent.com/26857440/38905804-7b07cd08-42d0-11e8-860c-b1ab2d409bff.PNG"></p>

# Implementing Bollinger Bands
**Importing Data**
```python
#Importing important libraries
import pandas as pd
import numpy as np
import math
from matplotlib import pyplot as plt
df = pd.read_csv('Put Your CSV File Here!!!')
# converting from UNIX timestamp to normal
array_date = np.array(df['date'])
array_close = np.array(df['close'])
array_open = np.array(df['open'])
array_high = np.array(df['high'])
array_low = np.array(df['low'])
array_volume = np.array(df['volume'])
print("High Array size",array_high.size)
print("Low Array size",array_low.size)
print("Open Array size",array_open.size)
print("Close Array size",array_close.size)
```
**Finding Middle Band with Bperiods**
```python
Bperiods=19 # Bperiods are 20 array start with 0 index
y=0
array_Middleband=[None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None]
for x in range(0,array_close.size-Bperiods):
	sum=0
	for j in range(0,Bperiods+1): #upto 20 periods value
		z=array_close[y]
		sum=sum+z
		y=y+1
	print(sum)
	sum=sum/20
	print(sum)
	array_Middleband.append(sum)
	y=y-(Bperiods)
print(len(array_Middleband))
print(array_Middleband)
```
**Finding Standard Deviation**
```python
stndrd_deviation=[None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None]
y=0
z=0
# taking periods for counting SD equal Bperiods
for x in range(0,array_close.size-Bperiods):
	sum=0
	for j in range(0,Bperiods+1): #upto 20 periods value
		z=array_Middleband[x+Bperiods]
		sum=sum+((z-array_close[y])*(z-array_close[y]))
		y=y+1
	print(sum)
	sum=sum/19
	sum=math.sqrt(sum)
	print(sum)
	stndrd_deviation.append(sum)
	y=y-(Bperiods)
print(len(stndrd_deviation))
print(stndrd_deviation)
```
**Finding Upper and Lower Bands**
```python
upper_band=[None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None]
lower_band=[None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None,None]
for x in range(Bperiods,len(stndrd_deviation)-1):
	upper_band.append(array_Middleband[x]+(2*stndrd_deviation[x]))
	lower_band.append(array_Middleband[x]-(2*stndrd_deviation[x]))
print(upper_band)
print(len(upper_band))
print(lower_band)
```
**Output**
```python
# Visualising the result
plt.plot(array_close,color='blue',label = 'close')
plt.plot(upper_band,color='red',label = 'Upper Band')
plt.plot(lower_band,color='green',label = 'lower Band')
plt.plot(array_Middleband,color='orange',label = 'Middle Band')
df['date'] = df['date'].reset_index()
x=df['date'].index
labels = array_date[0:]
plt.xticks(x, labels, rotation = 'vertical')
plt.ylabel('Bollinger_Bands')
plt.xlabel('dates')
plt.legend()
plt.show()
```
<p align="center"> 
<img src="https://user-images.githubusercontent.com/26857440/38933752-843cb5ca-4337-11e8-98ce-ccabbc2c4b22.PNG"></p>
<p align="center"> 
<img src="https://user-images.githubusercontent.com/26857440/38933857-c8069f78-4337-11e8-98ab-8602616e0dc1.PNG"></p>