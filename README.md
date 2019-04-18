# Fast_Fourier_Transform

The script parses the sensor data files and subsequently performs FFT to observe the temporal trends in the respiratory rates.


## Introduction

Fourier analysis converts a signal from its time domain to a representation in the frequency domain and vice versa. Fast Fourier transforms are widely used for applications in engineering, science, and mathematics. The basic ideas were popularized in 1965, but some algorithms had been derived as early as 1805.

## Description

To demonstrate inner workings of our code, we will use a sample file (****sample_sensor_data.txt****).

<p align="center">
  <img width="600" height="400" src="https://github.com/rcvenkata/Fast_Fourier_Transform/blob/master/Screenshot%20from%202019-04-17%2019-14-08.png">
</p>


In the above image, you can see that the entries within the variables are placed at regular intervals with a sampling frequency of ~50 samples/sec. The script will remove all the variables except respiratory ('rresp') and time ('timestamp') variables. Subsequently, it decodes the time variable to seconds with a starting entry at 0 seconds, to make it more meaningful. A arbitary plot illustrating time vs amplitude of the signal is saved (as ****Raw_signal_figure.pdf****) in the working directory. The below is the plot generated by the script for our sample dataset.


<p align="center">
  <img width="400" height="400" src="https://github.com/rcvenkata/Fast_Fourier_Transform/blob/master/Raw_signal_figure.png">
</p>


Importantly, the sensor data needs to preprocessed due to the presence of noise within the data. First, lets use a sliding window approach where each window/batch comprises of 1500 samples (corresponds to approx 30 seconds). Now we move the window one sample at a time (i.e., we discard the first sample of the previous window to include a new sample for the current window). 


<p align="center">
  <img width="300" height="300" src="https://github.com/rcvenkata/Fast_Fourier_Transform/blob/master/proxy.duckduckgo.com.jpeg">
</p>

Each window of respiratory signals are rescaled using mean-centering. Therafter, Discrete Fourier Transform is applied on each window to identify dominant frequency. The obtained dominant frequencies across all windows are plotted against their corresponding times in seconds. The resultant plot is again saved (as ****Dominant_Frequency_across_time_plot.pdf****) in the working directory. The below plot represents the time in seconds vs frequencies (Hz) for our sample dataset. 

<p align="center">
  <img width="500" height="500" src="https://github.com/rcvenkata/Fast_Fourier_Transform/blob/master/Dominant_frequency_across_time_plot.png">
</p>


## Usage

#### 1. Download the file using the below code in the terminal
```
$ git clone https://github.com/rcvenkata/Fast_Fourier_Transform.git

```

#### 2. Change directory
```
$ cd Fast_Fourier_Transform/

```

#### 3. Run the script on the accompanying sample dataset (****sample_sensor_data.txt****).
```
$ cat sample_sensor_data.txt | script.sh

```


## References

https://en.wikipedia.org/wiki/Fast_Fourier_transform
