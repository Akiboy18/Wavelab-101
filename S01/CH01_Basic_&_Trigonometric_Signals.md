
# **CH01 \- Basic & Trigonometric Signals**
# **Common signals**

In signal processing, these four signals—**Impulse, Step, Ramp, and Sine**—are considered "standard test signals" because they are the simplest mathematical models for the most common real\-world physical forces. 


They act as "stress tests" for a system, allowing engineers to predict how a device will handle sudden shocks, steady changes, or constant vibrations without having to test every possible scenario


 **Unit Impulse Signal** 


The Unit Impulse models a **sudden, instantaneous impact** or "shock" to a system, like a hammer hitting a bell or a lightning strike on a power line. 


Commonly called the ***Dirac Delta function***, this is a theoretical signal that is infinitely high and thin but has an area of exactly **1**.


![image_0.png](./CH01_Basic_&_Trigonometric_Signals_media/image_0.png)


**Behavior:** It exists only at ![image_1.gif](./CH01_Basic_&_Trigonometric_Signals_media/image_1.gif)![image_2.gif](./CH01_Basic_&_Trigonometric_Signals_media/image_2.gif)**t = 0** and is zero everywhere else.


**Purpose:** It reveals the "Impulse Response," which is the "DNA" of a system. If you know how a system reacts to an impulse, you can mathematically predict how it will react to *any* other input through a process called convolution.

```matlab
t = -1:0.001:1;
delta = (t == 0);

plot(t, delta);

title('Unit Impulse Signal');
grid on;
```

![figure_0.png](./CH01_Basic_&_Trigonometric_Signals_media/figure_0.png)

###  **Unit Step Signal** 

The Unit Step models a **sudden change that stays constant**, like flipping a light switch or a thermostat turning on a heater.


![image_3.png](./CH01_Basic_&_Trigonometric_Signals_media/image_3.png)


**Behavior:** It is ![image_4.gif](./CH01_Basic_&_Trigonometric_Signals_media/image_4.gif)0 for all time before![image_5.gif](./CH01_Basic_&_Trigonometric_Signals_media/image_5.gif)![image_6.gif](./CH01_Basic_&_Trigonometric_Signals_media/image_6.gif)t = 0, and jumps to exactly **1** for all time after t = 0![image_7.gif](./CH01_Basic_&_Trigonometric_Signals_media/image_7.gif)![image_8.gif](./CH01_Basic_&_Trigonometric_Signals_media/image_8.gif). 


**Purpose:** It is used to test the **stability** and settling time of a system (how long it takes to react to a sudden change). 


It is used to analyze **Transient Response**. It shows how much a system "overshoots" its target and how long it takes to settle down (stability).

```matlab
t = -5:0.01:5;
u = t >= 0;

plot(t, u, 'LineWidth', 2);
grid on;
title('Unit Step Signal');
xlabel('Time');
ylabel('Amplitude');
```

![figure_1.png](./CH01_Basic_&_Trigonometric_Signals_media/figure_1.png)


**Unit Ramp Signal**


A ramp signal represents a constant change over time, like an airplane steadily gaining altitude.


![image_9.png](./CH01_Basic_&_Trigonometric_Signals_media/image_9.png)


**Behavior:** It is ![image_10.gif](./CH01_Basic_&_Trigonometric_Signals_media/image_10.gif)0 before t = 0![image_11.gif](./CH01_Basic_&_Trigonometric_Signals_media/image_11.gif)![image_12.gif](./CH01_Basic_&_Trigonometric_Signals_media/image_12.gif), and then increases linearly forever.


**Purpose:** It tests the system's ability to track a moving target. It helps engineers find "steady\-state error"—basically, how far behind the system falls when trying to keep up with a constant change.

```matlab
t = -5:0.01:5;
r = t .* (t >= 0);

plot(t, r, 'LineWidth', 2);
grid on;
title('Ramp Signal');
xlabel('Time');
ylabel('Amplitude');
```

![figure_2.png](./CH01_Basic_&_Trigonometric_Signals_media/figure_2.png)

### Sinusoidal Signal 

The most common real\-world signal, found in everything from sound waves to the AC power in your walls.


