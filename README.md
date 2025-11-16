# Frequency-Modulation-and-Demodulation-using-NumPy-and-Matplotlib
### AIM
    To implement and analyze frequency modulation (FM) using Python's NumPy and Matplotlib libraries.   
### APPARATUS REQUIRED
1.	Software: Python with NumPy and Matplotlib libraries  
2.	Hardware: Personal Computer  
### THEORY 
Frequency Modulation (FM) is a method of transmitting information over a carrier wave by varying its frequency in accordance with the amplitude of the input signal (message signal). The frequency of the carrier wave is varied according to the instantaneous amplitude of the message signal. The general form of an FM signal is:


<img width="508" height="200" alt="image" src="https://github.com/user-attachments/assets/d69f6e8c-de84-4ee7-886b-0dc349407e29" />


### ALGORITHM

1.	Initialize Parameters: Set the values for carrier frequency, message frequency, sampling frequency, and frequency deviation.    
2.	Generate Time Axis: Create a time vector for the signal duration.  
3.	Generate Message Signal: Define the message signal as a cosine wave.  
4.	Compute the Integral of the Message Signal: Calculate the integral of the message signal over time.  
5.	Generate FM Signal: Apply the FM modulation formula to obtain the modulated signal.  
6.	Plot the Signals: Use Matplotlib to plot the message signal, carrier signal, and modulated signal.

### PROGRAM
```
Am = 7;
fm = 653;
fs = 65300;
Ac = 14;
fc = 6530;
b = 4;
t = 0:1/fs:2/fm;
m = Am * cos(2 * 3.14 * fm * t);
c = Ac * cos(2 * 3.14 * fc * t);
s = Ac * cos(2 * 3.14 * fc * t + b * sin(2 * 3.14 * fm * t));
subplot(4,1,1);
plot(t, m);
xlabel("Time (s)");
ylabel("Amplitude");
title("Message Signal");
xgrid();
subplot(4,1,2);
plot(t, c);
xlabel("Time (s)");
ylabel("Amplitude");
title("Carrier Signal");
xgrid();
subplot(4,1,3);
plot(t, s);
xlabel("Time (s)");
ylabel("Amplitude");
title("Frequency Modulated Signal");
xgrid();
ds = diff(s);
analytic_signal = hilbert(ds);
envelope = abs(analytic_signal);
demod = envelope - mean(envelope);
demod = demod / max(abs(demod)) * Am;
subplot(4,1,4);
plot(t(1:$-1), demod);
xlabel("Time (s)");
ylabel("Amplitude");
title("Demodulated Signal (Recovered Message)");
xgrid();

```
### TABULATION
![8a4ee392-b29e-474b-8653-33c55e2faa1f](https://github.com/user-attachments/assets/e0f3f95c-b8d3-4e83-94d7-1956f2dc32a2)

### OUTPUT
<img width="692" height="576" alt="image" src="https://github.com/user-attachments/assets/533fef5a-647c-4e2c-97ed-68b9e5cacb6b" />
 
### RESULT
The message signal, carrier signal, and frequency modulated (FM) signal will be displayed in separate plots. The modulated signal will show frequency variations corresponding to the amplitude of the message signal.
