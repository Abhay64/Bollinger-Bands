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

