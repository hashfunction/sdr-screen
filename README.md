# Deeplearning SDR

In this notebook, we'll try and see if we can determine what is shown on the monitor screen based only on the leaked EM radiation as captured by an rtl-sdr device.

Theoretically, the leaked signals contain all the data we need to determine whats displayed. Its possible the resolution of signals is not high enough to capture every pixel worth of data and we need a better rtl-sdr device. To start off, we'll attempt to display 4 different images on the screen, collect the leaky signals and then attempt to predict the image based solely on the signals.

## Summary

The data collection took most of the time. I collected the data in a 'noisy' environment with many other electronic devices leaking signals so as to not make the task too easy.  

The overall accuracy I was able to attain was just over 98% in the test set. This looks promising and points to a strong correlation between the leaked signals and the images displayed on the monitor. 

## Assets

* [Jupyter Notebook Output](http://htmlpreview.github.io/?https://github.com/hashfunction/sdr-screen/blob/master/SDR_Video_Detection.html)
* [Jupyter Notebook](SDR_Video_Detection.ipynb)
* [Sample Data](data/)

### Further steps and investigations

From the analysis above, its clear that the network had some trouble picking up on the patterns as can be seen by the very high number of epochs needed to get a good result. Still we were able to achieve > 98% accuracy from our testing set which implies a strong correlation between the signals collected and the image displayed on the video. 

Some next steps are outlined below. 

* Gather more data. This will give us a better gauge of the effectiveness of the model. 
* Look at the failed cases in more detail and see if we can spot the issues there.
* We could increase the number of images from 4 to a grid of 32 in checkerboard pattern with various boxes turned black or white. This would enable us to start gauging the fidelity of data collected.
* Drop the monitor resolution really low to 320x200 and then display random noise and collect the signal. Try and train the model and see if we can truly 'see' what the monitor is displaying purely from the leaky signals. 