![image_13.png](./CH01_Basic_&_Trigonometric_Signals_media/image_13.png)


**Behavior:** It oscillates smoothly and periodically between positive and negative peaks.


**Purpose:** It is the foundation of **Frequency Analysis** (Fourier Transforms). Every complex signal can be broken down into a collection of sine waves.

```matlab
t = 0:0.1:9*3.14
```

```matlabTextOutput
t = 1x283
         0    0.1000    0.2000    0.3000    0.4000    0.5000    0.6000    0.7000    0.8000    0.9000    1.0000    1.1000    1.2000    1.3000    1.4000    1.5000    1.6000    1.7000    1.8000    1.9000    2.0000    2.1000    2.2000    2.3000    2.4000    2.5000    2.6000    2.7000    2.8000    2.9000    3.0000    3.1000    3.2000    3.3000    3.4000    3.5000    3.6000    3.7000    3.8000    3.9000    4.0000    4.1000    4.2000    4.3000    4.4000    4.5000    4.6000    4.7000    4.8000    4.9000

```

```matlab
y = sin(t)
```

```matlabTextOutput
y = 1x283
         0    0.0998    0.1987    0.2955    0.3894    0.4794    0.5646    0.6442    0.7174    0.7833    0.8415    0.8912    0.9320    0.9636    0.9854    0.9975    0.9996    0.9917    0.9738    0.9463    0.9093    0.8632    0.8085    0.7457    0.6755    0.5985    0.5155    0.4274    0.3350    0.2392    0.1411    0.0416   -0.0584   -0.1577   -0.2555   -0.3508   -0.4425   -0.5298   -0.6119   -0.6878   -0.7568   -0.8183   -0.8716   -0.9162   -0.9516   -0.9775   -0.9937   -0.9999   -0.9962   -0.9825

```

```matlab
plot(t,y)
xlabel('Time (s)');
ylabel('Amplitude');
title('Sinusoidal Wave');
grid on;
```

![figure_3.png](./CH01_Basic_&_Trigonometric_Signals_media/figure_3.png)

## **Basic Trigonometric Signals**

1. **Degrees**


Degrees are based on tradition. We decided a full circle is 360°. Why 360? It's a "friendly" number—highly divisible by 2, 3, 4, 5, 6, 8, 9, 10, and 12.


![image_14.png](./CH01_Basic_&_Trigonometric_Signals_media/image_14.png)


Mental Image: Think of a compass or a clock. A right angle is 90°, and a straight line is 180°. 


2. **Radians**


Radians are based on the actual geometry of the circle. **One radian is the angle created when you take the radius of a circle and wrap it around the edge (the arc)**. 


![image_15.png](./CH01_Basic_&_Trigonometric_Signals_media/image_15.png)


The Math: Since the circumference of a circle is 2\*pi\*r, there are exactly 2\*pi radians in a full circle.


Mental Image: If you walked a distance equal to the radius along the curve of a circle, the angle you've covered is exactly 1 radian. 


![image_16.png](./CH01_Basic_&_Trigonometric_Signals_media/image_16.png)

```matlab
t = 0:0.1:5*3.14
```

```matlabTextOutput
t = 1x158
         0    0.1000    0.2000    0.3000    0.4000    0.5000    0.6000    0.7000    0.8000    0.9000    1.0000    1.1000    1.2000    1.3000    1.4000    1.5000    1.6000    1.7000    1.8000    1.9000    2.0000    2.1000    2.2000    2.3000    2.4000    2.5000    2.6000    2.7000    2.8000    2.9000    3.0000    3.1000    3.2000    3.3000    3.4000    3.5000    3.6000    3.7000    3.8000    3.9000    4.0000    4.1000    4.2000    4.3000    4.4000    4.5000    4.6000    4.7000    4.8000    4.9000

```

```matlab
y = sin(t)
```

```matlabTextOutput
y = 1x158
         0    0.0998    0.1987    0.2955    0.3894    0.4794    0.5646    0.6442    0.7174    0.7833    0.8415    0.8912    0.9320    0.9636    0.9854    0.9975    0.9996    0.9917    0.9738    0.9463    0.9093    0.8632    0.8085    0.7457    0.6755    0.5985    0.5155    0.4274    0.3350    0.2392    0.1411    0.0416   -0.0584   -0.1577   -0.2555   -0.3508   -0.4425   -0.5298   -0.6119   -0.6878   -0.7568   -0.8183   -0.8716   -0.9162   -0.9516   -0.9775   -0.9937   -0.9999   -0.9962   -0.9825

```

