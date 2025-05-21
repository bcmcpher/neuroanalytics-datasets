# Programming Insanity

The following example(s) walk through solving challenges that have
come up for scholars. The goal is less to provide specific solutions
to problems, but more to help establish how you can

## Same function, different answers?

A scholar encountered a puzzling issue. They were comparing different
tools, one in MATLAB and the other in Python. However, the tools were
supposedly doing the same thing: compute the spectram of an input
dataset.

Fortunately, this is a standard data manipulation and is readily
available in both software environments:
- `spectrogram` in MATLAB
- `specgram` in python scipy (and MNE)

Unfortunately, the analysis that's using the same operation on the
same inputs but with different software. So what gives?

### First: Check your assumptions

Despite doing the "same thing", clearly these functions do something
different.

Fortunately, it was pretty quick to identify what function was not
performing as expected. The fastest way to see what's going on is to
check the inline help.

specgram
```
Compute a spectrogram with consecutive Fourier transforms (legacy function).

Spectrograms can be used as a way of visualizing the change of a
nonstationary signal’s frequency content over time.

Parameters:

xarray_like

Time series of measurement values
	fsfloat, optional

Sampling frequency of the x time series. Defaults to 1.0.
	windowstr or tuple or array_like, optional

Desired window to use. If window is a string or tuple, it is passed to get_window to generate the window values, which are DFT-even by default. See get_window for a list of windows and required parameters. If window is array_like it will be used directly as the window and its length must be nperseg. Defaults to a Tukey window with shape parameter of 0.25.
	npersegint, optional

Length of each segment. Defaults to None, but if window is str or tuple, is set to 256, and if window is array_like, is set to the length of the window.
	noverlapint, optional

Number of points to overlap between segments. If None, noverlap = nperseg // 8. Defaults to None.
	nfftint, optional

Length of the FFT used, if a zero padded FFT is desired. If None, the FFT length is nperseg. Defaults to None.
	detrendstr or function or False, optional

Specifies how to detrend each segment. If detrend is a string, it is passed as the type argument to the detrend function. If it is a function, it takes a segment and returns a detrended segment. If detrend is False, no detrending is done. Defaults to ‘constant’.
	return_onesidedbool, optional

If True, return a one-sided spectrum for real data. If False return a two-sided spectrum. Defaults to True, but for complex data, a two-sided spectrum is always returned.
	scaling{ ‘density’, ‘spectrum’ }, optional

Selects between computing the power spectral density (‘density’) where Sxx has units of V**2/Hz and computing the power spectrum (‘spectrum’) where Sxx has units of V**2, if x is measured in V and fs is measured in Hz. Defaults to ‘density’.
	axisint, optional

Axis along which the spectrogram is computed; the default is over the last axis (i.e. axis=-1).
	modestr, optional

Defines what kind of return values are expected. Options are [‘psd’, ‘complex’, ‘magnitude’, ‘angle’, ‘phase’]. ‘complex’ is equivalent to the output of stft with no padding or boundary extension. ‘magnitude’ returns the absolute magnitude of the STFT. ‘angle’ and ‘phase’ return the complex angle of the STFT, with and without unwrapping, respectively.

Returns

f
	ndarray

Array of sample frequencies.
	t
	ndarray

Array of segment times.
	Sxx
	ndarray

Spectrogram of x. By default, the last axis of Sxx corresponds to the segment times.
```

spectrogram
```
s = spectrogram(x)
s = spectrogram(x,window)
s = spectrogram(x,window,noverlap)
s = spectrogram(x,window,noverlap,nfft)
[s,w,t] = spectrogram(___)
[s,f,t] = spectrogram(___,fs)
[s,w,t] = spectrogram(x,window,noverlap,w)
[s,f,t] = spectrogram(x,window,noverlap,f,fs)
[___,ps] = spectrogram(___,spectrumtype)
[___] = spectrogram(___,"reassigned")
[___,ps,fc,tc] = spectrogram(___)
[___] = spectrogram(___,freqrange)
[___] = spectrogram(___,Name=Value)
spectrogram(___)
spectrogram(___,freqloc)
Description

s = spectrogram(x) returns the Short-Time Fourier Transform (STFT) of the input signal x. Each column of s contains an estimate of the short-term, time-localized frequency content of x. The magnitude squared of s is known as the spectrogram time-frequency representation of x [1].

example

s = spectrogram(x,window) uses window to divide the signal into segments and perform windowing.

example

s = spectrogram(x,window,noverlap) uses noverlap samples of overlap between adjoining segments.

example

s = spectrogram(x,window,noverlap,nfft) uses nfft sampling points to calculate the discrete Fourier transform.

example

[s,w,t] = spectrogram(___) returns a vector of normalized frequencies, w, and a vector of time instants, t, at which the STFT is computed. This syntax can include any combination of input arguments from previous syntaxes.

example

[s,f,t] = spectrogram(___,fs) returns a vector of cyclical frequencies, f, expressed in terms of the sample rate fs. fs must be the fifth input to spectrogram. To input a sample rate and still use the default values of the preceding optional arguments, specify these arguments as empty, [].

example

[s,w,t] = spectrogram(x,window,noverlap,w) returns the STFT at the normalized frequencies specified in w. w must have at least two elements, because otherwise the function interprets it as nfft.

example

[s,f,t] = spectrogram(x,window,noverlap,f,fs) returns the STFT at the cyclical frequencies specified in f. f must have at least two elements, because otherwise the function interprets it as nfft.

example

[___,ps] = spectrogram(___,spectrumtype) also returns a matrix, ps, proportional to the spectrogram of x.

	If you specify spectrumtype as "psd", each column of ps contains an estimate of the power spectral density (PSD) of a windowed segment.

	If you specify spectrumtype as "power", each column of ps contains an estimate of the power spectrum of a windowed segment.

example

[___] = spectrogram(___,"reassigned") reassigns each PSD or power spectrum estimate to the location of its center of energy. If your signal contains well-localized temporal or spectral components, then this option generates a sharper spectrogram.

example

[___,ps,fc,tc] = spectrogram(___) also returns two matrices, fc and tc, containing the frequency and time of the center of energy of each PSD or power spectrum estimate.

example

[___] = spectrogram(___,freqrange) returns the PSD or power spectrum estimate over the frequency range specified by freqrange. Valid options for freqrange are "onesided", "twosided", and "centered".

example

[___] = spectrogram(___,Name=Value) specifies additional options using name-value arguments. Options include the minimum threshold and output time dimension.

example

spectrogram(___) with no output arguments plots ps in decibels in the current figure window.

example

spectrogram(___,freqloc) specifies the axis on which to plot the
frequency.
```
We can now compare what the default behavior in each tool is coded to
be.

#### Solution: They do something different by default

In python, `specgram` by default returns the *power spectral density*
(mode='PSD'). In MATLAB, `spectrogram` by default returns the
*short-time fourier transform*.

This explains pretty clearly why the results are different - the tools
aren't doing the same thing!

- To get the python defaults in MATLAB, set `nargout==4` to get it to
compute the PSD.
- To get the MATLAB defaults in python, set `mode='complex'`

This additional insight into what you're *actually* doing will
hopefully help you make more informed decisions and understand what
your analysis is actually able to tell you.

### References

https://stackoverflow.com/questions/31101987/different-spectrogram-between-matlab-and-python

https://dsp.stackexchange.com/questions/87084/scipy-and-matlab-spectrogram-not-matching

https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.spectrogram.html

https://www.mathworks.com/help/signal/ref/spectrogram.html