```matlab
plot(t,y)
xlabel('Time (s)');
ylabel('Amplitude');
title('Sine Wave');
grid on;
```

![figure_4.png](./CH01_Basic_&_Trigonometric_Signals_media/figure_4.png)

```matlab

t = 0:0.1:5*3.14
```

```matlabTextOutput
t = 1x158
         0    0.1000    0.2000    0.3000    0.4000    0.5000    0.6000    0.7000    0.8000    0.9000    1.0000    1.1000    1.2000    1.3000    1.4000    1.5000    1.6000    1.7000    1.8000    1.9000    2.0000    2.1000    2.2000    2.3000    2.4000    2.5000    2.6000    2.7000    2.8000    2.9000    3.0000    3.1000    3.2000    3.3000    3.4000    3.5000    3.6000    3.7000    3.8000    3.9000    4.0000    4.1000    4.2000    4.3000    4.4000    4.5000    4.6000    4.7000    4.8000    4.9000

```

```matlab
y = cos(t)
```

```matlabTextOutput
y = 1x158
1.0000    0.9950    0.9801    0.9553    0.9211    0.8776    0.8253    0.7648    0.6967    0.6216    0.5403    0.4536    0.3624    0.2675    0.1700    0.0707   -0.0292   -0.1288   -0.2272   -0.3233   -0.4161   -0.5048   -0.5885   -0.6663   -0.7374   -0.8011   -0.8569   -0.9041   -0.9422   -0.9710   -0.9900   -0.9991   -0.9983   -0.9875   -0.9668   -0.9365   -0.8968   -0.8481   -0.7910   -0.7259   -0.6536   -0.5748   -0.4903   -0.4008   -0.3073   -0.2108   -0.1122   -0.0124    0.0875    0.1865

```

```matlab
plot(t,y)
xlabel('Time (s)');
ylabel('Amplitude');
title('Cosine Wave');
grid on;
```

![figure_5.png](./CH01_Basic_&_Trigonometric_Signals_media/figure_5.png)

```matlab

t = 0:0.1:5*3.14
```

```matlabTextOutput
t = 1x158
         0    0.1000    0.2000    0.3000    0.4000    0.5000    0.6000    0.7000    0.8000    0.9000    1.0000    1.1000    1.2000    1.3000    1.4000    1.5000    1.6000    1.7000    1.8000    1.9000    2.0000    2.1000    2.2000    2.3000    2.4000    2.5000    2.6000    2.7000    2.8000    2.9000    3.0000    3.1000    3.2000    3.3000    3.4000    3.5000    3.6000    3.7000    3.8000    3.9000    4.0000    4.1000    4.2000    4.3000    4.4000    4.5000    4.6000    4.7000    4.8000    4.9000

```

```matlab
y = tan(t)
```

```matlabTextOutput
y = 1x158
         0    0.1003    0.2027    0.3093    0.4228    0.5463    0.6841    0.8423    1.0296    1.2602    1.5574    1.9648    2.5722    3.6021    5.7979   14.1014  -34.2325   -7.6966   -4.2863   -2.9271   -2.1850   -1.7098   -1.3738   -1.1192   -0.9160   -0.7470   -0.6016   -0.4727   -0.3555   -0.2464   -0.1425   -0.0416    0.0585    0.1597    0.2643    0.3746    0.4935    0.6247    0.7736    0.9474    1.1578    1.4235    1.7778    2.2858    3.0963    4.6373    8.8602   80.7128  -11.3849   -5.2675

```

```matlab
plot(t,y)
xlabel('Time (s)');
ylabel('Amplitude');
title('Tan Wave');
grid on;
```

![figure_6.png](./CH01_Basic_&_Trigonometric_Signals_media/figure_6.png)

```matlab

t = 0:0.1:5*3.14
```

```matlabTextOutput
t = 1x158
         0    0.1000    0.2000    0.3000    0.4000    0.5000    0.6000    0.7000    0.8000    0.9000    1.0000    1.1000    1.2000    1.3000    1.4000    1.5000    1.6000    1.7000    1.8000    1.9000    2.0000    2.1000    2.2000    2.3000    2.4000    2.5000    2.6000    2.7000    2.8000    2.9000    3.0000    3.1000    3.2000    3.3000    3.4000    3.5000    3.6000    3.7000    3.8000    3.9000    4.0000    4.1000    4.2000    4.3000    4.4000    4.5000    4.6000    4.7000    4.8000    4.9000

```

```matlab
y = cot(t)
```

```matlabTextOutput
y = 1x158
       Inf    9.9666    4.9332    3.2327    2.3652    1.8305    1.4617    1.1872    0.9712    0.7936    0.6421    0.5090    0.3888    0.2776    0.1725    0.0709   -0.0292   -0.1299   -0.2333   -0.3416   -0.4577   -0.5848   -0.7279   -0.8935   -1.0917   -1.3386   -1.6622   -2.1154   -2.8127   -4.0584   -7.0153  -24.0288   17.1017    6.2599    3.7833    2.6696    2.0265    1.6007    1.2927    1.0555

```

```matlab
plot(t,y)
xlabel('Time (s)');
ylabel('Amplitude');
title('Cot Wave');
grid on;
```

![figure_7.png](./CH01_Basic_&_Trigonometric_Signals_media/figure_7.png)

```matlab

t = 0:0.1:5*3.14
```

```matlabTextOutput
t = 1x158
         0    0.1000    0.2000    0.3000    0.4000    0.5000    0.6000    0.7000    0.8000    0.9000    1.0000    1.1000    1.2000    1.3000    1.4000    1.5000    1.6000    1.7000    1.8000    1.9000    2.0000    2.1000    2.2000    2.3000    2.4000    2.5000    2.6000    2.7000    2.8000    2.9000    3.0000    3.1000    3.2000    3.3000    3.4000    3.5000    3.6000    3.7000    3.8000    3.9000    4.0000    4.1000    4.2000    4.3000    4.4000    4.5000    4.6000    4.7000    4.8000    4.9000

```

```matlab
y = sec(t)
```

```matlabTextOutput
y = 1x158
1.0000    1.0050    1.0203    1.0468    1.0857    1.1395    1.2116    1.3075    1.4353    1.6087    1.8508    2.2046    2.7597    3.7383    5.8835   14.1368  -34.2471   -7.7613   -4.4014   -3.0932   -2.4030   -1.9808   -1.6992   -1.5009   -1.3561   -1.2482   -1.1670   -1.1061   -1.0613   -1.0299   -1.0101   -1.0009   -1.0017   -1.0127   -1.0343   -1.0679   -1.1151   -1.1791   -1.2643   -1.3775   -1.5299   -1.7397   -2.0397   -2.4950   -3.2538   -4.7439   -8.9164  -80.7190   11.4287    5.3616

```

```matlab
plot(t,y)
xlabel('Time (s)');
ylabel('Amplitude');
title('Sec Wave');
grid on;
```

![figure_8.png](./CH01_Basic_&_Trigonometric_Signals_media/figure_8.png)

```matlab

t = 0:0.1:5*3.14
```

```matlabTextOutput
t = 1x158
         0    0.1000    0.2000    0.3000    0.4000    0.5000    0.6000    0.7000    0.8000    0.9000    1.0000    1.1000    1.2000    1.3000    1.4000    1.5000    1.6000    1.7000    1.8000    1.9000    2.0000    2.1000    2.2000    2.3000    2.4000    2.5000    2.6000    2.7000    2.8000    2.9000    3.0000    3.1000    3.2000    3.3000    3.4000    3.5000    3.6000    3.7000    3.8000    3.9000    4.0000    4.1000    4.2000    4.3000    4.4000    4.5000    4.6000    4.7000    4.8000    4.9000

```

```matlab
y = 1./sin(t);
plot(t,y)
xlabel('Time (s)');
ylabel('Amplitude');
title('Cosec Wave');
grid on;
```

![figure_9.png](./CH01_Basic_&_Trigonometric_Signals_media/figure_9.png)
