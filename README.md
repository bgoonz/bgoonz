


---

# Hi, I am Bryan!



<div style=" border: 1px solid black">
<img align="center" src="https://github.com/bgoonz/bgoonz/blob/master/circle-small-sharp.png?raw=true?raw=true" ></img> 
</div>







---

<img src="https://readme-jokes.vercel.app/api" stye="width:500; height:320;">

#### Refresh the page for a new joke!



---



[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=bgoonz&langs_count=8&show_icons=true&theme=radical)](https://github.com/bgoonz)
[![trophy](https://github-profile-trophy.vercel.app/?username=bgoonz&theme=onedark)](https://github.com/ryo-ma/github-profile-trophy)


---

[Hi I'm Bryan!](#hi-im-bryan)
- [ ] ✅ [Portfolio:](#portfolio)
- [ ] ✅- [OR:](#or)
- [ ] ✅ [Github-Pages](#github-pages)re
- [ ] ✅ [Github Gists](#github-gists)
- [ ] ✅ [Web Dev Resource Hub](#web-dev-resource-hub)
- [ ] ✅ [Mihir\_Beg.com](#mihir_begcom)
- [ ] ✅ [Interview Prep Static Site](#interview-prep-static-site)
- [ ] ✅ [Data Structures Repository](#data-structures-repository)
- [ ] ✅ [Learning React Blog](#learning-react-blog)
- [ ] ✅ [React Repo:](#react-repo)
- [ ] ✅ [React Repo](#react-repo-1)
- [ ] ✅ [_Email_](#email)
- [ ] ✅ [_Phone_](#phone)
- [ ] ✅ [Social](#social)



---

[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.png?v=103)](https://github.com/ellerbrock/open-source-badges/) [![Bash Shell](https://badges.frapsoft.com/bash/v1/bash.png?v=103)](https://github.com/ellerbrock/open-source-badges/)

[wakatime](https://wakatime.com/@bgoonz)

![Profile views](https://views.whatilearened.today/views/github/bgoonz/views.svg)
---
[![GitHub followers](https://img.shields.io/github/followers/bgoonz.svg?style=social&label=Follow&maxAge=2592000)](https://github.com/bgoonz?tab=followers)
[![GitHub stars](https://img.shields.io/github/stars/Naereen/StrapDown.js.svg?style=social&label=Star&maxAge=2592000)](https://github.com/bgoonz)


---
[![Website shields.io](https://img.shields.io/website-up-down-green-red/http/shields.io.svg)](https://bgoonz.github.io/)
[![Ask Me Anything !](https://img.shields.io/badge/Ask%20me-anything-1abc9c.svg)](https://GitHub.com/bgoonz/ask-me-anything)
[![Gitter](https://badges.gitter.im/bgoonz/community.svg)](https://gitter.im/bgoonz/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
[![PyPI license](https://img.shields.io/pypi/l/ansicolortags.svg)](https://pypi.python.org/pypi/ansicolortags/)

---
![JavaScript](https://img.shields.io/badge/-JavaScript-black?style=flat&logo=javascript)

![React](https://img.shields.io/badge/-React-black?style=flat&logo=react) ![Redux](https://img.shields.io/badge/-Redux-lightblue?style=flat&logo=redux)



![HTML5](https://img.shields.io/badge/-HTML5-E34F26?style=flat&logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/-CSS3-1572B6?style=flat&logo=css3) ![Sass](https://img.shields.io/badge/-Sass-black?style=flat&logo=sass)




![Express](https://img.shields.io/badge/-Express-blue?style=flat&logo=express) ![Nodejs](https://img.shields.io/badge/-Nodejs-green?style=flat&logo=Node.js)![Python](https://img.shields.io/badge/-Python-lightyellow?style=flat&logo=python&logoColor=blue)     ![Bootstrap](https://img.shields.io/badge/-Bootstrap-7952B3?style=flat&logo=bootstrap&logoColor=white) 



![Docker](https://img.shields.io/badge/-Docker-black?style=flat&logo=docker)                                 ![MySQL](https://img.shields.io/badge/-MySQL-black?style=flat&logo=mysql) ![PostgresQL](https://img.shields.io/badge/-PostgreSQL-blue?style=flat&logo=postgresql) ![Git](https://img.shields.io/badge/-Git-black?style=flat&logo=git)      ![Ruby](https://img.shields.io/badge/-Ruby-darkred?style=flat&logo=ruby)             ![Material-UI](https://img.shields.io/badge/-MaterialUI-0081CB?style=flat&logo=Material-UI&logoColor=white)                     



---



*    [**GitHub**](https://github.com/bgoonz)
*    [**Instagram**](https://www.instagram.com/bgoonz/)
*    [**LinkedIn**](https://www.linkedin.com/in/bryan-guner-046199128/)



---
Portfolio:
------------

[netlify](https://tender-bartik-074feb.netlify.app/)

#### OR:

[Github-Pages](https://bgoonz.github.io/)

---



<div style=" border: 1px solid black">
<img src="https://cloud.netlifyusercontent.com/assets/344dbf88-fdf9-42bb-adb4-46f01eedd629/23b9b236-746e-409c-8e86-30b4385e3b72/hr1-raypham.gif" alt="hr-line" width="100%" height="22">
</div>

<hr>


[Github Gists](https://gist.github.com/bgoonz)


#My Gists:

<details>
  
  <summary>Click to expand!</summary>
  
  ---
  
  ### Find Duplicate Files in Working Directory

```js 
const Promise = require( 'bluebird' );
const fs = Promise.promisifyAll( require( 'fs' ) );
const crypto = require( 'crypto' );
const path = require( 'path' );
const pathA = ".";
const pathB = "/path/to/the/directory/you/want/to/compare/it/to";
let hashes = [];
function hashDirIn ( folder ) {
    var pathPromiseA = fs.readdirAsync( folder ).map( function ( fileName ) {
        var workPath = path.join( folder, fileName );
        var statPromise = fs.statAsync( workPath );
        return Promise.join( statPromise, fileName, function ( statPromise, fileName ) {
            if ( statPromise.isFile() ) {
                function makeStream ( file, callback ) {
                    var result = fs.createReadStream( workPath );
                    return callback( result );
                }
                function process ( stream ) {
                    var hash = crypto.createHash( 'md5' );
                    return new Promise( function ( resolve, reject ) {
                        stream.on( 'data', function updateProcess ( chunk ) {
                            hash.update( chunk, 'utf8' );
                        } );
                        stream.on( 'end', resolve );
                    } ).then( function publish () {
                        var digest = hash.digest( 'hex' );
                        hashes.push( { digest: digest, path: workPath } );
                    } );
                }
                return makeStream( fileName, process );
            }
        } );
    } ).then( function () {
        if ( i == 1 ) {
            hashes.sort( function ( a, b ) {
                if ( a.digest < b.digest ) {
                    return -1;
                }
                if ( a.digest > b.digest ) {
                    return 1;
                }
                return 0;
            } );
            var dupe = 1;
            hashes.map( function ( obj, index ) {
                if ( index - 1 >= 0 ) {
                    if ( obj.digest == hashes[ index - 1 ].digest ) {
                        console.log( "Dupe " + dupe + " found:" );
                        console.log( obj.path );
                        console.log( "Equal to:" )
                        console.log( hashes[ index - 1 ].path + "\n" );
                        dupe++;
                    }
                }
            } );
        }
        i++;
    } );
}
var i = 0;
hashDirIn( pathA );
hashDirIn( pathB );

```

---

### Jupyter Note Book Entry On Fourier Transform:

```python
{
  "cells": [
    {
      "cell_type": "markdown",
      "source": [
        "# Frequency and the fast Fourier transform\n",
        "\n",
        "> If you want to find the secrets of the universe, think in terms of energy,\n",
        "> frequency and vibration.\n",
        ">\n",
        "> — Nikola Tesla\n",
        "\n",
        "*This chapter was written in collaboration with SW's father, PW van der Walt.*\n",
        "\n",
        "This chapter will depart slightly from the format of the rest of the\n",
        "book.  In particular, you may find the *code* in the chapter quite\n",
        "modest.  Instead, we want to illustrate an elegant *algorithm*, the\n",
        "Fast Fourier Transform (FFT), that is endlessly useful, implemented in\n",
        "SciPy, and works, of course, on NumPy arrays.\n",
        "\n",
        "## Introducing frequency\n",
        "\n",
        "We'll start by setting up some plotting styles and importing the usual\n",
        "suspects:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "# Make plots appear inline, set custom plotting style\n",
        "%matplotlib inline\n",
        "import matplotlib.pyplot as plt\n",
        "plt.style.use('style/elegant.mplstyle')"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "import numpy as np"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "The discrete[^discrete] Fourier transform (DFT) is a mathematical technique\n",
        "to convert temporal or spatial data into *frequency domain* data.\n",
        "*Frequency* is a familiar concept, due to its colloquial occurrence in\n",
        "the English language: the lowest notes your headphones can rumble out\n",
        "are around 20 Hertz, whereas middle C on a piano lies around 261.6\n",
        "Hertz.  Hertz (Hz), or oscillations per second, in this case literally\n",
        "refers to the number of times per second at which the membrane inside\n",
        "the headphone moves to-and-fro.  That, in turn, creates compressed\n",
        "pulses of air which, upon arrival at your eardrum, induces a vibration\n",
        "at the same frequency.  So, if you take a simple periodic function, $\\sin(10 \\times 2 \\pi t)$, you can view it as a wave:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "f = 10  # Frequency, in cycles per second, or Hertz\n",
        "f_s = 100  # Sampling rate, or number of measurements per second\n",
        "\n",
        "t = np.linspace(0, 2, 2 * f_s, endpoint=False)\n",
        "x = np.sin(f * 2 * np.pi * t)\n",
        "\n",
        "fig, ax = plt.subplots()\n",
        "ax.plot(t, x)\n",
        "ax.set_xlabel('Time [s]')\n",
        "ax.set_ylabel('Signal amplitude');"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"A simple periodic function in time\" -->\n",
        "\n",
        "[^discrete]: The discrete Fourier transform operates on sampled data,\n",
        "             in contrast to the standard Fourier transform which is\n",
        "             defined for continuous functions.\n",
        "\n",
        "Or you can equivalently think of it as a repeating signal of\n",
        "*frequency* 10 Hertz (it repeats once every $1/10$ seconds—a length of\n",
        "time we call its *period*).  Although we naturally associate frequency\n",
        "with time, it can equally well be applied to space.  E.g., a\n",
        "photo of a textile patterns exhibits high *spatial frequency*, whereas\n",
        "the sky or other smooth objects have low spatial frequency.\n",
        "\n",
        "Let us now examine our sinusoid through application of the discrete Fourier\n",
        "transform:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "from scipy import fftpack\n",
        "\n",
        "X = fftpack.fft(x)\n",
        "freqs = fftpack.fftfreq(len(x)) * f_s\n",
        "\n",
        "fig, ax = plt.subplots()\n",
        "\n",
        "ax.stem(freqs, np.abs(X))\n",
        "ax.set_xlabel('Frequency in Hertz [Hz]')\n",
        "ax.set_ylabel('Frequency Domain (Spectrum) Magnitude')\n",
        "ax.set_xlim(-f_s / 2, f_s / 2)\n",
        "ax.set_ylim(-5, 110)"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Frequencies that make up our periodic signal above\" -->\n",
        "\n",
        "We see that the output of the FFT is a one-dimensional array of the\n",
        "same shape as the input, containing complex values.  All values are\n",
        "zero, except for two entries.  Traditionally, we visualize the\n",
        "magnitude of the result as a *stem plot*, in which the height of each\n",
        "stem corresponds to the underlying value.\n",
        "\n",
        "(We explain why you see positive and negative frequencies later on\n",
        "in the sidebox titled \"Discrete Fourier transforms\".  You may also\n",
        "refer to that section for a more in-depth overview of the underlying\n",
        "mathematics.)\n",
        "\n",
        "The Fourier transform takes us from the *time* to the *frequency*\n",
        "domain, and this turns out to have a massive number of applications.\n",
        "The *fast Fourier transform* is an algorithm for computing the\n",
        "discrete Fourier transform; it achieves its high speed by storing and\n",
        "re-using results of computations as it progresses.\n",
        "\n",
        "In this chapter, we examine a few applications of the discrete Fourier\n",
        "transform to demonstrate that the FFT can be applied to\n",
        "multidimensional data (not just 1D measurements) to achieve a variety\n",
        "of goals.\n",
        "\n",
        "## Illustration: a birdsong spectrogram\n",
        "\n",
        "Let's start with one of the most common applications, converting a sound signal (consisting of variations of air pressure over time) to a *spectrogram*.\n",
        "You might have seen spectrograms on your music player's equalizer view, or even on an old-school stereo.\n",
        "\n",
        "![The Numark EQ2600 Stereo Equalizer; image used with permission from the author, Sergey Gerasimuk. Source: http://sgerasimuk.blogspot.com/2014/06/numark-eq-2600-10-band-stereo-graphic.html](../images/sergey_gerasimuk_numark-eq-2600-IMG_0236.JPG)\n",
        "\n",
        "Listen to the following snippet of nightingale birdsong (released under CC BY 4.0 at\n",
        "http://www.orangefreesounds.com/nightingale-sound/):"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "from IPython.display import Audio\n",
        "Audio('data/nightingale.wav')"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "If you are reading the paper version of this book, you'll have to use\n",
        "your imagination!  It goes something like this:\n",
        "chee-chee-woorrrr-hee-hee cheet-wheet-hoorrr-chi\n",
        "rrr-whi-wheo-wheo-wheo-wheo-wheo-wheo.\n",
        "\n",
        "Since we realise that not everyone is fluent in bird-speak, perhaps\n",
        "it's best if we visualize the measurements—better known as \"the\n",
        "signal\"—instead.\n",
        "\n",
        "We load the audio file, which gives us\n",
        "the sampling rate (number of measurements per second) as well as audio\n",
        "data as an `(N, 2)` array—two columns because this is a stereo\n",
        "recording."
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "from scipy.io import wavfile\n",
        "\n",
        "rate, audio = wavfile.read('data/nightingale.wav')"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "We convert to mono by averaging the left and right channels."
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "audio = np.mean(audio, axis=1)"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "Then, calculate the length of the snippet and plot the audio."
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "N = audio.shape[0]\n",
        "L = N / rate\n",
        "\n",
        "print(f'Audio length: {L:.2f} seconds')\n",
        "\n",
        "f, ax = plt.subplots()\n",
        "ax.plot(np.arange(N) / rate, audio)\n",
        "ax.set_xlabel('Time [s]')\n",
        "ax.set_ylabel('Amplitude [unknown]');"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Audio waveform plot of birdsong\" -->\n",
        "\n",
        "Well, that's not very satisfying, is it?  If I sent this voltage to a\n",
        "speaker, I might hear a bird chirping, but I can't very well imagine\n",
        "how it would sound like in my head.  Is there a better way of *seeing*\n",
        "what is going on?\n",
        "\n",
        "There is, and it is called the discrete Fourier transform, where\n",
        "discrete refers to the recording consisting of time-spaced sound\n",
        "measurements, in contrast to a continual recording as, e.g., on\n",
        "magnetic tape (remember casettes?).  The discrete Fourier\n",
        "transform is often computed using the *fast Fourier transform* (FFT)\n",
        "algorithm, a name informally used to refer to the DFT itself. The\n",
        "DFT tells us which frequencies or \"notes\" to expect in our signal.\n",
        "\n",
        "Of course, a bird sings many notes throughout the song, so we'd also\n",
        "like to know *when* each note occurs.  The Fourier transform takes a\n",
        "signal in the time domain (i.e., a set of measurements over time) and\n",
        "turns it into a spectrum—a set of frequencies with corresponding\n",
        "(complex[^complex]) values.  The spectrum does not contain any information about\n",
        "time! [^time]\n",
        "\n",
        "[^complex]: The Fourier transform essentially tells us how to combine\n",
        "            a set of sinusoids of varying frequency to form the input\n",
        "            signal.  The spectrum consists of complex numbers—one for\n",
        "            each sinusoid.  A complex number encodes two things: a\n",
        "            magnitude and an angle.  The magnitude is the strength of\n",
        "            the sinusoid in the signal, and the angle how much it is\n",
        "            shifted in time.  At this point, we only care about the\n",
        "            magnitude, which we calculate using ``np.abs``.\n",
        "\n",
        "[^time]: For more on techniques for calculating both (approximate) frequencies\n",
        "         and time of occurrence, read up on wavelet analysis.\n",
        "\n",
        "So, to find both the frequencies and the time at which they were sung,\n",
        "we'll need to be somewhat clever.  Our strategy is as follows:\n",
        "take the audio signal, split it into small, overlapping slices, and\n",
        "apply the Fourier transform to each (a technique known as the Short\n",
        "Time Fourier Transform).\n",
        "\n",
        "We'll split the signal into slices of 1024 samples—that's about 0.02\n",
        "seconds of audio.  Why we choose 1024 and not 1000 we'll explain in a\n",
        "second when we examine performance.  The slices will overlap by 100\n",
        "samples as shown here:\n",
        "\n",
        "![A sliding window operation](../figures/generated/sliding_window.png)\n",
        "\n",
        "Start by chopping up the signal into slices of 1024 samples, each\n",
        "slice overlapping the previous by 100 samples.  The resulting `slices`\n",
        "object contains one slice per row."
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "from skimage import util\n",
        "\n",
        "M = 1024\n",
        "\n",
        "slices = util.view_as_windows(audio, window_shape=(M,), step=100)\n",
        "print(f'Audio shape: {audio.shape}, Sliced audio shape: {slices.shape}')"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "Generate a windowing function (see the section on windowing for a\n",
        "discussion of the underlying assumptions and interpretations of each)\n",
        "and multiply it with the signal:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "win = np.hanning(M + 1)[:-1]\n",
        "slices = slices * win"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "It's more convenient to have one slice per column, so we take the transpose:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "slices = slices.T\n",
        "print('Shape of `slices`:', slices.shape)"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "For each slice, calculate the discrete Fourier transform.  The DFT\n",
        "returns both positive and negative frequencies (more on that in\n",
        "\"Frequencies and their ordering\"), so we slice out the positive M / 2\n",
        "frequencies for now."
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "spectrum = np.fft.fft(slices, axis=0)[:M // 2 + 1:-1]\n",
        "spectrum = np.abs(spectrum)"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "(As a quick aside, you'll note that we use `scipy.fftpack.fft` and\n",
        "`np.fft` interchangeably.  NumPy provides basic FFT functionality,\n",
        "which SciPy extends further, but both include an `fft` function, based\n",
        "on the Fortran FFTPACK.)\n",
        "\n",
        "The spectrum can contain both very large and very small values.\n",
        "Taking the log compresses the range significantly.\n",
        "\n",
        "Here we do a log plot of the ratio of the signal divided by the maximum signal.\n",
        "The specific unit used for the ratio is the decibel, $20\n",
        "log_{10}\\left(\\mathrm{amplitude ratio}\\right)$."
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "f, ax = plt.subplots(figsize=(4.8, 2.4))\n",
        "\n",
        "S = np.abs(spectrum)\n",
        "S = 20 * np.log10(S / np.max(S))\n",
        "\n",
        "ax.imshow(S, origin='lower', cmap='viridis',\n",
        "          extent=(0, L, 0, rate / 2 / 1000))\n",
        "ax.axis('tight')\n",
        "ax.set_ylabel('Frequency [kHz]')\n",
        "ax.set_xlabel('Time [s]');"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Birdsong spectrogram\" -->\n",
        "\n",
        "Much better!  We can now see the frequencies vary over time, and it\n",
        "corresponds to the way the audio sounds.  See if you can match my\n",
        "earlier description: chee-chee-woorrrr-hee-hee cheet-wheet-hoorrr-chi\n",
        "rrr-whi-wheo-wheo-wheo-wheo-wheo-wheo (I didn't transcribe the section\n",
        "from 3 to 5 seconds—that's another bird).\n",
        "\n",
        "SciPy already includes an implementation of this\n",
        "procedure as ``scipy.signal.spectrogram``, which can be invoked as\n",
        "follows:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "from scipy import signal\n",
        "\n",
        "freqs, times, Sx = signal.spectrogram(audio, fs=rate, window='hanning',\n",
        "                                      nperseg=1024, noverlap=M - 100,\n",
        "                                      detrend=False, scaling='spectrum')\n",
        "\n",
        "f, ax = plt.subplots(figsize=(4.8, 2.4))\n",
        "ax.pcolormesh(times, freqs / 1000, 10 * np.log10(Sx), cmap='viridis')\n",
        "ax.set_ylabel('Frequency [kHz]')\n",
        "ax.set_xlabel('Time [s]');"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"SciPy built-in rendition of birdsong spectrogram\" -->\n",
        "\n",
        "The only differences are that SciPy returns the spectrum magnitude\n",
        "squared (which turns measured voltage into measured energy), and\n",
        "multiplies it by some normalization factors[^scaling].\n",
        "\n",
        "[^scaling]: SciPy goes to some effort to preserve the energy in the\n",
        "            spectrum.  Therefore, when taking only half the components\n",
        "            (for N even), it multiplies the remaining components,\n",
        "            apart from the first and last components, by two (those\n",
        "            two components are \"shared\" by the two halves of the\n",
        "            spectrum).  It also normalizes the window by dividing it\n",
        "            by its sum.\n",
        "\n",
        "## History\n",
        "\n",
        "Tracing the exact origins of the Fourier transform is tricky.  Some\n",
        "related procedures go as far back as Babylonian times, but it was the\n",
        "hot topics of calculating asteroid orbits and solving the heat (flow)\n",
        "equation that led to several breakthroughs in the early 1800s.  Whom\n",
        "exactly among Clairaut, Lagrange, Euler, Gauss and D'Alembert we\n",
        "should thank is not exactly clear, but Gauss was the first to describe\n",
        "the fast Fourier transform (an algorithm for computing the discrete\n",
        "Fourier transform, popularized by Cooley and Tukey in 1965).  Joseph\n",
        "Fourier, after whom the transform is named, first claimed that\n",
        "*arbitrary* periodic [^periodic] functions can be expressed as a sum of\n",
        "trigonometric functions.\n",
        "\n",
        "[^periodic]: The period can, in fact, also be infinite!  The general\n",
        "             continuous Fourier transform provides for this\n",
        "             possibility.  Discrete Fourier transforms are generally\n",
        "             defined over a finite interval, and this is implicitly\n",
        "             the period of the time domain function that is\n",
        "             transformed.  In other words, if you do the inverse\n",
        "             discrete Fourier transform, you *always* get a periodic\n",
        "             signal out.\n",
        "\n",
        "## Implementation\n",
        "\n",
        "The discrete Fourier transform functionality in SciPy lives in the\n",
        "`scipy.fftpack`` module.  Among other things, it provides the\n",
        "following DFT-related functionality:\n",
        "\n",
        " - ``fft``, ``fft2``, ``fftn``: Compute the discrete Fourier transform using\n",
        "   the Fast Fourier Transform algorithm in 1, 2, or `n` dimensions.\n",
        " - ``ifft``, ``ifft2``, ``ifftn``: Compute the inverse of the DFT\n",
        " - ``dct``, ``idct``, ``dst``, ``idst``: Compute the cosine and sine transforms, and their inverses.\n",
        " - ``fftshift``, ``ifftshift``: Shift the zero-frequency component to the center of the spectrum and back, respectively (more about that soon).\n",
        " - ``fftfreq``: Return the discrete Fourier transform sample frequencies.\n",
        " - ``rfft``: Compute the DFT of a real sequence, exploiting the symmetry of the resulting spectrum for increased performance.  Also used by ``fft`` internally when applicable.\n",
        "\n",
        "This is complemented by the following functions in NumPy:\n",
        "\n",
        " - ``np.hanning``, ``np.hamming``, ``np.bartlett``, ``np.blackman``,\n",
        "   ``np.kaiser``: Tapered windowing functions.\n",
        "\n",
        "It is also used to perform fast convolutions of large inputs by\n",
        "``scipy.signal.fftconvolve`.\n",
        "\n",
        "SciPy wraps the Fortran FFTPACK library—it is not the fastest out\n",
        "there, but unlike packages such as FFTW, it has a permissive free\n",
        "software license.\n",
        "\n",
        "## Choosing the length of the discrete Fourier transform (DFT)\n",
        "\n",
        "A naive calculation of the DFT takes $\\mathcal{O}\\left(N^2\\right)$ operations [^big_O].\n",
        "How come?  Well, you have $N$\n",
        "(complex) sinusoids of different frequencies ($2 \\pi f \\times 0, 2 \\pi f \\times\n",
        "1, 2 \\pi f \\times 3, ..., 2 \\pi f \\times (N - 1)$), and you want to see how\n",
        "strongly your signal corresponds to each.  Starting with the first,\n",
        "you take the dot product with the signal (which, in itself, entails $N$\n",
        "multiplication operations).  Repeating this operation$N$times, once\n",
        "for each sinusoid, then gives $N^2$ operations.\n",
        "\n",
        "[^big_O]: In computer science, the computational cost of an algorithm\n",
        "          is often expressed in \"Big O\" notation.  The notation gives\n",
        "          us an indication of how an algorithm's execution time scales\n",
        "          with an increasing number of elements.  If an algorithm is $\\mathcal{O}(N)$,\n",
        "          it means its execution time increases linearly with\n",
        "          the number of input elements (for example, searching for a\n",
        "          given value in an unsorted list is $\\mathcal{O}\\left(N\\right)$).  Bubble sort is\n",
        "          an example of an $O\\left(N^2\\right)$ algorithm; the exact number of\n",
        "          operations performed may, hypothetically, be $N + \\frac{1}{2} N^2$,\n",
        "          meaning that the computational cost grows quadratically with\n",
        "          the number of input elements.\n",
        "\n",
        "Now, contrast that with the fast Fourier transform, which is $\\mathcal{O}\\left(N \\log N\\right)$ in\n",
        "the ideal case due to the clever re-use of\n",
        "calculations—a great improvement!  However, the classical Cooley-Tukey\n",
        "algorithm implemented in FFTPACK (and used by SciPy) recursively breaks up the transform\n",
        "into smaller (prime-sized) pieces and only shows this improvement for\n",
        "\"smooth\" input lengths (an input length is considered smooth when its\n",
        "largest prime factor is small).  For large prime sized pieces, the\n",
        "Bluestein or Rader algorithms can be used in conjunction with the\n",
        "Cooley-Tukey algorithm, but this optimization is not implemented in\n",
        "FFTPACK.[^fast]\n",
        "\n",
        "Let us illustrate:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "import time\n",
        "\n",
        "from scipy import fftpack\n",
        "from sympy import factorint\n",
        "\n",
        "K = 1000\n",
        "lengths = range(250, 260)\n",
        "\n",
        "# Calculate the smoothness for all input lengths\n",
        "smoothness = [max(factorint(i).keys()) for i in lengths]\n",
        "\n",
        "\n",
        "exec_times = []\n",
        "for i in lengths:\n",
        "    z = np.random.random(i)\n",
        "\n",
        "    # For each input length i, execute the FFT K times\n",
        "    # and store the execution time\n",
        "\n",
        "    times = []\n",
        "    for k in range(K):\n",
        "        tic = time.monotonic()\n",
        "        fftpack.fft(z)\n",
        "        toc = time.monotonic()\n",
        "        times.append(toc - tic)\n",
        "\n",
        "    # For each input length, remember the *minimum* execution time\n",
        "    exec_times.append(min(times))\n",
        "\n",
        "\n",
        "f, (ax0, ax1) = plt.subplots(2, 1, sharex=True)\n",
        "ax0.stem(lengths, np.array(exec_times) * 10**6)\n",
        "ax0.set_ylabel('Execution time (µs)')\n",
        "\n",
        "ax1.stem(lengths, smoothness)\n",
        "ax1.set_ylabel('Smoothness of input length\\n(lower is better)')\n",
        "ax1.set_xlabel('Length of input');"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"FFT execution time vs smoothness for different input lengths\" -->\n",
        "\n",
        "The intuition is that, for smooth numbers, the FFT can be broken up\n",
        "into many small pieces. After performing the FFT on the first piece,\n",
        "those results can be reused in subsequent computations.  This explains\n",
        "why we chose a length of 1024 for our audio slices earlier—it has a\n",
        "smoothness of only 2, resulting in the optimal \"radix-2 Cooley-Tukey\"\n",
        "algorithm, which computes the FFT using only $(N/2) \\log_2 N = 5120$ complex\n",
        "multiplications, instead of $N^2 = 1048576$.  Choosing $N = 2^m$\n",
        "always ensures a maximally smooth $N$ (and, thus, the fastest FFT).\n",
        "\n",
        "[^fast]: While ideally we don't want to reimplement existing\n",
        "         algorithms, sometimes it becomes necessary in order to obtain\n",
        "         the best execution speeds possible, and tools\n",
        "         like [Cython](http://cython.org)—which compiles Python to\n",
        "         C—and [Numba](http://numba.pydata.org)—which does\n",
        "         just-in-time compilation of Python code—make life a lot\n",
        "         easier (and faster!).  If you are able to use GPL-licenced\n",
        "         software, you may consider\n",
        "         using [PyFFTW](https://github.com/hgomersall/pyFFTW) for\n",
        "         faster FFTs.\n",
        "\n",
        "## More discrete Fourier transform concepts\n",
        "\n",
        "Next, we present a couple of common concepts worth knowing before\n",
        "operating heavy Fourier transform machinery, whereafter we tackle\n",
        "another real-world problem: analyzing target detection in radar data.\n",
        "\n",
        "### Frequencies and their ordering\n",
        "\n",
        "For historical reasons, most implementations return an array where\n",
        "frequencies vary from low-to-high-to-low (see the box \"Discrete\n",
        "Fourier transforms\" for further explanation of frequencies).  E.g., when we do the real\n",
        "Fourier transform of a signal of all ones, an input that has no\n",
        "variation and therefore only has the slowest, constant Fourier\n",
        "component (also known as the \"DC\" or Direct Current component—just\n",
        "electronics jargon for \"mean of the signal\"), appearing as the first\n",
        "entry:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "from scipy import fftpack\n",
        "N = 10\n",
        "\n",
        "fftpack.fft(np.ones(N))  # The first component is np.mean(x) * N"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "When we try the FFT on a rapidly changing signal, we see a high\n",
        "frequency component appear:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "z = np.ones(10)\n",
        "z[::2] = -1\n",
        "\n",
        "print(f'Applying FFT to {z}')\n",
        "fftpack.fft(z)"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "Note that the FFT returns a complex spectrum which, in the case of\n",
        "real inputs, is conjugate symmetrical (i.e., symmetric in the real\n",
        "part, and anti-symmetric in the imaginary part):"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "x = np.array([1, 5, 12, 7, 3, 0, 4, 3, 2, 8])\n",
        "X = fftpack.fft(x)\n",
        "\n",
        "with np.printoptions(precision=2):\n",
        "    print(\"Real part:     \", X.real)\n",
        "    print(\"Imaginary part:\", X.imag)"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "(And, again, recall that the first component is ``np.mean(x) * N``.)\n",
        "\n",
        "The `fftfreq` function tells us which frequencies we are looking at\n",
        "specifically:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "fftpack.fftfreq(10)"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "The result tells us that our maximum component occured at a frequency\n",
        "of 0.5 cycles per sample.  This agrees with the input, where a\n",
        "minus-one-plus-one cycle repeated every second sample.\n",
        "\n",
        "Sometimes, it is convenient to view the spectrum organized slightly\n",
        "differently, from high-negative to low to-high-positive (for now, we\n",
        "won't dive too deeply into the concept of negative frequency, other\n",
        "than saying a real-world sine wave is produced by a combination of\n",
        "positive and negative frequencies).  We re-shuffle the spectrum using\n",
        "the `fftshift` function.\n",
        "\n",
        "> **Discrete Fourier transforms {.callout}**\n",
        ">\n",
        "> The Discrete Fourier Transform (DFT) converts a sequence of $N$\n",
        "> equally spaced real or complex samples $x_{0,}x_{1,\\ldots x_{N-1}}$ of\n",
        "> a function $x(t)$ of time (or another variable, depending on the\n",
        "> application) into a sequence of $N$ complex numbers $X_{k}$ by the\n",
        "> summation\n",
        ">\n",
        "> $$X_{k}=\\sum_{n=0}^{N-1}x_{n}e^{-j2\\pi kn/N},\\;k=0,1,\\ldots\n",
        "> N-1.$$\n",
        ">\n",
        "> With the numbers $X_{k}$ known, the inverse DFT *exactly* recovers the\n",
        "> sample values $x_{n}$ through the summation\n",
        ">\n",
        "> $$x_{n}=\\frac{1}{N}\\sum_{k=0}^{N-1}X_{k}e^{j2\\pi kn/N}.$$\n",
        ">\n",
        "> Keeping in mind that $e^{j\\theta}=\\cos\\theta+j\\sin\\theta,$ the last\n",
        "> equation shows that the DFT has decomposed the sequence $x_{n}$ into a\n",
        "> complex discrete Fourier series with coefficients $X_{k}$. Comparing\n",
        "> the DFT with a continuous complex Fourier series\n",
        ">\n",
        "> $$x(t)=\\sum_{n=-\\infty}^{\\infty}c_{n}e^{jn\\omega_{0}t},$$\n",
        ">\n",
        "> the DFT is a *finite *series with $N$ terms defined at the equally\n",
        "> spaced discrete instances of the *angle* $(\\omega_{0}t_{n})=2\\pi\\frac{k}{N}$\n",
        "> in the interval $[0,2\\pi)$,\n",
        "> i.e. *including* $0$  and *excluding* $2\\pi$.\n",
        "> This automatically normalizes the DFT so that time does\n",
        "> not appear explicitly in the forward or inverse transform.\n",
        ">\n",
        "> If the original function $x(t)$ is limited in frequency to less than\n",
        "> half of the sampling frequency (the so-called *Nyquist frequency*),\n",
        "> interpolation between sample values produced by the inverse DFT will\n",
        "> usually give a faithful reconstruction of $x(t)$. If $x(t)$ is *not*\n",
        "> limited as such, the inverse DFT can, in general, not be used to\n",
        "> reconstruct $x(t)$ by interpolation.  Note that this limit does not\n",
        "> imply that there are *no* methods that can do such a\n",
        "> reconstruction—see, e.g., compressed sensing, or finite rate of\n",
        "> innovation sampling.\n",
        ">\n",
        "> The function $e^{j2\\pi k/N}=\\left(e^{j2\\pi/N}\\right)^{k}=w^{k}$ takes on\n",
        "> discrete values between $0$ and $2\\pi\\frac{N-1}{N}$ on the unit circle in\n",
        "> the complex plane. The function $e^{j2\\pi kn/N}=w^{kn}$ encircles the\n",
        "> origin $n\\frac{N-1}{N}$ times, thus generating harmonics of the fundamental\n",
        "> sinusoid for which $n=1$.\n",
        ">\n",
        "> The way in which we defined the DFT leads to a few subtleties\n",
        "> when $n>\\frac{N}{2}$, for even $N$ [^odd_N]. The function $e^{j2\\pi kn/N}$ is plotted\n",
        "> for increasing values of $k$ in the figure below,\n",
        "> for the cases $n=1$ to $n=N-1$ for $N=16$. When $k$ increases from $k$\n",
        "> to $k+1$, the angle increases by $\\frac{2\\pi n}{N}$. When $n=1$,\n",
        "> the step is $\\frac{2\\pi}{N}$. When $n=N-1$, the angle\n",
        "> increases by $2\\pi\\frac{N-1}{N}=2\\pi-\\frac{2\\pi}{N}$. Since $2\\pi$\n",
        "> is precisely once around the circle, the step equates to $-\\frac{2\\pi}{N}$,\n",
        "> i.e. in the direction of a negative\n",
        "> frequency. The components up to $N/2$ represent *positive* frequency\n",
        "> components, those above $N/2$ up to $N-1$ represent *negative*\n",
        "> frequencies. The angle increment for the component $N/2$\n",
        "> for $N$ even advances precisely halfway around the circle for\n",
        "> each increment in $k$ and can therefore be interpreted as either a\n",
        "> positive or a negative frequency. This component of the DFT represents\n",
        "> the Nyquist Frequency, i.e. half of the sampling frequency, and is\n",
        "> useful to orientate oneself when looking at DFT graphics.\n",
        ">\n",
        "> The FFT in turn is simply a special and highly efficient algorithm for\n",
        "> calculating the DFT. Whereas a straightforward calculation of the DFT\n",
        "> takes of the order of $N^{2}$ calculations to compute, the FFT\n",
        "> algorithm requires of the order $N\\log N$ calculations. The FFT was\n",
        "> the key to the wide-spread use of the DFT in real-time applications\n",
        "> and was included in a list of the top $10$ algorithms of the $20^{th}$\n",
        "> century by the IEEE journal Computing in Science & Engineering in the\n",
        "> year $2000$.\n",
        ">\n",
        "> ![Unit circle samples](../figures/unit_circle_samples.png)\n",
        "\n",
        "[^odd_N]: We leave it as an exercise for the reader to picture the\n",
        "          situation for $N$ odd.  In this chapter, all examples use\n",
        "          even-order DFTs.\n",
        "\n",
        "Let's examine the frequency components in a noisy image.  Note that,\n",
        "while a static image has no time-varying component, its values do vary\n",
        "across *space*.  The DFT applies equally to either case.\n",
        "\n",
        "First, load and display the image:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "from skimage import io\n",
        "image = io.imread('images/moonlanding.png')\n",
        "M, N = image.shape\n",
        "\n",
        "f, ax = plt.subplots(figsize=(4.8, 4.8))\n",
        "ax.imshow(image)\n",
        "\n",
        "print((M, N), image.dtype)"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"A noisy image of the moon landing\" -->\n",
        "\n",
        "Do not adjust your monitor!  The image you are seeing is real,\n",
        "although clearly distorted by either the measurement or transmission\n",
        "equipment.\n",
        "\n",
        "To examine the spectrum of the image, we use `fftn` (instead of `fft`)\n",
        "to compute the DFT, since it has more than one dimension.  The\n",
        "two-dimensional FFT is equivalent to taking the 1-D FFT across rows\n",
        "and then across columns (or vice versa)."
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "F = fftpack.fftn(image)\n",
        "\n",
        "F_magnitude = np.abs(F)\n",
        "F_magnitude = fftpack.fftshift(F_magnitude)\n"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "Again, we take the log of the spectrum to compress the range of\n",
        "values, before displaying:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "f, ax = plt.subplots(figsize=(4.8, 4.8))\n",
        "\n",
        "ax.imshow(np.log(1 + F_magnitude), cmap='viridis',\n",
        "          extent=(-N // 2, N // 2, -M // 2, M // 2))\n",
        "ax.set_title('Spectrum magnitude');"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Spectrum of the noisy moon landing image (magnitude)\" -->\n",
        "\n",
        "Note the high values around the origin (middle) of the spectrum—these\n",
        "coefficients describe the low frequencies or smooth parts of the\n",
        "image; a vague canvas of the photo.  Higher frequency components,\n",
        "spread throughout the spectrum, fill in the edges and detail.  Peaks\n",
        "around higher frequencies correspond to the periodic noise.\n",
        "\n",
        "From the photo, we can see that the noise (measurement artifacts) is\n",
        "highly periodic, so we hope to remove it by zeroing out the\n",
        "corresponding parts of the spectrum.\n",
        "\n",
        "The image with those peaks suppressed indeed looks quite different!"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "# Set block around center of spectrum to zero\n",
        "K = 40\n",
        "F_magnitude[M // 2 - K: M // 2 + K, N // 2 - K: N // 2 + K] = 0\n",
        "\n",
        "# Find all peaks higher than the 98th percentile\n",
        "peaks = F_magnitude < np.percentile(F_magnitude, 98)\n",
        "\n",
        "# Shift the peaks back to align with the original spectrum\n",
        "peaks = fftpack.ifftshift(peaks)\n",
        "\n",
        "# Make a copy of the original (complex) spectrum\n",
        "F_dim = F.copy()\n",
        "\n",
        "# Set those peak coefficients to zero\n",
        "F_dim = F_dim * peaks.astype(int)\n",
        "\n",
        "# Do the inverse Fourier transform to get back to an image\n",
        "# Since we started with a real image, we only look at the real part of\n",
        "# the output.\n",
        "image_filtered = np.real(fftpack.ifft2(F_dim))\n",
        "\n",
        "f, (ax0, ax1) = plt.subplots(2, 1, figsize=(4.8, 7))\n",
        "ax0.imshow(fftpack.fftshift(np.log10(1 + np.abs(F_dim))), cmap='viridis')\n",
        "ax0.set_title('Spectrum after suppression')\n",
        "\n",
        "ax1.imshow(image_filtered)\n",
        "ax1.set_title('Reconstructed image');"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Filtered moon landing image and its spectrum\" -->\n",
        "\n",
        "### Windowing\n",
        "\n",
        "If we examine the Fourier transform of a rectangular pulse, we see\n",
        "significant sidelobes in the spectrum:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "x = np.zeros(500)\n",
        "x[100:150] = 1\n",
        "\n",
        "X = fftpack.fft(x)\n",
        "\n",
        "f, (ax0, ax1) = plt.subplots(2, 1, sharex=True)\n",
        "\n",
        "ax0.plot(x)\n",
        "ax0.set_ylim(-0.1, 1.1)\n",
        "\n",
        "ax1.plot(fftpack.fftshift(np.abs(X)))\n",
        "ax1.set_ylim(-5, 55);"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Spectrum of a rectangular pulse (magnitude)\" -->\n",
        "\n",
        "In theory, you would need a combination of infinitely many sinusoids\n",
        "(frequencies) to represent any abrupt transition; the coefficients would\n",
        "typically have the same sidelobe structure as seen here for the pulse.\n",
        "\n",
        "Importantly, the discrete Fourier transform assumes that the input\n",
        "signal is periodic.  If the signal is not, the assumption is simply\n",
        "that, right at the end of the signal, it jumps back to its beginning\n",
        "value.  Consider the function, $x(t)$, shown here:\n",
        "\n",
        "<img src=\"../figures/periodic.png\"/>\n",
        "<!-- caption text=\"Eight samples have been taken of a given\n",
        " function with effective length $T_{eff}$.  With the discrete Fourier\n",
        " transform assuming periodicity, it creates a step discontinuity\n",
        " between the first and last samples.\" -->\n",
        "\n",
        "We only measure the signal for a short time, labeled $T_{eff}$.  The\n",
        "Fourier transform assumes that $x(8) = x(0)$, and that the signal is\n",
        "continued as the dashed, rather than the solid line.  This introduces\n",
        "a big jump at the edge, with the expected oscillation in the spectrum:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "t = np.linspace(0, 1, 500)\n",
        "x = np.sin(49 * np.pi * t)\n",
        "\n",
        "X = fftpack.fft(x)\n",
        "\n",
        "f, (ax0, ax1) = plt.subplots(2, 1)\n",
        "\n",
        "ax0.plot(x)\n",
        "ax0.set_ylim(-1.1, 1.1)\n",
        "\n",
        "ax1.plot(fftpack.fftfreq(len(t)), np.abs(X))\n",
        "ax1.set_ylim(0, 190);"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Spectrum oscillation due to signal edge discontinuity\" -->\n",
        "\n",
        "Instead of the expected two lines, the peaks are spread out in the\n",
        "spectrum.\n",
        "\n",
        "We can counter this effect by a process called *windowing*. The\n",
        "original function is multiplied with a window function such as the\n",
        "Kaiser window $K(N,\\beta)$.  Here we visualize it for $\\beta$ ranging\n",
        "from 0 to 100:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "f, ax = plt.subplots()\n",
        "\n",
        "N = 10\n",
        "beta_max = 5\n",
        "colormap = plt.cm.plasma\n",
        "\n",
        "norm = plt.Normalize(vmin=0, vmax=beta_max)\n",
        "\n",
        "lines = [\n",
        "    ax.plot(np.kaiser(100, beta), color=colormap(norm(beta)))\n",
        "    for beta in np.linspace(0, beta_max, N)\n",
        "    ]\n",
        "\n",
        "sm = plt.cm.ScalarMappable(cmap=colormap, norm=norm)\n",
        "\n",
        "sm._A = []\n",
        "\n",
        "plt.colorbar(sm).set_label(r'Kaiser $\\beta$');"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"The Kaiser window for various values of $\\beta$\" -->\n",
        "\n",
        "By changing the parameter $\\beta$, the shape of the window can be\n",
        "changed from rectangular ($\\beta=0$, no windowing) to a window that\n",
        "produces signals that smoothly increase from zero and decrease to zero\n",
        "at the endpoints of the sampled interval, producing very low side\n",
        "lobes ($\\beta$ typically between 5 and 10) [^choosing_a_window].\n",
        "\n",
        "[^choosing_a_window]: The classical windowing functions include Hann,\n",
        "                      Hamming, and Blackman.  They differ in their\n",
        "                      sidelobe levels and in the broadening of the\n",
        "                      main lobe (in the Fourier domain).  A modern and\n",
        "                      flexible window function that is close to\n",
        "                      optimal for most applications is the Kaiser\n",
        "                      window—a good approximation to the optimal\n",
        "                      prolate spheroid window, which concentrates the\n",
        "                      most energy into the main lobe.  The Kaiser\n",
        "                      window can be tuned to suit the particular\n",
        "                      application, as illustrated in the main text, by\n",
        "                      adjusting the parameter $\\beta$.\n",
        "\n",
        "Applying the Kaiser window here, we see that the sidelobes have been\n",
        "drastically reduced, at the cost of a slight widening in the main lobe.\n",
        "\n",
        "<!--\n",
        "*For online notebook, use something like:*"
      ],
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "```\n",
        "# @interact(beta=(0, 20.))\n",
        "# def window(beta):\n",
        "#    x = np.kaiser(1000, beta)\n",
        "#    f, axes = plt.subplots(1, 2, figsize=(4.8, 2.4))\n",
        "#    axes[0].plot(x)\n",
        "#    axes[1].plot(fftpack.fftshift(np.abs(np.fft.fft(x, 10000))))\n",
        "#    axes[1].set_xlim(2*2480, 2*2520)\n",
        "#    plt.show()\n",
        "```\n"
      ],
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "-->\n",
        "\n",
        "The effect of windowing our previous example is noticeable:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "win = np.kaiser(len(t), 5)\n",
        "X_win = fftpack.fft(x * win)\n",
        "\n",
        "plt.plot(fftpack.fftfreq(len(t)), np.abs(X_win))\n",
        "plt.ylim(0, 190);"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Spectrum of a windowed signal (magnitude)\" -->\n",
        "\n",
        "## Real-world Application: Analyzing Radar Data\n",
        "\n",
        "Linearly modulated FMCW (Frequency-Modulated Continuous-Wave) radars\n",
        "make extensive use of the FFT algorithm for signal processing and\n",
        "provide examples of various applications of the FFT. We will use actual\n",
        "data from an FMCW radar to demonstrate one such an application: target\n",
        "detection.\n",
        "\n",
        "Roughly, an FMCW radar works like this (see box \"A\n",
        "simple FMCW radar system\" for more detail):\n",
        "\n",
        "A signal with changing frequency is generated.  This signal is\n",
        "transmitted by an antenna, after which it travels outwards, away from the\n",
        "radar.  When it hits an object, part of the signal is reflected back\n",
        "to the radar, where it is received, multiplied by a copy of the\n",
        "transmitted signal, and sampled, turning it into\n",
        "numbers that are packed into an array.  Our challenge is to interpret\n",
        "those numbers to form meaningful results.\n",
        "\n",
        "The multiplication step above is important.  From school, recall the\n",
        "trigonometric identity:\n",
        "\n",
        "$\n",
        "\\sin(xt) \\sin(yt) = \\frac{1}{2}\n",
        "\\left[ \\sin \\left( (x - y)t + \\frac{\\pi}{2} \\right) - \\sin \\left( (x + y)t + \\frac{\\pi}{2} \\right) \\right]\n",
        "$\n",
        "\n",
        "Thus, if we multiply the received signal by the transmitted signal, we\n",
        "expect two frequency components to appear in the spectrum: one that is\n",
        "the difference in frequencies between the received and transmitted\n",
        "signal, and one that is the sum of their frequencies.\n",
        "\n",
        "We are particularly interested in the first, since that gives us some\n",
        "indication of how long it took the signal to reflect back to the radar\n",
        "(in other words, how far away the object is from us!).  We discard the\n",
        "other by applying a low-pass filter to the signal (i.e., a filter that\n",
        "discards any high frequencies).\n",
        "\n",
        "> **A simple FMCW radar system** {.callout}\n",
        ">\n",
        "> ![The block diagram of a simple FMCW radar system](../figures/FMCW_Block.png)\n",
        ">\n",
        "> A block diagram of a simple FMCW radar that uses separate\n",
        "> transmit and receive antennas is shown above. The radar consists of a waveform generator\n",
        "> that generates a sinusoidal signal of which the frequency varies\n",
        "> linearly around the required transmit frequency. The generated signal\n",
        "> is amplified to the required power level by the transmit amplifier\n",
        "> and routed to the transmit antenna via a coupler circuit where a copy\n",
        "> of the transmit signal is tapped off. The transmit antenna radiates\n",
        "> the transmit signal as an electromagnetic wave in a narrow beam\n",
        "> towards the target to be detected. When the wave encounters an object\n",
        "> that reflects electromagnetic waves, a fraction of of the energy\n",
        "> irradiating the target is reflected back to the receiver as a second\n",
        "> electromagnetic wave that propagates in the direction of the radar\n",
        "> system. When this wave encounters the receive antenna, the antenna\n",
        "> collects the energy in the wave energy impinging on it and converts\n",
        "> it to a fluctuating voltage that is fed to the mixer. The mixer\n",
        "> multiplies the received signal with a replica of the transmit signal\n",
        "> and produces a sinusoidal signal with a frequency equal to the\n",
        "> difference in frequency between the transmitted and received\n",
        "> signals. The low-pass filter ensures that the received signal is band\n",
        "> limited (i.e., does not contain frequencies that we don't care about)\n",
        "> and the receive amplifier strengthens the signal to a suitable\n",
        "> amplitude for the analog to digital converter (ADC) that feeds data\n",
        "> to the computer.\n",
        "\n",
        "To summarize, we should note that:\n",
        "\n",
        " - The data that reaches the computer consists of $N$ samples sampled\n",
        "   (from the multiplied, filtered signal) at a sample frequency of\n",
        "   $f_{s}$.\n",
        " - The **amplitude** of the returned signal varies depending on the\n",
        "   **strength of the reflection** (i.e., is a property of the target\n",
        "   object and the distance between the target and the radar).\n",
        " - The **frequency measured** is an indication of the **distance** of the\n",
        "   target object from the radar.\n",
        "\n",
        "<!--\n",
        "\n",
        "### Signal properties in the time domain\n",
        "\n",
        "The transmit signal is a sinusoidal signal with an instantaneous\n",
        "frequency that increases linearly with time, as shown in\n",
        "Fig. [fig:FMCW waveform](a).\n",
        "\n",
        "Starting at $f_{min}$, the frequency increases at a rate $S$ Hz/s to $f_{max}.$\n",
        "The frequency is then decreased rapidly back to $f_{min}$\n",
        "after which a next frequency sweep occurs.\n",
        "\n",
        "This signal is radiated by a directional transmit antenna. When the\n",
        "wave with propagation velocity $v\\approx300\\times10^{6}$ m/s (the\n",
        "propagation speed of electromagnetic waves in air is ever-so-slightly\n",
        "slower than the speed of light in a vacuum) hits a target at a range $R$,\n",
        "the echo will reach the radar after a time\n",
        "\n",
        "$$t_{d}=\\frac{2R}{v}.$$\n",
        "\n",
        "Here it is collected by the receive antenna and converted to a\n",
        "sinusoidally fluctuating voltage. The received signal is a replica of\n",
        "the transmitted signal, delayed by the transit time $t_{d}$ and is\n",
        "shown dashed in Fig. [fig:FMCW waveform](b).\n",
        "\n",
        "A radar is designed to detect targets up to a maximum range $R_{max}$.\n",
        "Echoes from maximum range reach the radar after a transit\n",
        "time $t_{dm}$ as shown in Fig. [fig:FMCW waveform](c).\n",
        "\n",
        "We note that there is a constant difference in frequency between the\n",
        "transmitted and received signals and this will be true for all targets\n",
        "after time $t_{s}$ until $t_{e}$. We conclude from\n",
        "Fig. [fig:FMCW waveform] that the frequency difference is given by\n",
        "\n",
        "$$f_{d}=S\\times t_{d}=\\frac{2SR}{v},$$\n",
        "\n",
        "where $T_{eff}=t_{e}-t_{s}=\\frac{N}{f_{s}}$ is the effective sweep duration\n",
        "of the radar. The frequency excursion of the sweep during $T_{eff}$ is\n",
        "the effective bandwidth of the radar, given by\n",
        "\n",
        "$$B_{eff}=f_{max}-f_{1}=ST_{eff}.$$\n",
        "\n",
        "We will see that the range resolution of the radar is determined by\n",
        "the effective bandwidth.\n",
        "\n",
        "\n",
        "Returning to Fig. [fig: block-diagram], the signal produced by the\n",
        "receiver at the input to the Analog to Digital Converter (ADC) when\n",
        "there is a single target is a sinusoid with constant amplitude,\n",
        "proportional to the amplitude of the echo, and constant frequency,\n",
        "proportional to the range to the target.\n",
        "\n",
        "-->\n",
        "\n",
        "![The frequency relationships in an FMCW radar with\n",
        " linear frequency modulation](../figures/FMCW_waveform.png)\n",
        "\n",
        "To start off, we'll generate some synthetic signals, after which we'll\n",
        "turn our focus to the output of an actual radar.\n",
        "\n",
        "Recall that the radar is increasing its frequency as it transmits at a\n",
        "rate of $S$ Hz/s.  After a certain amount of time, $t$, has passed,\n",
        "the frequency will now be $t S$ higher.  In that same time span, the\n",
        "radar signal has traveled $d = t / v$ meters, where $v$ is the speed of\n",
        "the transmitted wave through air (roughly the same as the speed of\n",
        "light, $3 \\times 10^8$ m/s).\n",
        "\n",
        "Combining the above observations, we can calculate the amount of time\n",
        "it would take the signal to travel to, bounce off, and return from a\n",
        "target that is distance $R$ away:\n",
        "\n",
        "$$ t_R = 2R / v $$\n",
        "\n",
        "Therefore, the change in frequency for a target at range $R$ will be:\n",
        "\n",
        "$$ f_{d}= t_R S = \\frac{2RS}{v}$$"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "pi = np.pi\n",
        "\n",
        "# Radar parameters\n",
        "fs = 78125          # Sampling frequency in Hz, i.e. we sample 78125\n",
        "                    # times per second\n",
        "\n",
        "ts = 1 / fs         # Sampling time, i.e. one sample is taken each\n",
        "                    # ts seconds\n",
        "\n",
        "Teff = 2048.0 * ts  # Total sampling time for 2048 samples\n",
        "                    # (AKA effective sweep duration) in seconds.\n",
        "\n",
        "Beff = 100e6        # Range of transmit signal frequency during the time the\n",
        "                    # radar samples, known as the \"effective bandwidth\"\n",
        "                    # (given in Hz)\n",
        "\n",
        "S = Beff / Teff     # Frequency sweep rate in Hz/s\n",
        "\n",
        "# Specification of targets.  We made these targets up, imagining they\n",
        "# are objects seen by the radar with the specified range and size\n",
        "\n",
        "R = np.array([100, 137, 154, 159,  180])  # Ranges (in meter)\n",
        "M = np.array([0.33, 0.2, 0.9, 0.02, 0.1])  # Target size\n",
        "P = np.array([0, pi / 2, pi / 3, pi / 5, pi / 6])  # Randomly chosen phase offsets\n",
        "\n",
        "t = np.arange(2048) * ts  # Sample times\n",
        "\n",
        "fd = 2 * S * R / 3E8      # Frequency differences for these targets\n",
        "\n",
        "# Generate five targets\n",
        "signals = np.cos(2 * pi * fd * t[:, np.newaxis] + P)\n",
        "\n",
        "# Save the signal associated with the first target as an example for\n",
        "# later inspection\n",
        "v_single = signals[:, 0]\n",
        "\n",
        "# Weigh the signals, according to target size, and sum, to generate\n",
        "# the combined signal seen by the radar\n",
        "v_sim = np.sum(M * signals, axis=1)\n",
        "\n",
        "## The above code is equivalent to:\n",
        "#\n",
        "# v0 = np.cos(2 * pi * fd[0] * t)\n",
        "# v1 = np.cos(2 * pi * fd[1] * t + pi / 2)\n",
        "# v2 = np.cos(2 * pi * fd[2] * t + pi / 3)\n",
        "# v3 = np.cos(2 * pi * fd[3] * t + pi / 5)\n",
        "# v4 = np.cos(2 * pi * fd[4] * t + pi / 6)\n",
        "#\n",
        "## Blend them together\n",
        "# v_single = v0\n",
        "# v_sim = (0.33 * v0) + (0.2 * v1) + (0.9 * v2) + (0.02 * v3) + (0.1 * v4)\n"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "Above, we generate a synthetic signal, $v_{single}$, received when\n",
        "looking at a single target (see figure below).  By counting the number\n",
        "of cycles seen in a given time period, we can compute the frequency of\n",
        "the signal and thus the distance to the target.\n",
        "\n",
        "A real radar will rarely receive only a single echo, though. The\n",
        "simulated signal $v_\\mathrm{sim}$ shows what a radar signal will look\n",
        "like with five targets at different ranges (including two close to one\n",
        "another at 154 and 159 meters), and $v_\\mathrm{actual}(t)$ shows the\n",
        "output signal obtained with an actual radar.  When multiple echoes add\n",
        "together, the result makes little intuitive sense; until, that is, we\n",
        "look at it more carefully through the lens of the discrete Fourier\n",
        "transform.\n",
        "\n",
        "<!--\n",
        "A synthetic radar signal is shown as $v_{1}(t)$ in Fig. [fig:radar time signals]\n",
        "for a radar with parameters $B_{eff}=100$ MHz, sampling frequency\n",
        "28125 Hz and N=2048 samples. The effective sweep time is\n",
        "$T_{eff}=\\frac{2048}{28125}=26.214$ ms. We can interpret this signal\n",
        "by counting the number of cycles in the graph — about\n",
        "$66\\frac{1}{2}$. The difference frequency is approximately\n",
        "$\\frac{66.5}{26.214E-3}=6.35$ kHz. With\n",
        "$S=\\frac{B_{eff}}{T_{eff}}=\\frac{100E6}{26.214E-3}=3.815\\times10^{9}$\n",
        "Hz/s, we can calculate the range to the target as\n",
        "$R=\\frac{vf_{d}}{2S}=\\frac{3\\times10^{8}\\times6.35\\times10^{3}}{2\\times3.815\\times10^{9}}=249.7$\n",
        "m.\n",
        "-->\n",
        "\n",
        "![Receiver output signals: (a) single simulated target\n",
        " (b) five simulated targets (c) actual radar data](../figures/generated/radar_time_signals.png)\n",
        "\n",
        "The real world radar data is read from a NumPy-format ``.npz`` file (a\n",
        "light-weight, cross platform and cross-version compatible storage\n",
        "format).  These files can be saved with the ``np.savez`` or\n",
        "``np.savez_compressed`` functions.  Note that SciPy's ``io`` submodule\n",
        "can also easily read other formats, such as MATLAB(R) and NetCDF\n",
        "files."
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "data = np.load('data/radar_scan_0.npz')\n",
        "\n",
        "# Load variable 'scan' from 'radar_scan_0.npz'\n",
        "scan = data['scan']\n",
        "\n",
        "# The dataset contains multiple measurements, each taken with the\n",
        "# radar pointing in a different direction.  Here we take one such as\n",
        "# measurement, at a specified azimuth (left-right position) and elevation\n",
        "# (up-down position).  The measurement has shape (2048,).\n",
        "\n",
        "v_actual = scan['samples'][5, 14, :]\n",
        "\n",
        "# The signal amplitude ranges from -2.5V to +2.5V.  The 14-bit\n",
        "# analogue-to-digital converter in the radar gives out integers\n",
        "# between -8192 to 8192.  We convert back to voltage by multiplying by\n",
        "# $(2.5 / 8192)$.\n",
        "\n",
        "v_actual = v_actual * (2.5 / 8192)\n"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "Since ``.npz``-files can store multiple variables, we have to select\n",
        "the one we want: ``data['scan']``.  That returns a\n",
        "*structured NumPy array* with the following fields:\n",
        "\n",
        "- **time** : unsigned 64-bit (8 byte) integer (`np.uint64`)\n",
        "- **size** : unsigned 32-bit (4 byte) integer (`np.uint32`)\n",
        "- **position**\n",
        "\n",
        "  - **az** : 32-bit float (`np.float32`)\n",
        "  - **el** : 32-bit float (`np.float32`)\n",
        "  - **region_type** : unsigned 8-bit (1 byte) integer (`np.uint8`)\n",
        "  - **region_ID** : unsigned 16-bit (2 byte) integer (`np.uint16`)\n",
        "  - **gain** : unsigned 8-bit (1 byte) integer (`np.uin8`)\n",
        "  - **samples** : 2048 unsigned 16-bit (2 byte) integers (`np.uint16`)\n",
        "\n",
        "While it is true that NumPy arrays are *homogeneous* (i.e., all the\n",
        "elements inside are the same), it does not mean that those elements\n",
        "cannot be compound elements, as is the case here.\n",
        "\n",
        "An individual field is accessed using dictionary syntax:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "azimuths = scan['position']['az']  # Get all azimuth measurements"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "To summarize what we've seen so far: the shown measurements\n",
        "($v_\\mathrm{sim}$ and $v_\\mathrm{actual}$) are the sum of sinusoidal\n",
        "signals reflected by each of several objects.  We need to determine\n",
        "each of the constituent components of these composite radar\n",
        "signals. The FFT is the tool that will do this for us.\n",
        "\n",
        "### Signal properties in the frequency domain\n",
        "\n",
        "First, we take the FFTs of our three signals (synthetic single target,\n",
        "synthetic multi-target, and real) and then display the\n",
        "positive frequency components (i.e., components $0$ to $N/2$).  These\n",
        "are called the *range traces* in radar terminology."
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "fig, axes = plt.subplots(3, 1, sharex=True, figsize=(4.8, 2.4))\n",
        "\n",
        "# Take FFTs of our signals.  Note the convention to name FFTs with a\n",
        "# capital letter.\n",
        "\n",
        "V_single = np.fft.fft(v_single)\n",
        "V_sim = np.fft.fft(v_sim)\n",
        "V_actual = np.fft.fft(v_actual)\n",
        "\n",
        "N = len(V_single)\n",
        "\n",
        "with plt.style.context('style/thinner.mplstyle'):\n",
        "    axes[0].plot(np.abs(V_single[:N // 2]))\n",
        "    axes[0].set_ylabel(\"$|V_\\mathrm{single}|$\")\n",
        "    axes[0].set_xlim(0, N // 2)\n",
        "    axes[0].set_ylim(0, 1100)\n",
        "\n",
        "    axes[1].plot(np.abs(V_sim[:N // 2]))\n",
        "    axes[1].set_ylabel(\"$|V_\\mathrm{sim} |$\")\n",
        "    axes[1].set_ylim(0, 1000)\n",
        "\n",
        "    axes[2].plot(np.abs(V_actual[:N // 2]))\n",
        "    axes[2].set_ylim(0, 750)\n",
        "    axes[2].set_ylabel(\"$|V_\\mathrm{actual}|$\")\n",
        "\n",
        "    axes[2].set_xlabel(\"FFT component $n$\")\n",
        "\n",
        "    for ax in axes:\n",
        "        ax.grid()"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Range traces for: (a) single simulated target, (b) mutiple simulated targets, (c) real-world targets\" --> \n",
        "\n",
        "Suddenly, the information makes sense!\n",
        "\n",
        "The plot for $|V_{0}|$ clearly shows a target at component 67, and\n",
        "for $|V_\\mathrm{sim}|$ shows the targets that produced the signal that was\n",
        "uninterpretable in the time domain. The real radar\n",
        "signal, $|V_\\mathrm{actual}|$ shows a large number of targets between\n",
        "component 400 and 500 with a large peak in component 443. This happens\n",
        "to be an echo return from a radar illuminating the high wall of an\n",
        "open-cast mine.\n",
        "\n",
        "To get useful information from the plot, we must determine the range!\n",
        "Again, we use the formula:\n",
        "\n",
        "$$R_{n}=\\frac{nv}{2B_{eff}}$$\n",
        "\n",
        "In radar terminology, each DFT component is known as a *range bin*.\n",
        "\n",
        "<!--\n",
        "The sinusoid associated with the first component of the DFT has a\n",
        "period exactly equal to the duration $T_{eff}$ of the time domain\n",
        "signal, so $f_{1}=\\frac{1}{T_{eff}}$. The other sinusoids in the\n",
        "Fourier series are harmonics of this, $f_{n}=\\frac{n}{T_{eff}}$.\n",
        "\n",
        "The ranges associated with the DFT components follow from\n",
        "Eqs. ([eq:difference frequency]) and ([eq:Effective bandwidth]) as\n",
        "\n",
        "$$R_{n}=\\frac{nv}{2B_{eff}}$$\n",
        "\n",
        "and the associated DFT components are known as *range bins* in radar\n",
        "terminology.\n",
        "\n",
        "-->\n",
        "\n",
        "This equation also defines the range resolution of the radar: targets\n",
        "will only be distinguishable if they are separated by more than two\n",
        "range bins, i.e.\n",
        "\n",
        "$$\\Delta R>\\frac{1}{B_{eff}}.$$\n",
        "\n",
        "This is a fundamental property of all types of radar.\n",
        "\n",
        "<!--\n",
        "The plot in Fig. ([fig:FFT range traces]) has a fundamental\n",
        "shortcoming. The observable dynamic range is the signal is very\n",
        "limited! We could easily have missed one of the targets in the trace\n",
        "for $V_{5}$!  To ameliorate the problem, we plot the same FFTs but\n",
        "this time against a logarithmic y-axis.  The traces were all\n",
        "normalized by dividing the amplitudes with the maximum value.\n",
        "-->\n",
        "\n",
        "This result is quite satisfying—but the dynamic range is so large\n",
        "that we could very easily miss some peaks.  Let's take the $\\log$ as\n",
        "before with the spectrogram:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "c = 3e8  # Approximately the speed of light and of\n",
        "         # electromagnetic waves in air\n",
        "\n",
        "fig, (ax0, ax1, ax2) = plt.subplots(3, 1)\n",
        "\n",
        "\n",
        "def dB(y):\n",
        "    \"Calculate the log ratio of y / max(y) in decibel.\"\n",
        "\n",
        "    y = np.abs(y)\n",
        "    y /= y.max()\n",
        "\n",
        "    return 20 * np.log10(y)\n",
        "\n",
        "\n",
        "def log_plot_normalized(x, y, ylabel, ax):\n",
        "    ax.plot(x, dB(y))\n",
        "    ax.set_ylabel(ylabel)\n",
        "    ax.grid()\n",
        "\n",
        "\n",
        "rng = np.arange(N // 2) * c / 2 / Beff\n",
        "\n",
        "with plt.style.context('style/thinner.mplstyle'):\n",
        "    log_plot_normalized(rng, V_single[:N // 2], \"$|V_0|$ [dB]\", ax0)\n",
        "    log_plot_normalized(rng, V_sim[:N // 2], \"$|V_5|$ [dB]\", ax1)\n",
        "    log_plot_normalized(rng, V_actual[:N // 2], \"$|V_{\\mathrm{actual}}|$ [dB]\", ax2)\n",
        "\n",
        "ax0.set_xlim(0, 300)  # Change x limits for these plots so that\n",
        "ax1.set_xlim(0, 300)  # we are better able to see the shape of the peaks.\n",
        "ax2.set_xlim(0, len(V_actual) // 2)\n",
        "ax2.set_xlabel('range')"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Logarithm of range traces\" -->\n",
        "\n",
        "The observable dynamic range is much improved in these plots. For\n",
        "instance, in the real radar signal the *noise floor* of the radar has\n",
        "become visible (i.e., the level where electronic noise in the system\n",
        "starts to limit the radar's ability to detect a target).\n",
        "\n",
        "<!-- The noise floor is ultimately caused by a phenomenon\n",
        "called thermal noise that is produced by all conducting elements that\n",
        "have resistance at temperatures above absolute zero, as well as by\n",
        "shot noise, a noise mechanism inherent in all the electronic devices\n",
        "that are used for processing the radar signal. The noise floor of a\n",
        "radar limits its ability to detect weak echoes. -->\n",
        "\n",
        "\n",
        "### Windowing, applied\n",
        "\n",
        "We're getting there, but in the spectrum of the simulated signal, we\n",
        "still cannot distinguish the peaks at 154 and 159 meters.  Who knows\n",
        "what we're missing in the real-world signal!  To sharpen the peaks,\n",
        "we'll return to our toolbox and make use of *windowing*.\n",
        "\n",
        "<!--\n",
        "\n",
        "The range traces in Fig. ([fig:Log range traces]) display a further\n",
        "serious shortcoming. The signals $v_{1}$ and $v_{5}$ are composed of\n",
        "pure sinusoids and we would ideally expect the FFT to produce line\n",
        "spectra for these signals. The logarithmic plots show steadily\n",
        "increasing values as the peaks are approached from both sides, to such\n",
        "an extent that one of the targets in the plot for $|v_{5}|$ can hardly\n",
        "be distinguished even though it is separated by several range bins\n",
        "from the large target. The broadening is caused by *side lobes* in the\n",
        "DFT. These are caused by an inherent clash between the properties of\n",
        "the signal we analyzed and the signal produced by the inverse DFT.\n",
        "\n",
        "-->\n",
        "\n",
        "Here are the signals used thus far in this example, windowed with a\n",
        "Kaiser window with $\\beta=6.1$:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "f, axes = plt.subplots(3, 1, sharex=True, figsize=(4.8, 2.8))\n",
        "\n",
        "t_ms = t * 1000  # Sample times in milli-second\n",
        "\n",
        "w = np.kaiser(N, 6.1)  # Kaiser window with beta = 6.1\n",
        "\n",
        "for n, (signal, label) in enumerate([(v_single, r'$v_0 [V]$'),\n",
        "                                     (v_sim, r'$v_5 [V]$'),\n",
        "                                     (v_actual, r'$v_{\\mathrm{actual}} [V]$')]):\n",
        "    with plt.style.context('style/thinner.mplstyle'):\n",
        "        axes[n].plot(t_ms, w * signal)\n",
        "        axes[n].set_ylabel(label)\n",
        "        axes[n].grid()\n",
        "\n",
        "axes[2].set_xlim(0, t_ms[-1])\n",
        "axes[2].set_xlabel('Time [ms]');"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Windowed signals for: (a) single simulated target, (b) multiple simulated targets, (c) real targets\" -->\n",
        "\n",
        "And the corresponding FFTs (or \"range traces\", in radar terms):"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "V_single_win = np.fft.fft(w * v_single)\n",
        "V_sim_win = np.fft.fft(w * v_sim)\n",
        "V_actual_win = np.fft.fft(w * v_actual)\n",
        "\n",
        "fig, (ax0, ax1,ax2) = plt.subplots(3, 1)\n",
        "\n",
        "with plt.style.context('style/thinner.mplstyle'):\n",
        "    log_plot_normalized(rng, V_single_win[:N // 2],\n",
        "                        r\"$|V_{0,\\mathrm{win}}|$ [dB]\", ax0)\n",
        "    log_plot_normalized(rng, V_sim_win[:N // 2],\n",
        "                        r\"$|V_{5,\\mathrm{win}}|$ [dB]\", ax1)\n",
        "    log_plot_normalized(rng, V_actual_win[:N // 2],\n",
        "                        r\"$|V_\\mathrm{actual,win}|$ [dB]\", ax2)\n",
        "\n",
        "ax0.set_xlim(0, 300)  # Change x limits for these plots so that\n",
        "ax1.set_xlim(0, 300)  # we are better able to see the shape of the peaks.\n",
        "\n",
        "ax1.annotate(\"New, previously unseen!\", (160, -35), xytext=(10, 15),\n",
        "             textcoords=\"offset points\", color='red', size='x-small',\n",
        "             arrowprops=dict(width=0.5, headwidth=3, headlength=4,\n",
        "                             fc='k', shrink=0.1));"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Range traces (spectrum) of windowed signals\" -->\n",
        "\n",
        "Compare these with the earlier range traces. There is a dramatic\n",
        "lowering in side lobe level, but at a price: the peaks have changed in\n",
        "shape, widening and becoming less peaky, thus lowering the radar\n",
        "resolution, that is, the ability of the radar to distinguish between\n",
        "two closely space targets. The choice of window is a compromise\n",
        "between side lobe level and resolution. Even so, referring to the\n",
        "trace for $V_\\mathrm{sim}$, windowing has dramatically increased our\n",
        "ability to distinguish the small target from its large neighbor.\n",
        "\n",
        "In the real radar data range trace windowing has also reduced the side\n",
        "lobes. This is most visible in the depth of the notch between the two\n",
        "groups of targets.\n",
        "\n",
        "### Radar Images\n",
        "\n",
        "Knowing how to analyze a single trace, we can expand to looking at\n",
        "radar images.\n",
        "\n",
        "The data is produced by a radar with a parabolic reflector antenna. It\n",
        "produces a highly directive round pencil beam with a $2^\\circ$\n",
        "spreading angle between half-power points. When directed with normal\n",
        "incidence at a plane, the radar will illuminate a spot of about $2$ meters in\n",
        "diameter at a distance of 60 meters.\n",
        "Outside this spot, the power drops off quite rapidly, but strong\n",
        "echoes from outside the spot will nevertheless still be visible.\n",
        "\n",
        "By varying the pencil beam's azimuth (left-right position) and\n",
        "elevation (up-down position), we can sweep it across the target area\n",
        "of interest.  When reflections are picked up, we can calculate the\n",
        "distance to the reflector (the object hit by the radar signal).\n",
        "Together with the current pencil beam azimuth and elevation, this\n",
        "defines the reflector's position in 3D.\n",
        "\n",
        "A rock slope consists of thousands of reflectors. A range bin can be\n",
        "thought of as a large sphere with the radar at its center that\n",
        "intersects the slope along a ragged line. The scatterers on this line\n",
        "will produce reflections in this range bin. The wavelength of the\n",
        "radar (distance the transmitted wave travels in one oscillation\n",
        "second) is about 30 mm. The reflections from scatterers separated by\n",
        "odd multiples of a quarter wavelength in range, about 7.5 mm, will\n",
        "tend to interfere destructively, while those from scatterers separated\n",
        "by multiples of a half wavelength will tend to interfere\n",
        "constructively at the radar. The reflections combine to produce\n",
        "apparent spots of strong reflections. This specific radar moves its\n",
        "antenna in order to scan small regions consisting of $20^\\circ$\n",
        "azimuth and $30^\\circ$ elevation bins scanned in steps of $0.5^\\circ$.\n",
        "\n",
        "We will now draw some contour plots of the resulting radar data.\n",
        "Please refer to the diagram below to see how the different slices are\n",
        "taken.  A first slice at fixed range shows the strength of echoes\n",
        "against elevation and azimuth.  Another two slices at fixed elevation\n",
        "and azimuth respectively shows the slope.  The stepped construction of\n",
        "the high wall in an opencast mine is visible in the azimuth plane.\n",
        "\n",
        "<img src=\"../figures/axes_slices.png\"\n",
        "     alt=\"Diagram showing azimuth, elevation and range slices through data volume\"/>"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "data = np.load('data/radar_scan_1.npz')\n",
        "scan = data['scan']\n",
        "\n",
        "# The signal amplitude ranges from -2.5V to +2.5V.  The 14-bit\n",
        "# analogue-to-digital converter in the radar gives out integers\n",
        "# between -8192 to 8192.  We convert back to voltage by multiplying by\n",
        "# $(2.5 / 8192)$.\n",
        "\n",
        "v = scan['samples'] * 2.5 / 8192\n",
        "win = np.hanning(N + 1)[:-1]\n",
        "\n",
        "# Take FFT for each measurement\n",
        "V = np.fft.fft(v * win, axis=2)[::-1, :, :N // 2]\n",
        "\n",
        "contours = np.arange(-40, 1, 2)\n",
        "\n",
        "# ignore MPL layout warnings\n",
        "import warnings\n",
        "warnings.filterwarnings('ignore', '.*Axes.*compatible.*tight_layout.*')\n",
        "\n",
        "f, axes = plt.subplots(2, 2, figsize=(4.8, 4.8), tight_layout=True)\n",
        "\n",
        "labels = ('Range', 'Azimuth', 'Elevation')\n",
        "\n",
        "def plot_slice(ax, radar_slice, title, xlabel, ylabel):\n",
        "    ax.contourf(dB(radar_slice), contours, cmap='magma_r')\n",
        "    ax.set_title(title)\n",
        "    ax.set_xlabel(xlabel)\n",
        "    ax.set_ylabel(ylabel)\n",
        "    ax.set_facecolor(plt.cm.magma_r(-40))\n",
        "\n",
        "with plt.style.context('style/thinner.mplstyle'):\n",
        "    plot_slice(axes[0, 0], V[:, :, 250], 'Range=250', 'Azimuth', 'Elevation')\n",
        "    plot_slice(axes[0, 1], V[:, 3, :], 'Azimuth=3', 'Range', 'Elevation')\n",
        "    plot_slice(axes[1, 0], V[6, :, :].T, 'Elevation=6', 'Azimuth', 'Range')\n",
        "    axes[1, 1].axis('off')"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"Contour plots of range traces along various axes (see diagram)\" -->\n",
        "\n",
        "#### 3D visualization\n",
        "\n",
        "We can also visualize the volume in three dimensions.\n",
        "\n",
        "We first compute the argmax (the index of the maximum value) in the\n",
        "range direction.  This should give an indication of the range at which\n",
        "the radar beam hit the rock slope.  Each argmax index is converted to\n",
        "a three-dimensional (elevation-azimuth-range) coordinate:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "r = np.argmax(V, axis=2)\n",
        "\n",
        "el, az = np.meshgrid(*[np.arange(s) for s in r.shape], indexing='ij')\n",
        "\n",
        "axis_labels = ['Elevation', 'Azimuth', 'Range']\n",
        "coords = np.column_stack((el.flat, az.flat, r.flat))"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "Taking these coordinates, we project them onto the plane (by dropping\n",
        "the range coordinate), and perform a Delaunay tesselation.  The\n",
        "tesselation returns a set of indices into our coordinates that define\n",
        "triangles (or simplices).  While the triangles are strictly speaking\n",
        "defined on the projected coordinates, we use our original coordinates\n",
        "for the reconstruction, thereby adding back the range component:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "from scipy import spatial\n",
        "\n",
        "d = spatial.Delaunay(coords[:, :2])\n",
        "simplexes = coords[d.vertices]"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "For display purposes, we swap the range axis to be the first:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "coords = np.roll(coords, shift=-1, axis=1)\n",
        "axis_labels = np.roll(axis_labels, shift=-1)"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "Now, Matplotlib's `trisurf` can be used to visualize the result:"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "# This import initializes Matplotlib's 3D machinery\n",
        "from mpl_toolkits.mplot3d import Axes3D\n",
        "\n",
        "# Set up the 3D axis\n",
        "f, ax = plt.subplots(1, 1, figsize=(4.8, 4.8),\n",
        "                     subplot_kw=dict(projection='3d'))\n",
        "\n",
        "with plt.style.context('style/thinner.mplstyle'):\n",
        "    ax.plot_trisurf(*coords.T, triangles=d.vertices, cmap='magma_r')\n",
        "\n",
        "    ax.set_xlabel(axis_labels[0])\n",
        "    ax.set_ylabel(axis_labels[1])\n",
        "    ax.set_zlabel(axis_labels[2], labelpad=-3)\n",
        "    ax.set_xticks([0, 5, 10, 15])\n",
        "\n",
        "# Adjust the camera position to match our diagram above\n",
        "ax.view_init(azim=-50);"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- caption text=\"3-D visualization of estimated rock slope position\" -->\n",
        "\n",
        "### Further applications of the FFT\n",
        "\n",
        "The examples above show just one of the uses of the FFT in\n",
        "radar. There are many others, such as movement (Doppler) measurement\n",
        "and target recognition.  The fast Fourier transform is pervasive, and is\n",
        "seen anywhere from Magnetic Resonance Imaging (MRI) to statistics.\n",
        "With the basic techniques that this chapter outlines in hand, you\n",
        "should be well equipped to use it!\n",
        "\n",
        "### Further reading\n",
        "\n",
        "On the Fourier transform:\n",
        "\n",
        "- A. Papoulis, *The Fourier Integral and Its Applications*,\n",
        "  McGraw-Hill, 1960.\n",
        "- Ronald A. Bracewell, *The Fourier Transform and Its Applications*,\n",
        "  McGraw-Hill, 1986.\n",
        "\n",
        "On radar signal processing:\n",
        "\n",
        "- Mark A. Richards, *Principles of Modern Radar: Basic Principles*,\n",
        "  SciTech, 2010\n",
        "- Mark A. Richards, *Fundamentals of Radar Signal Processing*,\n",
        "  McGraw-Hill, 2014.\n",
        "\n",
        "<!-- exercise begin -->\n",
        "\n",
        "**Exercise:** The FFT is often used to speed up image convolution\n",
        "(convolution is the application of a moving filter mask).  Convolve an\n",
        "image with ``np.ones((5, 5))``, using a) numpy's ``np.convolve`` and\n",
        "b) ``np.fft.fft2``.  Confirm that the results are identical.\n",
        "\n",
        "Hints:\n",
        "\n",
        " - The convolution of `x` and `y` is equivalent to `ifft2(X * Y)`, where\n",
        "   `X` and `Y` are the FFTs of x and y respectively.\n",
        " - In order to multiply `X` and `Y`, they have to be the same size.\n",
        "   Use `np.pad` to extend `x` and `y` with zeros (toward the right and\n",
        "   bottom) *before* taking their FFT.\n",
        " - You may see some edge effects.  These can be removed by increasing\n",
        "   the padding size, so that both `x` and `y` have dimensions\n",
        "   `shape(x) + shape(y) - 1`.\n",
        "\n",
        "<!-- solution begin -->\n",
        "\n",
        "**Solution:**"
      ],
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": [
        "from scipy import signal\n",
        "\n",
        "x = np.random.random((50, 50))\n",
        "y = np.ones((5, 5))\n",
        "\n",
        "L = x.shape[0] + y.shape[0] - 1\n",
        "Px = L - x.shape[0]\n",
        "Py = L - y.shape[0]\n",
        "\n",
        "xx = np.pad(x, ((0, Px), (0, Px)), mode='constant')\n",
        "yy = np.pad(y, ((0, Py), (0, Py)), mode='constant')\n",
        "\n",
        "zz = np.fft.ifft2(np.fft.fft2(xx) * np.fft.fft2(yy)).real\n",
        "print('Resulting shape:', zz.shape, ' <-- Why?')\n",
        "\n",
        "z = signal.convolve2d(x, y)\n",
        "\n",
        "print('Results are equal?', np.allclose(zz, z))"
      ],
      "outputs": [],
      "execution_count": null,
      "metadata": {}
    },
    {
      "cell_type": "markdown",
      "source": [
        "<!-- solution end -->\n",
        "\n",
        "<!-- exercise end -->"
      ],
      "metadata": {}
    }
  ],
  "metadata": {},
  "nbformat": 4,
  "nbformat_minor": 4
}

```



---


###  Node Cheat Sheet

```js
/*************************
 * //NODE-JS-CHEAT-SHEET *
 *************************/
var http = require('http');
// An example of a web server written with Node which responds with 'Hello World'.
// To run the server, put the code into a file called example.js and execute it with the node program.
http.createServer(function (request, response) {
response.writeHead(200, {'Content-Type': 'text/plain'});
response.end('Hello World\n');
}).listen(8124);
console.log('Server running at http://127.0.0.1:8124/');
/* *******************************************************************************************
* GLOBAL OBJECTS
* http://nodejs.org/api/globals.html
* ******************************************************************************************* */
// In browsers, the top-level scope is the global scope.
// That means that in browsers if you're in the global scope var something will define a global variable.
// In Node this is different. The top-level scope is not the global scope; var something inside a Node module will be local to that module.
__filename;  // The filename of the code being executed. (absolute path)
__dirname;   // The name of the directory that the currently executing script resides in. (absolute path)
module;      // A reference to the current module. In particular module.exports is used for defining what a module exports and makes available through require().
exports;     // A reference to the module.exports that is shorter to type.
process;     // The process object is a global object and can be accessed from anywhere. It is an instance of EventEmitter.
Buffer;      // The Buffer class is a global type for dealing with binary data directly.
* CONSOLE
* http://nodejs.org/api/console.html
console.log([data], [...]);             // Prints to stdout with newline.
console.info([data], [...]);            // Same as console.log.
console.error([data], [...]);           // Same as console.log but prints to stderr.
console.warn([data], [...]);            // Same as console.error.
console.dir(obj);                       // Uses util.inspect on obj and prints resulting string to stdout.
console.time(label);                    // Mark a time.
console.timeEnd(label);                 // Finish timer, record output.
console.trace(label);                   // Print a stack trace to stderr of the current position.
console.assert(expression, [message]);  // Same as assert.ok() where if the expression evaluates as false throw an AssertionError with message.
* TIMERS
* http://nodejs.org/api/timers.html
setTimeout(callback, delay, [arg], [...]);   // To schedule execution of a one-time callback after delay milliseconds. Optionally you can also pass arguments to the callback.
clearTimeout(t);                             // Stop a timer that was previously created with setTimeout().
setInterval(callback, delay, [arg], [...]);  // To schedule the repeated execution of callback every delay milliseconds. Optionally you can also pass arguments to the callback.
clearInterval(t);                            // Stop a timer that was previously created with setInterval().
setImmediate(callback, [arg], [...]);        // To schedule the "immediate" execution of callback after I/O events callbacks and before setTimeout and setInterval.
clearImmediate(immediateObject);             // Stop a timer that was previously created with setImmediate().
unref();  // Allow you to create a timer that is active but if it is the only item left in the event loop, node won't keep the program running.
ref();    // If you had previously unref()d a timer you can call ref() to explicitly request the timer hold the program open.
* MODULES
* http://nodejs.org/api/modules.html
var module = require('./module.js');    // Loads the module module.js in the same directory.
module.require('./another_module.js');  // load another_module as if require() was called from the module itself.
module.id;        // The identifier for the module. Typically this is the fully resolved filename.
module.filename;  // The fully resolved filename to the module.
module.loaded;    // Whether or not the module is done loading, or is in the process of loading.
module.parent;    // The module that required this one.
module.children;  // The module objects required by this one.
exports.area = function (r) {
return Math.PI * r * r;
};
// If you want the root of your module's export to be a function (such as a constructor)
// or if you want to export a complete object in one assignment instead of building it one property at a time,
// assign it to module.exports instead of exports.
module.exports = function(width) {
return {
area: function() {
return width * width;
}
* PROCESS
* http://nodejs.org/api/process.html
process.on('exit', function(code) {});              // Emitted when the process is about to exit
process.on('uncaughtException', function(err) {});  // Emitted when an exception bubbles all the way back to the event loop. (should not be used)
process.stdout;           // A writable stream to stdout.
process.stderr;           // A writable stream to stderr.
process.stdin;            // A readable stream for stdin.
process.argv;             // An array containing the command line arguments.
process.env;              // An object containing the user environment.
process.execPath;         // This is the absolute pathname of the executable that started the process.
process.execArgv;         // This is the set of node-specific command line options from the executable that started the process.
process.arch;             // What processor architecture you're running on: 'arm', 'ia32', or 'x64'.
process.config;           // An Object containing the JavaScript representation of the configure options that were used to compile the current node executable.
process.pid;              // The PID of the process.
process.platform;         // What platform you're running on: 'darwin', 'freebsd', 'linux', 'sunos' or 'win32'.
process.title;            // Getter/setter to set what is displayed in 'ps'.
process.version;          // A compiled-in property that exposes NODE_VERSION.
process.versions;         // A property exposing version strings of node and its dependencies.
process.abort();          // This causes node to emit an abort. This will cause node to exit and generate a core file.
process.chdir(dir);       // Changes the current working directory of the process or throws an exception if that fails.
process.cwd();            // Returns the current working directory of the process.
process.exit([code]);     // Ends the process with the specified code. If omitted, exit uses the 'success' code 0.
process.getgid();         // Gets the group identity of the process.
process.setgid(id);       // Sets the group identity of the process.
process.getuid();         // Gets the user identity of the process.
process.setuid(id);       // Sets the user identity of the process.
process.getgroups();      // Returns an array with the supplementary group IDs.
process.setgroups(grps);  // Sets the supplementary group IDs.
process.initgroups(user, extra_grp);  // Reads /etc/group and initializes the group access list, using all groups of which the user is a member.
process.kill(pid, [signal]);          // Send a signal to a process. pid is the process id and signal is the string describing the signal to send.
process.memoryUsage();                // Returns an object describing the memory usage of the Node process measured in bytes.
process.nextTick(callback);           // On the next loop around the event loop call this callback.
process.maxTickDepth;                 // Callbacks passed to process.nextTick will usually be called at the end of the current flow of execution, and are thus approximately as fast as calling a function synchronously.
process.umask([mask]);                // Sets or reads the process's file mode creation mask.
process.uptime();                     // Number of seconds Node has been running.
process.hrtime();                     // Returns the current high-resolution real time in a [seconds, nanoseconds] tuple Array.
* CHILD PROCESS
* http://nodejs.org/api/child_process.html
// Node provides a tri-directional popen facility through the child_process module.
// It is possible to stream data through a child's stdin, stdout, and stderr in a fully non-blocking way.
ChildProcess;                                                 // Class. ChildProcess is an EventEmitter.
child.stdin;                                                  // A Writable Stream that represents the child process's stdin
child.stdout;                                                 // A Readable Stream that represents the child process's stdout
child.stderr;                                                 // A Readable Stream that represents the child process's stderr.
child.pid;                                                    // The PID of the child process
child.connected;                                              // If .connected is false, it is no longer possible to send messages
child.kill([signal]);                                         // Send a signal to the child process
child.send(message, [sendHandle]);                            // When using child_process.fork() you can write to the child using child.send(message, [sendHandle]) and messages are received by a 'message' event on the child.
child.disconnect();                                           // Close the IPC channel between parent and child, allowing the child to exit gracefully once there are no other connections keeping it alive.
child_process.spawn(command, [args], [options]);              // Launches a new process with the given command, with command line arguments in args. If omitted, args defaults to an empty Array.
child_process.exec(command, [options], callback);             // Runs a command in a shell and buffers the output.
child_process.execFile(file, [args], [options], [callback]);  // Runs a command in a shell and buffers the output.
child_process.fork(modulePath, [args], [options]);            // This is a special case of the spawn() functionality for spawning Node processes. In addition to having all the methods in a normal ChildProcess instance, the returned object has a communication channel built-in. 
* UTIL
* http://nodejs.org/api/util.html
// These functions are in the module 'util'. Use require('util') to access them.
util.format(format, [...]);    // Returns a formatted string using the first argument as a printf-like format. (%s, %d, %j)
util.debug(string);            // A synchronous output function. Will block the process and output string immediately to stderr.
util.error([...]);             // Same as util.debug() except this will output all arguments immediately to stderr.
util.puts([...]);              // A synchronous output function. Will block the process and output all arguments to stdout with newlines after each argument.
util.print([...]);             // A synchronous output function. Will block the process, cast each argument to a string then output to stdout. (no newlines)
util.log(string);              // Output with timestamp on stdout.
util.inspect(object, [opts]);  // Return a string representation of object, which is useful for debugging. (options: showHidden, depth, colors, customInspect)
util.isArray(object);          // Returns true if the given "object" is an Array. false otherwise.
util.isRegExp(object);         // Returns true if the given "object" is a RegExp. false otherwise.
util.isDate(object);           // Returns true if the given "object" is a Date. false otherwise.
util.isError(object);          // Returns true if the given "object" is an Error. false otherwise.
util.promisify(fn)             // Takes a function whose last argument is a callback and returns a version that returns promises.
util.inherits(constructor, superConstructor);  // Inherit the prototype methods from one constructor into another.
* EVENTS
* http://nodejs.org/api/events.html
// All objects which emit events are instances of events.EventEmitter. You can access this module by doing: require("events");
// To access the EventEmitter class, require('events').EventEmitter.
// All EventEmitters emit the event 'newListener' when new listeners are added and 'removeListener' when a listener is removed.
emitter.addListener(event, listener);        // Adds a listener to the end of the listeners array for the specified event.
emitter.on(event, listener);                 // Same as emitter.addListener().
emitter.once(event, listener);               // Adds a one time listener for the event. This listener is invoked only the next time the event is fired, after which it is removed.
emitter.removeListener(event, listener);     // Remove a listener from the listener array for the specified event.
emitter.removeAllListeners([event]);         // Removes all listeners, or those of the specified event.
emitter.setMaxListeners(n);                  // By default EventEmitters will print a warning if more than 10 listeners are added for a particular event.
emitter.listeners(event);                    // Returns an array of listeners for the specified event.
emitter.emit(event, [arg1], [arg2], [...]);  // Execute each of the listeners in order with the supplied arguments. Returns true if event had listeners, false otherwise.
EventEmitter.listenerCount(emitter, event);  // Return the number of listeners for a given event.
* STREAM
* http://nodejs.org/api/stream.html
// A stream is an abstract interface implemented by various objects in Node. For example a request to an HTTP server is a stream, as is stdout.
// Streams are readable, writable, or both. All streams are instances of EventEmitter.
// The Readable stream interface is the abstraction for a source of data that you are reading from.
// In other words, data comes out of a Readable stream.
// A Readable stream will not start emitting data until you indicate that you are ready to receive it.
// Examples of readable streams include: http responses on the client, http requests on the server, fs read streams
// zlib streams, crypto streams, tcp sockets, child process stdout and stderr, process.stdin.
var readable = getReadableStreamSomehow();
readable.on('readable', function() {});   // When a chunk of data can be read from the stream, it will emit a 'readable' event.
readable.on('data', function(chunk) {});  // If you attach a data event listener, then it will switch the stream into flowing mode, and data will be passed to your handler as soon as it is available.
readable.on('end', function() {});        // This event fires when there will be no more data to read.
readable.on('close', function() {});      // Emitted when the underlying resource (for example, the backing file descriptor) has been closed. Not all streams will emit this.
readable.on('error', function() {});      // Emitted if there was an error receiving data.
// The read() method pulls some data out of the internal buffer and returns it. If there is no data available, then it will return null.
// This method should only be called in non-flowing mode. In flowing-mode, this method is called automatically until the internal buffer is drained.
readable.read([size]);
readable.setEncoding(encoding);           // Call this function to cause the stream to return strings of the specified encoding instead of Buffer objects.
readable.resume();                        // This method will cause the readable stream to resume emitting data events.
readable.pause();                         // This method will cause a stream in flowing-mode to stop emitting data events.
readable.pipe(destination, [options]);    // This method pulls all the data out of a readable stream, and writes it to the supplied destination, automatically managing the flow so that the destination is not overwhelmed by a fast readable stream.
readable.unpipe([destination]);           // This method will remove the hooks set up for a previous pipe() call. If the destination is not specified, then all pipes are removed.
readable.unshift(chunk);                  // This is useful in certain cases where a stream is being consumed by a parser, which needs to "un-consume" some data that it has optimistically pulled out of the source, so that the stream can be passed on to some other party.
// The Writable stream interface is an abstraction for a destination that you are writing data to.
// Examples of writable streams include: http requests on the client, http responses on the server, fs write streams,
// zlib streams, crypto streams, tcp sockets, child process stdin, process.stdout, process.stderr.
var writer = getWritableStreamSomehow();
writable.write(chunk, [encoding], [callback]);  // This method writes some data to the underlying system, and calls the supplied callback once the data has been fully handled.
writer.once('drain', write);                    // If a writable.write(chunk) call returns false, then the drain event will indicate when it is appropriate to begin writing more data to the stream.
writable.end([chunk], [encoding], [callback]);  // Call this method when no more data will be written to the stream.
writer.on('finish', function() {});             // When the end() method has been called, and all data has been flushed to the underlying system, this event is emitted.
writer.on('pipe', function(src) {});            // This is emitted whenever the pipe() method is called on a readable stream, adding this writable to its set of destinations.
writer.on('unpipe', function(src) {});          // This is emitted whenever the unpipe() method is called on a readable stream, removing this writable from its set of destinations.
writer.on('error', function(src) {});           // Emitted if there was an error when writing or piping data.
// Duplex streams are streams that implement both the Readable and Writable interfaces. See above for usage.
// Examples of Duplex streams include: tcp sockets, zlib streams, crypto streams.
// Transform streams are Duplex streams where the output is in some way computed from the input. They implement both the Readable and Writable interfaces. See above for usage.
// Examples of Transform streams include: zlib streams, crypto streams.
* FILE SYSTEM
* http://nodejs.org/api/fs.html
// To use this module do require('fs').
// All the methods have asynchronous and synchronous forms.
fs.rename(oldPath, newPath, callback);  // Asynchronous rename. No arguments other than a possible exception are given to the completion callback.Asynchronous ftruncate. No arguments other than a possible exception are given to the completion callback.
fs.renameSync(oldPath, newPath);        // Synchronous rename.
fs.ftruncate(fd, len, callback);        // Asynchronous ftruncate. No arguments other than a possible exception are given to the completion callback.
fs.ftruncateSync(fd, len);              // Synchronous ftruncate.
fs.truncate(path, len, callback);       // Asynchronous truncate. No arguments other than a possible exception are given to the completion callback.
fs.truncateSync(path, len);             // Synchronous truncate.
fs.chown(path, uid, gid, callback);     // Asynchronous chown. No arguments other than a possible exception are given to the completion callback.
fs.chownSync(path, uid, gid);           // Synchronous chown.
fs.fchown(fd, uid, gid, callback);      // Asynchronous fchown. No arguments other than a possible exception are given to the completion callback.
fs.fchownSync(fd, uid, gid);            // Synchronous fchown.
fs.lchown(path, uid, gid, callback);    // Asynchronous lchown. No arguments other than a possible exception are given to the completion callback.
fs.lchownSync(path, uid, gid);          // Synchronous lchown.
fs.chmod(path, mode, callback);         // Asynchronous chmod. No arguments other than a possible exception are given to the completion callback.
fs.chmodSync(path, mode);               // Synchronous chmod.
fs.fchmod(fd, mode, callback);          // Asynchronous fchmod. No arguments other than a possible exception are given to the completion callback.
fs.fchmodSync(fd, mode);                // Synchronous fchmod.
fs.lchmod(path, mode, callback);        // Asynchronous lchmod. No arguments other than a possible exception are given to the completion callback.
fs.lchmodSync(path, mode);              // Synchronous lchmod.
fs.stat(path, callback);                // Asynchronous stat. The callback gets two arguments (err, stats) where stats is a fs.Stats object. 
fs.statSync(path);                      // Synchronous stat. Returns an instance of fs.Stats.
fs.lstat(path, callback);               // Asynchronous lstat. The callback gets two arguments (err, stats) where stats is a fs.Stats object. lstat() is identical to stat(), except that if path is a symbolic link, then the link itself is stat-ed, not the file that it refers to.
fs.lstatSync(path);                     // Synchronous lstat. Returns an instance of fs.Stats.
fs.fstat(fd, callback);                 // Asynchronous fstat. The callback gets two arguments (err, stats) where stats is a fs.Stats object. fstat() is identical to stat(), except that the file to be stat-ed is specified by the file descriptor fd.
fs.fstatSync(fd);                       // Synchronous fstat. Returns an instance of fs.Stats.
fs.link(srcpath, dstpath, callback);             // Asynchronous link. No arguments other than a possible exception are given to the completion callback.
fs.linkSync(srcpath, dstpath);                   // Synchronous link.
fs.symlink(srcpath, dstpath, [type], callback);  // Asynchronous symlink. No arguments other than a possible exception are given to the completion callback. The type argument can be set to 'dir', 'file', or 'junction' (default is 'file') and is only available on Windows (ignored on other platforms)
fs.symlinkSync(srcpath, dstpath, [type]);        // Synchronous symlink.
fs.readlink(path, callback);                     // Asynchronous readlink. The callback gets two arguments (err, linkString).
fs.readlinkSync(path);                           // Synchronous readlink. Returns the symbolic link's string value.
fs.unlink(path, callback);                       // Asynchronous unlink. No arguments other than a possible exception are given to the completion callback.
fs.unlinkSync(path);                             // Synchronous unlink.
fs.realpath(path, [cache], callback);     // Asynchronous realpath. The callback gets two arguments (err, resolvedPath).
fs.realpathSync(path, [cache]);           // Synchronous realpath. Returns the resolved path.
fs.rmdir(path, callback);                 // Asynchronous rmdir. No arguments other than a possible exception are given to the completion callback.
fs.rmdirSync(path);                       // Synchronous rmdir.
fs.mkdir(path, [mode], callback);         // Asynchronous mkdir. No arguments other than a possible exception are given to the completion callback. mode defaults to 0777.
fs.mkdirSync(path, [mode]);               // Synchronous mkdir.
fs.readdir(path, callback);               // Asynchronous readdir. Reads the contents of a directory. The callback gets two arguments (err, files) where files is an array of the names of the files in the directory excluding '.' and '..'.
fs.readdirSync(path);                     // Synchronous readdir. Returns an array of filenames excluding '.' and '..'.
fs.close(fd, callback);                   // Asynchronous close. No arguments other than a possible exception are given to the completion callback.
fs.closeSync(fd);                         // Synchronous close.
fs.open(path, flags, [mode], callback);   // Asynchronous file open.
fs.openSync(path, flags, [mode]);         // Synchronous version of fs.open().
fs.utimes(path, atime, mtime, callback);  // Change file timestamps of the file referenced by the supplied path.
fs.utimesSync(path, atime, mtime);        // Synchronous version of fs.utimes().
fs.futimes(fd, atime, mtime, callback);   // Change the file timestamps of a file referenced by the supplied file descriptor.
fs.futimesSync(fd, atime, mtime);         // Synchronous version of fs.futimes().
fs.fsync(fd, callback);                   // Asynchronous fsync. No arguments other than a possible exception are given to the completion callback.
fs.fsyncSync(fd);                         // Synchronous fsync.
fs.write(fd, buffer, offset, length, position, callback);  // Write buffer to the file specified by fd.
fs.writeSync(fd, buffer, offset, length, position);        // Synchronous version of fs.write(). Returns the number of bytes written.
fs.read(fd, buffer, offset, length, position, callback);   // Read data from the file specified by fd.
fs.readSync(fd, buffer, offset, length, position);         // Synchronous version of fs.read. Returns the number of bytesRead.
fs.readFile(filename, [options], callback);                // Asynchronously reads the entire contents of a file.
fs.readFileSync(filename, [options]);                      // Synchronous version of fs.readFile. Returns the contents of the filename. If the encoding option is specified then this function returns a string. Otherwise it returns a buffer.
fs.writeFile(filename, data, [options], callback);   // Asynchronously writes data to a file, replacing the file if it already exists. data can be a string or a buffer.
fs.writeFileSync(filename, data, [options]);         // The synchronous version of fs.writeFile.
fs.appendFile(filename, data, [options], callback);  // Asynchronously append data to a file, creating the file if it not yet exists. data can be a string or a buffer.
fs.appendFileSync(filename, data, [options]);        // The synchronous version of fs.appendFile.
fs.watch(filename, [options], [listener]);           // Watch for changes on filename, where filename is either a file or a directory. The returned object is a fs.FSWatcher. The listener callback gets two arguments (event, filename). event is either 'rename' or 'change', and filename is the name of the file which triggered the event.
fs.exists(path, callback);                           // Test whether or not the given path exists by checking with the file system. Then call the callback argument with either true or false. (should not be used)
fs.existsSync(path);                                 // Synchronous version of fs.exists. (should not be used)
// fs.Stats: objects returned from fs.stat(), fs.lstat() and fs.fstat() and their synchronous counterparts are of this type.
stats.isFile();
stats.isDirectory()
stats.isBlockDevice()
stats.isCharacterDevice()
stats.isSymbolicLink()  // (only valid with fs.lstat())
stats.isFIFO()
stats.isSocket()
fs.createReadStream(path, [options]);   // Returns a new ReadStream object.
fs.createWriteStream(path, [options]);  // Returns a new WriteStream object.
* PATH
// Use require('path') to use this module.
// This module contains utilities for handling and transforming file paths.
// Almost all these methods perform only string transformations.
// The file system is not consulted to check whether paths are valid.
path.normalize(p);                    // Normalize a string path, taking care of '..' and '.' parts.
path.join([path1], [path2], [...]);   // Join all arguments together and normalize the resulting path.
path.resolve([from ...], to);         // Resolves 'to' to an absolute path.
path.relative(from, to);              // Solve the relative path from 'from' to 'to'.
path.dirname(p);                      // Return the directory name of a path. Similar to the Unix dirname command.
path.basename(p, [ext]);              // Return the last portion of a path. Similar to the Unix basename command.
path.extname(p);                      // Return the extension of the path, from the last '.' to end of string in the last portion of the path.
path.sep;                             // The platform-specific file separator. '\\' or '/'.
path.delimiter;                       // The platform-specific path delimiter, ';' or ':'.
* HTTP
* http://nodejs.org/api/http.html
// To use the HTTP server and client one must require('http').
http.STATUS_CODES;                                             // A collection of all the standard HTTP response status codes, and the short description of each.
http.request(options, [callback]);                             // This function allows one to transparently issue requests.
http.get(options, [callback]);                                 // Set the method to GET and calls req.end() automatically.
server = http.createServer([requestListener]);                 // Returns a new web server object. The requestListener is a function which is automatically added to the 'request' event.
server.listen(port, [hostname], [backlog], [callback]);        // Begin accepting connections on the specified port and hostname.
server.listen(path, [callback]);                               // Start a UNIX socket server listening for connections on the given path.
server.listen(handle, [callback]);                             // The handle object can be set to either a server or socket (anything with an underlying _handle member), or a {fd: <n>} object.
server.close([callback]);                                      // Stops the server from accepting new connections. 
server.setTimeout(msecs, callback);                            // Sets the timeout value for sockets, and emits a 'timeout' event on the Server object, passing the socket as an argument, if a timeout occurs.
# Node JS Quick Reference
server.maxHeadersCount;  // Limits maximum incoming headers count, equal to 1000 by default. If set to 0 - no limit will be applied.
server.timeout;          // The number of milliseconds of inactivity before a socket is presumed to have timed out.
server.on('request', function (request, response) { });        // Emitted each time there is a request.
server.on('connection', function (socket) { });                // When a new TCP stream is established.
server.on('close', function () { });                           // Emitted when the server closes.
server.on('checkContinue', function (request, response) { });  // Emitted each time a request with an http Expect: 100-continue is received.
server.on('connect', function (request, socket, head) { });    // Emitted each time a client requests a http CONNECT method.
server.on('upgrade', function (request, socket, head) { });    // Emitted each time a client requests a http upgrade.
server.on('clientError', function (exception, socket) { });    // If a client connection emits an 'error' event - it will forwarded here.
request.write(chunk, [encoding]);                              // Sends a chunk of the body.
request.end([data], [encoding]);                               // Finishes sending the request. If any parts of the body are unsent, it will flush them to the stream.
request.abort();                                               // Aborts a request.
request.setTimeout(timeout, [callback]);                       // Once a socket is assigned to this request and is connected socket.setTimeout() will be called.
request.setNoDelay([noDelay]);                                 // Once a socket is assigned to this request and is connected socket.setNoDelay() will be called.
request.setSocketKeepAlive([enable], [initialDelay]);          // Once a socket is assigned to this request and is connected socket.setKeepAlive() will be called.
request.on('response', function(response) { });                // Emitted when a response is received to this request. This event is emitted only once.
request.on('socket', function(socket) { });                    // Emitted after a socket is assigned to this request.
request.on('connect', function(response, socket, head) { });   // Emitted each time a server responds to a request with a CONNECT method. If this event isn't being listened for, clients receiving a CONNECT method will have their connections closed.
request.on('upgrade', function(response, socket, head) { });   // Emitted each time a server responds to a request with an upgrade. If this event isn't being listened for, clients receiving an upgrade header will have their connections closed.
request.on('continue', function() { });                        // Emitted when the server sends a '100 Continue' HTTP response, usually because the request contained 'Expect: 100-continue'. This is an instruction that the client should send the request body.
response.write(chunk, [encoding]);                             // This sends a chunk of the response body. If this merthod is called and response.writeHead() has not been called, it will switch to implicit header mode and flush the implicit headers.
response.writeContinue();                                      // Sends a HTTP/1.1 100 Continue message to the client, indicating that the request body should be sent.
response.writeHead(statusCode, [reasonPhrase], [headers]);     // Sends a response header to the request.
response.setTimeout(msecs, callback);                          // Sets the Socket's timeout value to msecs. If a callback is provided, then it is added as a listener on the 'timeout' event on the response object.
response.setHeader(name, value);                               // Sets a single header value for implicit headers. If this header already exists in the to-be-sent headers, its value will be replaced. Use an array of strings here if you need to send multiple headers with the same name.
response.getHeader(name);                                      // Reads out a header that's already been queued but not sent to the client. Note that the name is case insensitive.
response.removeHeader(name);                                   // Removes a header that's queued for implicit sending.
response.addTrailers(headers);                                 // This method adds HTTP trailing headers (a header but at the end of the message) to the response.
response.end([data], [encoding]);                              // This method signals to the server that all of the response headers and body have been sent; that server should consider this message complete. The method, response.end(), MUST be called on each response.
response.statusCode;                                           // When using implicit headers (not calling response.writeHead() explicitly), this property controls the status code that will be sent to the client when the headers get flushed.
response.headersSent;                                          // Boolean (read-only). True if headers were sent, false otherwise.
response.sendDate;                                             // When true, the Date header will be automatically generated and sent in the response if it is not already present in the headers. Defaults to true.
response.on('close', function () { });  // Indicates that the underlying connection was terminated before response.end() was called or able to flush.
response.on('finish', function() { });  // Emitted when the response has been sent. 
message.httpVersion;                    // In case of server request, the HTTP version sent by the client. In the case of client response, the HTTP version of the connected-to server.
message.headers;                        // The request/response headers object.
message.trailers;                       // The request/response trailers object. Only populated after the 'end' event.
message.method;                         // The request method as a string. Read only. Example: 'GET', 'DELETE'.
message.url;                            // Request URL string. This contains only the URL that is present in the actual HTTP request.
message.statusCode;                     // The 3-digit HTTP response status code. E.G. 404.
message.socket;                         // The net.Socket object associated with the connection.
message.setTimeout(msecs, callback);    // Calls message.connection.setTimeout(msecs, callback).
* URL
* http://nodejs.org/api/url.html
// This module has utilities for URL resolution and parsing. Call require('url') to use it.
url.parse(urlStr, [parseQueryString], [slashesDenoteHost]);  // Take a URL string, and return an object.
url.format(urlObj);                                          // Take a parsed URL object, and return a formatted URL string.
url.resolve(from, to);                                       // Take a base URL, and a href URL, and resolve them as a browser would for an anchor tag.
* QUERY STRING
* http://nodejs.org/api/querystring.html
// This module provides utilities for dealing with query strings. Call require('querystring') to use it.
querystring.stringify(obj, [sep], [eq]);         // Serialize an object to a query string. Optionally override the default separator ('&') and assignment ('=') characters.
querystring.parse(str, [sep], [eq], [options]);  // Deserialize a query string to an object. Optionally override the default separator ('&') and assignment ('=') characters.
* ASSERT
* http://nodejs.org/api/assert.html
// This module is used for writing unit tests for your applications, you can access it with require('assert').
assert.fail(actual, expected, message, operator);     // Throws an exception that displays the values for actual and expected separated by the provided operator.
assert(value, message); assert.ok(value, [message]);  // Tests if value is truthy, it is equivalent to assert.equal(true, !!value, message);
assert.equal(actual, expected, [message]);            // Tests shallow, coercive equality with the equal comparison operator ( == ).
assert.notEqual(actual, expected, [message]);         // Tests shallow, coercive non-equality with the not equal comparison operator ( != ).
assert.deepEqual(actual, expected, [message]);        // Tests for deep equality.
assert.notDeepEqual(actual, expected, [message]);     // Tests for any deep inequality.
assert.strictEqual(actual, expected, [message]);      // Tests strict equality, as determined by the strict equality operator ( === )
assert.notStrictEqual(actual, expected, [message]);   // Tests strict non-equality, as determined by the strict not equal operator ( !== )
assert.throws(block, [error], [message]);             // Expects block to throw an error. error can be constructor, RegExp or validation function.
assert.doesNotThrow(block, [message]);                // Expects block not to throw an error, see assert.throws for details.
assert.ifError(value);                                // Tests if value is not a false value, throws if it is a true value. Useful when testing the first argument, error in callbacks.
* OS
* http://nodejs.org/api/os.html
// Provides a few basic operating-system related utility functions.
// Use require('os') to access this module.
os.tmpdir();             // Returns the operating system's default directory for temp files.
os.endianness();         // Returns the endianness of the CPU. Possible values are "BE" or "LE".
os.hostname();           // Returns the hostname of the operating system.
os.type();               // Returns the operating system name.
os.platform();           // Returns the operating system platform.
os.arch();               // Returns the operating system CPU architecture.
os.release();            // Returns the operating system release.
os.uptime();             // Returns the system uptime in seconds.
os.loadavg();            // Returns an array containing the 1, 5, and 15 minute load averages.
os.totalmem();           // Returns the total amount of system memory in bytes.
os.freemem();            // Returns the amount of free system memory in bytes.
os.cpus();               // Returns an array of objects containing information about each CPU/core installed: model, speed (in MHz), and times (an object containing the number of milliseconds the CPU/core spent in: user, nice, sys, idle, and irq).
os.networkInterfaces();  // Get a list of network interfaces.
os.EOL;                  // A constant defining the appropriate End-of-line marker for the operating system.
* BUFFER
* http://nodejs.org/api/buffer.html
// Buffer is used to dealing with binary data
// Buffer is similar to an array of integers but corresponds to a raw memory allocation outside the V8 heap
Buffer.from(size);                                                  // Allocates a new buffer of size octets.
Buffer.from(array);                                                 // Allocates a new buffer using an array of octets.
Buffer.from(str, [encoding]);                                       // Allocates a new buffer containing the given str. encoding defaults to 'utf8'.
Buffer.isEncoding(encoding);                                        // Returns true if the encoding is a valid encoding argument, or false otherwise.
Buffer.isBuffer(obj);                                               // Tests if obj is a Buffer
Buffer.concat(list, [totalLength]);                                 // Returns a buffer which is the result of concatenating all the buffers in the list together.
Buffer.byteLength(string, [encoding]);                              // Gives the actual byte length of a string.
buf.write(string, [offset], [length], [encoding]);                  // Writes string to the buffer at offset using the given encoding
buf.toString([encoding], [start], [end]);                           // Decodes and returns a string from buffer data encoded with encoding (defaults to 'utf8') beginning at start (defaults to 0) and ending at end (defaults to buffer.length).
buf.toJSON();                                                       // Returns a JSON-representation of the Buffer instance, which is identical to the output for JSON Arrays
buf.copy(targetBuffer, [targetStart], [sourceStart], [sourceEnd]);  // Does copy between buffers. The source and target regions can be overlapped
buf.slice([start], [end]);                                          // Returns a new buffer which references the same memory as the old, but offset and cropped by the start (defaults to 0) and end (defaults to buffer.length) indexes. Negative indexes start from the end of the buffer.   
buf.fill(value, [offset], [end]);                                   // Fills the buffer with the specified value
buf[index];                                                         // Get and set the octet at index
buf.length;                                                         // The size of the buffer in bytes, Note that this is not necessarily the size of the contents
buffer.INSPECT_MAX_BYTES;                                           // How many bytes will be returned when buffer.inspect() is called. This can be overridden by user modules.
```





---

### Trello Board Json to HTML Converter

```html

<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <title>True Trello Printer</title>
    <link href="http://netdna.bootstrapcdn.com/bootstrap/3.0.3/css/bootstrap.min.css" rel="stylesheet">
    <style>
        body {
            margin: 15%;
        }

        .panel-body {
            font-size: 1.2em;

        }
    </style>
    <STYLE type="text/css" media="print">
        body {
            margin: 0;
        }
    </STYLE>
</head>

<body>

    <div id="out">
        No Trello JSON data found
    </div>

    </ul>
    </div>

    <script type="text/html" id="template-output">
        {{#lists}}
        <h1> {{name}}</h1>
        {{#cards}}
        <div class="panel panel-default">
            <div class="panel-heading">
                <h4>{{name}}</h4>{{{desc}}}
            </div>
            <!--div class="panel-body" >
                
              </div-->
            <ul class="list-group">

                {{#actions}}
                <li class="list-group-item"><tt style="color:gray;">{{date}} </tt> {{{text}}}</li>
                {{/actions}}
            </ul>
        </div>
        {{/cards}}
        <hr><br><br>
        {{/lists}}
    </script>




    <script src="http://netdna.bootstrapcdn.com/bootstrap/3.0.3/js/bootstrap.min.js"></script>
    <script src="http://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js" type="text/javascript"></script>
    <script src="http://cdnjs.cloudflare.com/ajax/libs/mustache.js/0.7.2/mustache.min.js" type="text/javascript">
    </script>
    <script src="http://cdnjs.cloudflare.com/ajax/libs/moment.js/2.5.1/moment.min.js" type="text/javascript"></script>
    <script src="http://cdnjs.cloudflare.com/ajax/libs/marked/0.3.0/marked.min.js
" type="text/javascript"></script>
    <script type="text/javascript">
        function eatData( trelloJson ) {
            var data = {
                board: trelloJson.name,
                lists: [],
                ref: {}
            }

            for ( i in trelloJson.lists ) {
                var list = trelloJson.lists[ i ]
                if ( list.closed ) {
                    //continue
                }
                data.ref[ list.id ] = {
                    name: list.name,
                    cards: []
                }
                data.lists.push( data.ref[ list.id ] )
            }


            for ( i in trelloJson.cards ) {
                var card = trelloJson.cards[ i ]
                if ( card.closed ) {
                    //continue
                }

                data.ref[ card.id ] = {
                    name: card.name,
                    desc: marked( card.desc ),
                    actions: []
                }

                data.ref[ card.idList ].cards.push( data.ref[ card.id ] )

            }

            for ( i in trelloJson.actions ) {
                var action = trelloJson.actions[ i ]
                if ( action.type != "commentCard" ) {
                    continue
                }


                data.ref[ action.id ] = {
                    text: marked( action.data.text ),
                    date: moment( action.date ).format( 'YYYY-MM-DD' )
                }
                try {
                    data.ref[ action.data.card.id ].actions.push( data.ref[ action.id ] )
                } catch ( e ) {}
            }

            return data;
        }

        function showData( data ) {
            var template = $( '#template-output' ).html()
            console.log( JSON.stringify( data, null, 2 ) )
            $( '#out' ).html( Mustache.render( template, data ) )
        }

        function autorun() {
            if ( null == data ) {
                return alert( 'Please insert JSON data from Trello in the code' )
            }
            showData( eatData( data ) );
        }
        if ( document.addEventListener ) document.addEventListener( "DOMContentLoaded", autorun, false );
        else if ( document.attachEvent ) document.attachEvent( "onreadystatechange", autorun );
        else window.onload = autorun;


        data = null;
        
           data = {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "desc": "",
           "descData": null,
           "closed": false,
           "idOrganization": "6026193a66a9890a34067149",
           "shortLink": "xanN1duF",
           "powerUps": [],
           "dateLastActivity": "2021-02-12T06:09:46.506Z",
           "idTags": [],
           "datePluginDisable": null,
           "creationMethod": "automatic",
           "idBoardSource": null,
           "idMemberCreator": "6026192732328a14a53e94d8",
           "idEnterprise": null,
           "pinned": false,
           "starred": false,
           "url": "https://trello.com/b/xanN1duF/web-dev-hub-website",
           "shortUrl": "https://trello.com/b/xanN1duF",
           "ixUpdate": "30",
           "limits": {
           "attachments": {
           "perBoard": {
           "status": "ok",
           "disableAt": 36000,
           "warnAt": 32400
           },
           "perCard": {
           "status": "ok",
           "disableAt": 1000,
           "warnAt": 900
           }
           },
           "boards": {
           "totalMembersPerBoard": {
           "status": "ok",
           "disableAt": 1600,
           "warnAt": 1440
           }
           },
           "cards": {
           "openPerBoard": {
           "status": "ok",
           "disableAt": 5000,
           "warnAt": 4500
           },
           "openPerList": {
           "status": "ok",
           "disableAt": 5000,
           "warnAt": 4500
           },
           "totalPerBoard": {
           "status": "ok",
           "disableAt": 2000000,
           "warnAt": 1800000
           },
           "totalPerList": {
           "status": "ok",
           "disableAt": 1000000,
           "warnAt": 900000
           }
           },
           "checklists": {
           "perBoard": {
           "status": "ok",
           "disableAt": 2000000,
           "warnAt": 1800000
           },
           "perCard": {
           "status": "ok",
           "disableAt": 500,
           "warnAt": 450
           }
           },
           "checkItems": {
           "perChecklist": {
           "status": "ok",
           "disableAt": 200,
           "warnAt": 180
           }
           },
           "customFields": {
           "perBoard": {
           "status": "ok",
           "disableAt": 50,
           "warnAt": 45
           }
           },
           "customFieldOptions": {
           "perField": {
           "status": "ok",
           "disableAt": 50,
           "warnAt": 45
           }
           },
           "labels": {
           "perBoard": {
           "status": "ok",
           "disableAt": 1000,
           "warnAt": 900
           }
           },
           "lists": {
           "openPerBoard": {
           "status": "ok",
           "disableAt": 500,
           "warnAt": 450
           },
           "totalPerBoard": {
           "status": "ok",
           "disableAt": 3000,
           "warnAt": 2700
           }
           },
           "stickers": {
           "perCard": {
           "status": "ok",
           "disableAt": 70,
           "warnAt": 63
           }
           },
           "reactions": {
           "perAction": {
           "status": "ok",
           "disableAt": 1000,
           "warnAt": 900
           },
           "uniquePerAction": {
           "status": "ok",
           "disableAt": 17,
           "warnAt": 16
           }
           }
           },
           "enterpriseOwned": false,
           "subscribed": false,
           "templateGallery": null,
           "premiumFeatures": [],
           "dateLastView": "2021-02-12T06:10:06.275Z",
           "labelNames": {
           "green": "",
           "yellow": "",
           "orange": "",
           "red": "",
           "purple": "",
           "blue": "",
           "sky": "",
           "lime": "",
           "pink": "",
           "black": ""
           },
           "prefs": {
           "permissionLevel": "org",
           "hideVotes": false,
           "voting": "disabled",
           "comments": "members",
           "invitations": "members",
           "selfJoin": true,
           "cardCovers": true,
           "isTemplate": false,
           "cardAging": "regular",
           "calendarFeedEnabled": false,
           "background": "602606032e380738004a96bb",
           "backgroundImage":
           "https://trello-backgrounds.s3.amazonaws.com/SharedBackground/original/34e8349439184644f6bf4940a8ea606a/photo-1611955917566-70d110dc19f3",
           "backgroundImageScaled": [ {
           "width": 140,
           "height": 93,
           "url":
           "https://trello-backgrounds.s3.amazonaws.com/SharedBackground/140x93/15f103d54c224d53d69a4470cfcbe9ef/photo-1611955917566-70d110dc19f3.jpg"
           }, {
           "width": 256,
           "height": 171,
           "url":
           "https://trello-backgrounds.s3.amazonaws.com/SharedBackground/256x171/15f103d54c224d53d69a4470cfcbe9ef/photo-1611955917566-70d110dc19f3.jpg"
           }, {
           "width": 480,
           "height": 320,
           "url":
           "https://trello-backgrounds.s3.amazonaws.com/SharedBackground/480x320/15f103d54c224d53d69a4470cfcbe9ef/photo-1611955917566-70d110dc19f3.jpg"
           }, {
           "width": 960,
           "height": 640,
           "url":
           "https://trello-backgrounds.s3.amazonaws.com/SharedBackground/960x640/15f103d54c224d53d69a4470cfcbe9ef/photo-1611955917566-70d110dc19f3.jpg"
           }, {
           "width": 1024,
           "height": 683,
           "url":
           "https://trello-backgrounds.s3.amazonaws.com/SharedBackground/1024x683/15f103d54c224d53d69a4470cfcbe9ef/photo-1611955917566-70d110dc19f3.jpg"
           }, {
           "width": 2048,
           "height": 1366,
           "url":
           "https://trello-backgrounds.s3.amazonaws.com/SharedBackground/2048x1366/15f103d54c224d53d69a4470cfcbe9ef/photo-1611955917566-70d110dc19f3.jpg"
           }, {
           "width": 1280,
           "height": 854,
           "url":
           "https://trello-backgrounds.s3.amazonaws.com/SharedBackground/1280x854/15f103d54c224d53d69a4470cfcbe9ef/photo-1611955917566-70d110dc19f3.jpg"
           }, {
           "width": 1920,
           "height": 1280,
           "url":
           "https://trello-backgrounds.s3.amazonaws.com/SharedBackground/1920x1280/15f103d54c224d53d69a4470cfcbe9ef/photo-1611955917566-70d110dc19f3.jpg"
           }, {
           "width": 2400,
           "height": 1600,
           "url":
           "https://trello-backgrounds.s3.amazonaws.com/SharedBackground/2400x1600/15f103d54c224d53d69a4470cfcbe9ef/photo-1611955917566-70d110dc19f3.jpg"
           }, {
           "width": 2560,
           "height": 1707,
           "url":
           "https://trello-backgrounds.s3.amazonaws.com/SharedBackground/original/34e8349439184644f6bf4940a8ea606a/photo-1611955917566-70d110dc19f3"
           } ],
           "backgroundTile": false,
           "backgroundBrightness": "dark",
           "backgroundBottomColor": "#222222",
           "backgroundTopColor": "#363636",
           "canBePublic": true,
           "canBeEnterprise": true,
           "canBeOrg": true,
           "canBePrivate": true,
           "canInvite": true
           },
           "actions": [ {
           "id": "60261baac6f0794629a131ad",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "card": {
           "id": "60261baac6f0794629a131ac",
           "name": "Start implementing reusable react components",
           "idShort": 9,
           "shortLink": "ZeQlTEfp"
           },
           "list": {
           "id": "602619ce28343d8b99cab23c",
           "name": "To Do"
           },
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "createCard",
           "date": "2021-02-12T06:09:46.528Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "60261b97d363b10c50ce6f56",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "card": {
           "id": "60261b97d363b10c50ce6f55",
           "name": "Consolidate site building resources and remove unused code",
           "idShort": 8,
           "shortLink": "3omT4w2E"
           },
           "list": {
           "id": "602619ce28343d8b99cab23c",
           "name": "To Do"
           },
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "createCard",
           "date": "2021-02-12T06:09:27.273Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "60261b4c8afd7b371b96a47b",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "old": {
           "prefs": {
           "background": "602606b4f59f6b4c89a95cec"
           }
           },
           "board": {
           "prefs": {
           "background": "602606032e380738004a96bb"
           },
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "updateBoard",
           "date": "2021-02-12T06:08:12.451Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "60261b49f52d0188fbebeabc",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "old": {
           "prefs": {
           "background": "6026052da3595c7055b1a844"
           }
           },
           "board": {
           "prefs": {
           "background": "602606b4f59f6b4c89a95cec"
           },
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "updateBoard",
           "date": "2021-02-12T06:08:09.743Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "60261a91ae38502031702550",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "card": {
           "id": "60261a91ae3850203170254f",
           "name": "Unify Theme across pages",
           "idShort": 7,
           "shortLink": "ihBtbXPo"
           },
           "list": {
           "id": "602619ce28343d8b99cab23c",
           "name": "To Do"
           },
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "createCard",
           "date": "2021-02-12T06:05:05.715Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "60261a87bb51c819d6e95320",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "card": {
           "id": "60261a87bb51c819d6e9531f",
           "name": "Use the watch page from the work you did on mihir's website to add to your portfolio section",
           "idShort": 6,
           "shortLink": "LYRzJGCi"
           },
           "list": {
           "id": "602619ce28343d8b99cab23c",
           "name": "To Do"
           },
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "createCard",
           "date": "2021-02-12T06:04:55.980Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "60261a5f65476e111782617c",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "card": {
           "id": "60261a5f65476e111782617b",
           "name": "Organize Blog",
           "idShort": 5,
           "shortLink": "AteKMLQf"
           },
           "list": {
           "id": "602619ce28343d8b99cab23c",
           "name": "To Do"
           },
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "createCard",
           "date": "2021-02-12T06:04:15.467Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "60261a5a3266381e8182cec0",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "card": {
           "id": "60261a5a3266381e8182cebf",
           "name": "Add Fiddle Code Spaces wherever there are examples",
           "idShort": 4,
           "shortLink": "y5y8RtbH"
           },
           "list": {
           "id": "602619ce28343d8b99cab23c",
           "name": "To Do"
           },
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "createCard",
           "date": "2021-02-12T06:04:10.863Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "60261a45183c8c14ce192f22",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "card": {
           "id": "60261a45183c8c14ce192f21",
           "name": "Reorganize file structure to reduce redundancy",
           "idShort": 3,
           "shortLink": "kvSMfztl"
           },
           "list": {
           "id": "602619ce28343d8b99cab23c",
           "name": "To Do"
           },
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "createCard",
           "date": "2021-02-12T06:03:49.378Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "60261a2e215d2086ff273533",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "card": {
           "id": "60261a2e215d2086ff273532",
           "name": "Created Navigation Interface",
           "idShort": 2,
           "shortLink": "jciAoplj"
           },
           "list": {
           "id": "602619ce28343d8b99cab23d",
           "name": "Complete"
           },
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "createCard",
           "date": "2021-02-12T06:03:26.715Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "60261a24faad3a0435e90155",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "card": {
           "id": "60261a24faad3a0435e90154",
           "name": "Fixed sandbox text editor",
           "idShort": 1,
           "shortLink": "mjDuZvcp"
           },
           "list": {
           "id": "602619ce28343d8b99cab23d",
           "name": "Complete"
           },
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "createCard",
           "date": "2021-02-12T06:03:16.750Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "60261a013f423554c3584039",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "old": {
           "name": "Done"
           },
           "list": {
           "name": "Feature List",
           "id": "602619ce28343d8b99cab23e"
           },
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "updateList",
           "date": "2021-02-12T06:02:41.095Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "602619f89221c88712645c96",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "old": {
           "name": "Doing"
           },
           "list": {
           "name": "Complete",
           "id": "602619ce28343d8b99cab23d"
           },
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "updateList",
           "date": "2021-02-12T06:02:32.607Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "602619ce28343d8b99cab242",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           },
           "organization": {
           "id": "6026193a66a9890a34067149",
           "name": "web-dev-hub"
           }
           },
           "type": "addToOrganizationBoard",
           "date": "2021-02-12T06:01:50.125Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           }, {
           "id": "602619ce28343d8b99cab240",
           "idMemberCreator": "6026192732328a14a53e94d8",
           "data": {
           "creationMethod": "automatic",
           "board": {
           "id": "602619ce28343d8b99cab23b",
           "name": "web-dev-hub-website",
           "shortLink": "xanN1duF"
           }
           },
           "type": "createBoard",
           "date": "2021-02-12T06:01:50.121Z",
           "appCreator": null,
           "limits": {},
           "memberCreator": {
           "id": "6026192732328a14a53e94d8",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idMemberReferrer": null,
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true
           }
           } ],
           "cards": [ {
           "id": "60261a45183c8c14ce192f21",
           "address": null,
           "checkItemStates": null,
           "closed": false,
           "coordinates": null,
           "creationMethod": null,
           "dateLastActivity": "2021-02-12T06:03:49.356Z",
           "desc": "",
           "descData": null,
           "dueReminder": null,
           "idBoard": "602619ce28343d8b99cab23b",
           "idLabels": [],
           "idList": "602619ce28343d8b99cab23c",
           "idMembersVoted": [],
           "idShort": 3,
           "idAttachmentCover": null,
           "locationName": null,
           "manualCoverAttachment": false,
           "name": "Reorganize file structure to reduce redundancy",
           "pos": 65535,
           "shortLink": "kvSMfztl",
           "isTemplate": false,
           "cardRole": null,
           "badges": {
           "attachmentsByType": {
           "trello": {
           "board": 0,
           "card": 0
           }
           },
           "location": false,
           "votes": 0,
           "viewingMemberVoted": false,
           "subscribed": false,
           "fogbugz": "",
           "checkItems": 0,
           "checkItemsChecked": 0,
           "checkItemsEarliestDue": null,
           "comments": 0,
           "attachments": 0,
           "description": false,
           "due": null,
           "dueComplete": false,
           "start": null
           },
           "dueComplete": false,
           "due": null,
           "email": "bryancguner+2vuwbabqgeh2088w7a0+2vuwc58r276l56b9mw1+2jnb5wft3n@boards.trello.com",
           "idChecklists": [],
           "idMembers": [],
           "labels": [],
           "limits": {
           "attachments": {
           "perCard": {
           "status": "ok",
           "disableAt": 1000,
           "warnAt": 900
           }
           },
           "checklists": {
           "perCard": {
           "status": "ok",
           "disableAt": 500,
           "warnAt": 450
           }
           },
           "stickers": {
           "perCard": {
           "status": "ok",
           "disableAt": 70,
           "warnAt": 63
           }
           }
           },
           "shortUrl": "https://trello.com/c/kvSMfztl",
           "start": null,
           "subscribed": false,
           "url": "https://trello.com/c/kvSMfztl/3-reorganize-file-structure-to-reduce-redundancy",
           "cover": {
           "idAttachment": null,
           "color": null,
           "idUploadedBackground": null,
           "size": "normal",
           "brightness": "light",
           "idPlugin": null
           },
           "attachments": [],
           "pluginData": [],
           "customFieldItems": []
           }, {
           "id": "60261a5a3266381e8182cebf",
           "address": null,
           "checkItemStates": null,
           "closed": false,
           "coordinates": null,
           "creationMethod": null,
           "dateLastActivity": "2021-02-12T06:04:10.836Z",
           "desc": "",
           "descData": null,
           "dueReminder": null,
           "idBoard": "602619ce28343d8b99cab23b",
           "idLabels": [],
           "idList": "602619ce28343d8b99cab23c",
           "idMembersVoted": [],
           "idShort": 4,
           "idAttachmentCover": null,
           "locationName": null,
           "manualCoverAttachment": false,
           "name": "Add Fiddle Code Spaces wherever there are examples",
           "pos": 131071,
           "shortLink": "y5y8RtbH",
           "isTemplate": false,
           "cardRole": null,
           "badges": {
           "attachmentsByType": {
           "trello": {
           "board": 0,
           "card": 0
           }
           },
           "location": false,
           "votes": 0,
           "viewingMemberVoted": false,
           "subscribed": false,
           "fogbugz": "",
           "checkItems": 0,
           "checkItemsChecked": 0,
           "checkItemsEarliestDue": null,
           "comments": 0,
           "attachments": 0,
           "description": false,
           "due": null,
           "dueComplete": false,
           "start": null
           },
           "dueComplete": false,
           "due": null,
           "email": "bryancguner+2vuwbabqgeh2088w7a0+2vuwc7iwj0hfho7zf7j+0kk67x8d8y@boards.trello.com",
           "idChecklists": [],
           "idMembers": [],
           "labels": [],
           "limits": {
           "attachments": {
           "perCard": {
           "status": "ok",
           "disableAt": 1000,
           "warnAt": 900
           }
           },
           "checklists": {
           "perCard": {
           "status": "ok",
           "disableAt": 500,
           "warnAt": 450
           }
           },
           "stickers": {
           "perCard": {
           "status": "ok",
           "disableAt": 70,
           "warnAt": 63
           }
           }
           },
           "shortUrl": "https://trello.com/c/y5y8RtbH",
           "start": null,
           "subscribed": false,
           "url": "https://trello.com/c/y5y8RtbH/4-add-fiddle-code-spaces-wherever-there-are-examples",
           "cover": {
           "idAttachment": null,
           "color": null,
           "idUploadedBackground": null,
           "size": "normal",
           "brightness": "light",
           "idPlugin": null
           },
           "attachments": [],
           "pluginData": [],
           "customFieldItems": []
           }, {
           "id": "60261a5f65476e111782617b",
           "address": null,
           "checkItemStates": null,
           "closed": false,
           "coordinates": null,
           "creationMethod": null,
           "dateLastActivity": "2021-02-12T06:04:15.446Z",
           "desc": "",
           "descData": null,
           "dueReminder": null,
           "idBoard": "602619ce28343d8b99cab23b",
           "idLabels": [],
           "idList": "602619ce28343d8b99cab23c",
           "idMembersVoted": [],
           "idShort": 5,
           "idAttachmentCover": null,
           "locationName": null,
           "manualCoverAttachment": false,
           "name": "Organize Blog",
           "pos": 196607,
           "shortLink": "AteKMLQf",
           "isTemplate": false,
           "cardRole": null,
           "badges": {
           "attachmentsByType": {
           "trello": {
           "board": 0,
           "card": 0
           }
           },
           "location": false,
           "votes": 0,
           "viewingMemberVoted": false,
           "subscribed": false,
           "fogbugz": "",
           "checkItems": 0,
           "checkItemsChecked": 0,
           "checkItemsEarliestDue": null,
           "comments": 0,
           "attachments": 0,
           "description": false,
           "due": null,
           "dueComplete": false,
           "start": null
           },
           "dueComplete": false,
           "due": null,
           "email": "bryancguner+2vuwbabqgeh2088w7a0+2vuwc8354q752tm7urf+0qqpqysmvt@boards.trello.com",
           "idChecklists": [],
           "idMembers": [],
           "labels": [],
           "limits": {
           "attachments": {
           "perCard": {
           "status": "ok",
           "disableAt": 1000,
           "warnAt": 900
           }
           },
           "checklists": {
           "perCard": {
           "status": "ok",
           "disableAt": 500,
           "warnAt": 450
           }
           },
           "stickers": {
           "perCard": {
           "status": "ok",
           "disableAt": 70,
           "warnAt": 63
           }
           }
           },
           "shortUrl": "https://trello.com/c/AteKMLQf",
           "start": null,
           "subscribed": false,
           "url": "https://trello.com/c/AteKMLQf/5-organize-blog",
           "cover": {
           "idAttachment": null,
           "color": null,
           "idUploadedBackground": null,
           "size": "normal",
           "brightness": "light",
           "idPlugin": null
           },
           "attachments": [],
           "pluginData": [],
           "customFieldItems": []
           }, {
           "id": "60261a87bb51c819d6e9531f",
           "address": null,
           "checkItemStates": null,
           "closed": false,
           "coordinates": null,
           "creationMethod": null,
           "dateLastActivity": "2021-02-12T06:04:55.959Z",
           "desc": "",
           "descData": null,
           "dueReminder": null,
           "idBoard": "602619ce28343d8b99cab23b",
           "idLabels": [],
           "idList": "602619ce28343d8b99cab23c",
           "idMembersVoted": [],
           "idShort": 6,
           "idAttachmentCover": null,
           "locationName": null,
           "manualCoverAttachment": false,
           "name": "Use the watch page from the work you did on mihir's website to add to your portfolio section",
           "pos": 262143,
           "shortLink": "LYRzJGCi",
           "isTemplate": false,
           "cardRole": null,
           "badges": {
           "attachmentsByType": {
           "trello": {
           "board": 0,
           "card": 0
           }
           },
           "location": false,
           "votes": 0,
           "viewingMemberVoted": false,
           "subscribed": false,
           "fogbugz": "",
           "checkItems": 0,
           "checkItemsChecked": 0,
           "checkItemsEarliestDue": null,
           "comments": 0,
           "attachments": 0,
           "description": false,
           "due": null,
           "dueComplete": false,
           "start": null
           },
           "dueComplete": false,
           "due": null,
           "email": "bryancguner+2vuwbabqgeh2088w7a0+2vuwccg681pos2ess2n+1g6ybiufvi@boards.trello.com",
           "idChecklists": [],
           "idMembers": [],
           "labels": [],
           "limits": {
           "attachments": {
           "perCard": {
           "status": "ok",
           "disableAt": 1000,
           "warnAt": 900
           }
           },
           "checklists": {
           "perCard": {
           "status": "ok",
           "disableAt": 500,
           "warnAt": 450
           }
           },
           "stickers": {
           "perCard": {
           "status": "ok",
           "disableAt": 70,
           "warnAt": 63
           }
           }
           },
           "shortUrl": "https://trello.com/c/LYRzJGCi",
           "start": null,
           "subscribed": false,
           "url":
           "https://trello.com/c/LYRzJGCi/6-use-the-watch-page-from-the-work-you-did-on-mihirs-website-to-add-to-your-portfolio-section",
           "cover": {
           "idAttachment": null,
           "color": null,
           "idUploadedBackground": null,
           "size": "normal",
           "brightness": "light",
           "idPlugin": null
           },
           "attachments": [],
           "pluginData": [],
           "customFieldItems": []
           }, {
           "id": "60261a91ae3850203170254f",
           "address": null,
           "checkItemStates": null,
           "closed": false,
           "coordinates": null,
           "creationMethod": null,
           "dateLastActivity": "2021-02-12T06:05:05.694Z",
           "desc": "",
           "descData": null,
           "dueReminder": null,
           "idBoard": "602619ce28343d8b99cab23b",
           "idLabels": [],
           "idList": "602619ce28343d8b99cab23c",
           "idMembersVoted": [],
           "idShort": 7,
           "idAttachmentCover": null,
           "locationName": null,
           "manualCoverAttachment": false,
           "name": "Unify Theme across pages",
           "pos": 327679,
           "shortLink": "ihBtbXPo",
           "isTemplate": false,
           "cardRole": null,
           "badges": {
           "attachmentsByType": {
           "trello": {
           "board": 0,
           "card": 0
           }
           },
           "location": false,
           "votes": 0,
           "viewingMemberVoted": false,
           "subscribed": false,
           "fogbugz": "",
           "checkItems": 0,
           "checkItemsChecked": 0,
           "checkItemsEarliestDue": null,
           "comments": 0,
           "attachments": 0,
           "description": false,
           "due": null,
           "dueComplete": false,
           "start": null
           },
           "dueComplete": false,
           "due": null,
           "email": "bryancguner+2vuwbabqgeh2088w7a0+2vuwcdiwjrt5fjardxr+1lb64pajid@boards.trello.com",
           "idChecklists": [],
           "idMembers": [],
           "labels": [],
           "limits": {
           "attachments": {
           "perCard": {
           "status": "ok",
           "disableAt": 1000,
           "warnAt": 900
           }
           },
           "checklists": {
           "perCard": {
           "status": "ok",
           "disableAt": 500,
           "warnAt": 450
           }
           },
           "stickers": {
           "perCard": {
           "status": "ok",
           "disableAt": 70,
           "warnAt": 63
           }
           }
           },
           "shortUrl": "https://trello.com/c/ihBtbXPo",
           "start": null,
           "subscribed": false,
           "url": "https://trello.com/c/ihBtbXPo/7-unify-theme-across-pages",
           "cover": {
           "idAttachment": null,
           "color": null,
           "idUploadedBackground": null,
           "size": "normal",
           "brightness": "light",
           "idPlugin": null
           },
           "attachments": [],
           "pluginData": [],
           "customFieldItems": []
           }, {
           "id": "60261b97d363b10c50ce6f55",
           "address": null,
           "checkItemStates": null,
           "closed": false,
           "coordinates": null,
           "creationMethod": null,
           "dateLastActivity": "2021-02-12T06:09:27.246Z",
           "desc": "",
           "descData": null,
           "dueReminder": null,
           "idBoard": "602619ce28343d8b99cab23b",
           "idLabels": [],
           "idList": "602619ce28343d8b99cab23c",
           "idMembersVoted": [],
           "idShort": 8,
           "idAttachmentCover": null,
           "locationName": null,
           "manualCoverAttachment": false,
           "name": "Consolidate site building resources and remove unused code",
           "pos": 393215,
           "shortLink": "3omT4w2E",
           "isTemplate": false,
           "cardRole": null,
           "badges": {
           "attachmentsByType": {
           "trello": {
           "board": 0,
           "card": 0
           }
           },
           "location": false,
           "votes": 0,
           "viewingMemberVoted": false,
           "subscribed": false,
           "fogbugz": "",
           "checkItems": 0,
           "checkItemsChecked": 0,
           "checkItemsEarliestDue": null,
           "comments": 0,
           "attachments": 0,
           "description": false,
           "due": null,
           "dueComplete": false,
           "start": null
           },
           "dueComplete": false,
           "due": null,
           "email": "bryancguner+2vuwbabqgeh2088w7a0+2vuwd5vg4fbi41ocklx+0agjezcvrz@boards.trello.com",
           "idChecklists": [],
           "idMembers": [],
           "labels": [],
           "limits": {
           "attachments": {
           "perCard": {
           "status": "ok",
           "disableAt": 1000,
           "warnAt": 900
           }
           },
           "checklists": {
           "perCard": {
           "status": "ok",
           "disableAt": 500,
           "warnAt": 450
           }
           },
           "stickers": {
           "perCard": {
           "status": "ok",
           "disableAt": 70,
           "warnAt": 63
           }
           }
           },
           "shortUrl": "https://trello.com/c/3omT4w2E",
           "start": null,
           "subscribed": false,
           "url": "https://trello.com/c/3omT4w2E/8-consolidate-site-building-resources-and-remove-unused-code",
           "cover": {
           "idAttachment": null,
           "color": null,
           "idUploadedBackground": null,
           "size": "normal",
           "brightness": "light",
           "idPlugin": null
           },
           "attachments": [],
           "pluginData": [],
           "customFieldItems": []
           }, {
           "id": "60261baac6f0794629a131ac",
           "address": null,
           "checkItemStates": null,
           "closed": false,
           "coordinates": null,
           "creationMethod": null,
           "dateLastActivity": "2021-02-12T06:09:46.506Z",
           "desc": "",
           "descData": null,
           "dueReminder": null,
           "idBoard": "602619ce28343d8b99cab23b",
           "idLabels": [],
           "idList": "602619ce28343d8b99cab23c",
           "idMembersVoted": [],
           "idShort": 9,
           "idAttachmentCover": null,
           "locationName": null,
           "manualCoverAttachment": false,
           "name": "Start implementing reusable react components",
           "pos": 458751,
           "shortLink": "ZeQlTEfp",
           "isTemplate": false,
           "cardRole": null,
           "badges": {
           "attachmentsByType": {
           "trello": {
           "board": 0,
           "card": 0
           }
           },
           "location": false,
           "votes": 0,
           "viewingMemberVoted": false,
           "subscribed": false,
           "fogbugz": "",
           "checkItems": 0,
           "checkItemsChecked": 0,
           "checkItemsEarliestDue": null,
           "comments": 0,
           "attachments": 0,
           "description": false,
           "due": null,
           "dueComplete": false,
           "start": null
           },
           "dueComplete": false,
           "due": null,
           "email": "bryancguner+2vuwbabqgeh2088w7a0+2vuwd7x85gfttl7incc+2epb2srcci@boards.trello.com",
           "idChecklists": [],
           "idMembers": [],
           "labels": [],
           "limits": {
           "attachments": {
           "perCard": {
           "status": "ok",
           "disableAt": 1000,
           "warnAt": 900
           }
           },
           "checklists": {
           "perCard": {
           "status": "ok",
           "disableAt": 500,
           "warnAt": 450
           }
           },
           "stickers": {
           "perCard": {
           "status": "ok",
           "disableAt": 70,
           "warnAt": 63
           }
           }
           },
           "shortUrl": "https://trello.com/c/ZeQlTEfp",
           "start": null,
           "subscribed": false,
           "url": "https://trello.com/c/ZeQlTEfp/9-start-implementing-reusable-react-components",
           "cover": {
           "idAttachment": null,
           "color": null,
           "idUploadedBackground": null,
           "size": "normal",
           "brightness": "light",
           "idPlugin": null
           },
           "attachments": [],
           "pluginData": [],
           "customFieldItems": []
           }, {
           "id": "60261a24faad3a0435e90154",
           "address": null,
           "checkItemStates": null,
           "closed": false,
           "coordinates": null,
           "creationMethod": null,
           "dateLastActivity": "2021-02-12T06:03:16.725Z",
           "desc": "",
           "descData": null,
           "dueReminder": null,
           "idBoard": "602619ce28343d8b99cab23b",
           "idLabels": [],
           "idList": "602619ce28343d8b99cab23d",
           "idMembersVoted": [],
           "idShort": 1,
           "idAttachmentCover": null,
           "locationName": null,
           "manualCoverAttachment": false,
           "name": "Fixed sandbox text editor",
           "pos": 65535,
           "shortLink": "mjDuZvcp",
           "isTemplate": false,
           "cardRole": null,
           "badges": {
           "attachmentsByType": {
           "trello": {
           "board": 0,
           "card": 0
           }
           },
           "location": false,
           "votes": 0,
           "viewingMemberVoted": false,
           "subscribed": false,
           "fogbugz": "",
           "checkItems": 0,
           "checkItemsChecked": 0,
           "checkItemsEarliestDue": null,
           "comments": 0,
           "attachments": 0,
           "description": false,
           "due": null,
           "dueComplete": false,
           "start": null
           },
           "dueComplete": false,
           "due": null,
           "email": "bryancguner+2vuwbabqgeh2088w7a0+2vuwc1rq35bmkagkrpw+1s0s59ba8r@boards.trello.com",
           "idChecklists": [],
           "idMembers": [],
           "labels": [],
           "limits": {
           "attachments": {
           "perCard": {
           "status": "ok",
           "disableAt": 1000,
           "warnAt": 900
           }
           },
           "checklists": {
           "perCard": {
           "status": "ok",
           "disableAt": 500,
           "warnAt": 450
           }
           },
           "stickers": {
           "perCard": {
           "status": "ok",
           "disableAt": 70,
           "warnAt": 63
           }
           }
           },
           "shortUrl": "https://trello.com/c/mjDuZvcp",
           "start": null,
           "subscribed": false,
           "url": "https://trello.com/c/mjDuZvcp/1-fixed-sandbox-text-editor",
           "cover": {
           "idAttachment": null,
           "color": null,
           "idUploadedBackground": null,
           "size": "normal",
           "brightness": "light",
           "idPlugin": null
           },
           "attachments": [],
           "pluginData": [],
           "customFieldItems": []
           }, {
           "id": "60261a2e215d2086ff273532",
           "address": null,
           "checkItemStates": null,
           "closed": false,
           "coordinates": null,
           "creationMethod": null,
           "dateLastActivity": "2021-02-12T06:03:26.695Z",
           "desc": "",
           "descData": null,
           "dueReminder": null,
           "idBoard": "602619ce28343d8b99cab23b",
           "idLabels": [],
           "idList": "602619ce28343d8b99cab23d",
           "idMembersVoted": [],
           "idShort": 2,
           "idAttachmentCover": null,
           "locationName": null,
           "manualCoverAttachment": false,
           "name": "Created Navigation Interface",
           "pos": 131071,
           "shortLink": "jciAoplj",
           "isTemplate": false,
           "cardRole": null,
           "badges": {
           "attachmentsByType": {
           "trello": {
           "board": 0,
           "card": 0
           }
           },
           "location": false,
           "votes": 0,
           "viewingMemberVoted": false,
           "subscribed": false,
           "fogbugz": "",
           "checkItems": 0,
           "checkItemsChecked": 0,
           "checkItemsEarliestDue": null,
           "comments": 0,
           "attachments": 0,
           "description": false,
           "due": null,
           "dueComplete": false,
           "start": null
           },
           "dueComplete": false,
           "due": null,
           "email": "bryancguner+2vuwbabqgeh2088w7a0+2vuwc2rcm4e4a9muvjm+1oy3nx7p2q@boards.trello.com",
           "idChecklists": [],
           "idMembers": [],
           "labels": [],
           "limits": {
           "attachments": {
           "perCard": {
           "status": "ok",
           "disableAt": 1000,
           "warnAt": 900
           }
           },
           "checklists": {
           "perCard": {
           "status": "ok",
           "disableAt": 500,
           "warnAt": 450
           }
           },
           "stickers": {
           "perCard": {
           "status": "ok",
           "disableAt": 70,
           "warnAt": 63
           }
           }
           },
           "shortUrl": "https://trello.com/c/jciAoplj",
           "start": null,
           "subscribed": false,
           "url": "https://trello.com/c/jciAoplj/2-created-navigation-interface",
           "cover": {
           "idAttachment": null,
           "color": null,
           "idUploadedBackground": null,
           "size": "normal",
           "brightness": "light",
           "idPlugin": null
           },
           "attachments": [],
           "pluginData": [],
           "customFieldItems": []
           } ],
           "labels": [ {
           "id": "602619ce86c6bc9cc5bc0a49",
           "idBoard": "602619ce28343d8b99cab23b",
           "name": "",
           "color": "green"
           }, {
           "id": "602619ce86c6bc9cc5bc0a4b",
           "idBoard": "602619ce28343d8b99cab23b",
           "name": "",
           "color": "yellow"
           }, {
           "id": "602619ce86c6bc9cc5bc0a4d",
           "idBoard": "602619ce28343d8b99cab23b",
           "name": "",
           "color": "orange"
           }, {
           "id": "602619ce86c6bc9cc5bc0a4f",
           "idBoard": "602619ce28343d8b99cab23b",
           "name": "",
           "color": "purple"
           }, {
           "id": "602619ce86c6bc9cc5bc0a52",
           "idBoard": "602619ce28343d8b99cab23b",
           "name": "",
           "color": "blue"
           }, {
           "id": "602619ce86c6bc9cc5bc0a53",
           "idBoard": "602619ce28343d8b99cab23b",
           "name": "",
           "color": "red"
           } ],
           "lists": [ {
           "id": "602619ce28343d8b99cab23c",
           "name": "To Do",
           "closed": false,
           "pos": 16384,
           "softLimit": null,
           "creationMethod": "automatic",
           "idBoard": "602619ce28343d8b99cab23b",
           "limits": {
           "cards": {
           "openPerList": {
           "status": "ok",
           "disableAt": 5000,
           "warnAt": 4500
           },
           "totalPerList": {
           "status": "ok",
           "disableAt": 1000000,
           "warnAt": 900000
           }
           }
           },
           "subscribed": false
           }, {
           "id": "602619ce28343d8b99cab23d",
           "name": "Complete",
           "closed": false,
           "pos": 32768,
           "softLimit": null,
           "creationMethod": "automatic",
           "idBoard": "602619ce28343d8b99cab23b",
           "limits": {
           "cards": {
           "openPerList": {
           "status": "ok",
           "disableAt": 5000,
           "warnAt": 4500
           },
           "totalPerList": {
           "status": "ok",
           "disableAt": 1000000,
           "warnAt": 900000
           }
           }
           },
           "subscribed": false
           }, {
           "id": "602619ce28343d8b99cab23e",
           "name": "Feature List",
           "closed": false,
           "pos": 49152,
           "softLimit": null,
           "creationMethod": "automatic",
           "idBoard": "602619ce28343d8b99cab23b",
           "limits": {
           "cards": {
           "openPerList": {
           "status": "ok",
           "disableAt": 5000,
           "warnAt": 4500
           },
           "totalPerList": {
           "status": "ok",
           "disableAt": 1000000,
           "warnAt": 900000
           }
           }
           },
           "subscribed": false
           } ],
           "members": [ {
           "id": "6026192732328a14a53e94d8",
           "bio": "",
           "bioData": null,
           "confirmed": true,
           "memberType": "normal",
           "username": "bryancguner",
           "activityBlocked": false,
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "fullName": "Bryan C Guner",
           "idEnterprise": null,
           "idEnterprisesDeactivated": [],
           "idMemberReferrer": null,
           "idPremOrgsAdmin": [],
           "initials": "BG",
           "nonPublic": {
           "fullName": "Bryan Guner",
           "initials": "BG",
           "avatarUrl":
           "https://trello-members.s3.amazonaws.com/6026192732328a14a53e94d8/bbd362d2e6a84e455c89025c83f5edda",
           "avatarHash": "bbd362d2e6a84e455c89025c83f5edda"
           },
           "nonPublicAvailable": true,
           "products": [],
           "url": "https://trello.com/bryancguner",
           "status": "disconnected"
           } ],
           "checklists": [],
           "customFields": [],
           "memberships": [ {
           "id": "602619ce28343d8b99cab23f",
           "idMember": "6026192732328a14a53e94d8",
           "memberType": "admin",
           "unconfirmed": false,
           "deactivated": false
           } ],
           "pluginData": []
           }

 
    </script>
</body>

</html>

```



---




---





</details>

---
[github-resume](https://resume.github.io/?bgoonz)


**Technical Skills­­­**

| **Programming**** Languages:** | JavaScript ES-6, NodeJS, React, HTML5, CSS3, SCSS, Bash Shell, Excel, SQL, NoSQL, MATLAB, Python, C++ |
| --- | --- |
| **Databases:** | PostgreSQL, MongoDB |
| **Cloud:** | Docker, AWS, Google App Engine, Netlify, Digital Ocean, Heroku, Azure Cloud Services |
| **OS:** | Linux, Windows (WSL), IOS |
| **Agile:** | GitHub, BitBucket, Jira, Confluence |
| **IDEs:** | VSCode, Visual Studio, Atom, Code Blocks, Sublime Text 3, Brackets |

# Experience

| **Relational Concepts:** Hallandale Beach, FL | March 2020 - Present |
| --- | --- |
| **Front End Web Developer** |
 |

- Responsible for front-end development for a custom real estate application which provides sophisticated and fully customizable filtering to allow investors and real estate professionals to narrow in on exact search targets.
- Designed mock-up screens, wireframes, and workflows for intuitive user experience.
- Migrated existing multi-page user experience into singular page interfaces using React components.
- Participated in every stage of the design from conception through development and iterative improvement.
- Produced user stories and internal documentation for future site development and maintenance.
- Implemented modern frameworks including Bootstrap and Font-Awesome to give the site an aesthetic overhaul.
- Managed all test deployments using a combination of Digital Ocean and Netlify.
- Produced unit tests using a combination of Mocha and Chai.
- Injected Google Analytics to capture pertinent usage data to produce an insightful dashboard experience.

| **Environment:** | **JavaScript, JQuery, React, HTML5 &amp; CSS, Bootstrap, DOJO, Google Cloud, Bash Script** |
| --- | --- |

| **Cembre:** Edison, NJ | Nov 2019 – Mar 2020 |
| --- | --- |
| **Product Development Engineer** |
 |

- Converted client&#39;s product needs into technical specs to be sent to the development team in Italy.
- Reorganized internal file server structure.
- Conducted remote / in person system integration and product demonstrations.
- Presided over internal and end user software trainings in addition to producing the corresponding documentation.
- Served as the primary point of contact for troubleshooting railroad hardware and software in the North America.

| **Environment:** | **Excel, AutoCAD, PowerPoint, Word** |
| --- | --- |

# Education

| **B.S. Electrical Engineering, TCNJ,** Ewing NJ | 2014 – 2019 |
| --- | --- |

**Capstone Project – Team Lead**

- Successfully completed and delivered a platform to digitize a guitar signal and perform filtering before executing frequency &amp; time domain analysis to track a current performance against prerecorded performance.
- Implemented the Dynamic Time Warping algorithm in C++ and Python to autonomously activate or adjust guitar effect at multiple pre-designated section of performance.

| **Environment:** | **C++, Python, MATLAB, PureData** |
| --- | --- |

**References and portfolio available upon request**





---


<div style=" border: 1px solid black">
<img src="https://cloud.netlifyusercontent.com/assets/344dbf88-fdf9-42bb-adb4-46f01eedd629/23b9b236-746e-409c-8e86-30b4385e3b72/hr1-raypham.gif" alt="hr-line" width="100%" height="22">
</div>

<hr>

<details>
  
<summary>My Projects</summary>




Web Dev Resource Hub
----------------------

### My personal Web Development blog and resource sharing site

*   [Live Site](https://goofy-euclid-1cd736.netlify.app/)


*   [Main Page](https://goofy-euclid-1cd736.netlify.app/core-site/index.html)




<div style=" border: 1px solid black">
<img src="https://cloud.netlifyusercontent.com/assets/344dbf88-fdf9-42bb-adb4-46f01eedd629/23b9b236-746e-409c-8e86-30b4385e3b72/hr1-raypham.gif" alt="hr-line" width="100%" height="22">
</div>

<hr>


---

MihirBeg.com
---------------


### Created a dynamic web page for a local musician using the Bootsrtap framework.

-Talk about App Features & Design Process Here-

-   [Live Site](https://eloquent-sammet-ba1810.netlify.app/)


<div style=" border: 1px solid black">
<img src="https://cloud.netlifyusercontent.com/assets/344dbf88-fdf9-42bb-adb4-46f01eedd629/23b9b236-746e-409c-8e86-30b4385e3b72/hr1-raypham.gif" alt="hr-line" width="100%" height="22">
</div>

<hr>


---       
Interview Prep Static Site 
-----------------------------

### Data Structures Repository

-Hope this helps someone other than me!-

*   [Live Site](https://gracious-raman-474030.netlify.app)

---



<div style=" border: 1px solid black">
<img src="https://cloud.netlifyusercontent.com/assets/344dbf88-fdf9-42bb-adb4-46f01eedd629/23b9b236-746e-409c-8e86-30b4385e3b72/hr1-raypham.gif" alt="hr-line" width="100%" height="22">
</div>

<hr>


---

Learning React Blog
--------------------
https://ecstatic-jang-593fd1.netlify.app/readme

#### React Repo:

[React Repo](https://github.com/bgoonz/React-Practice)


---

<a href="https://codesandbox.io/embed/zealous-microservice-ti7em?autoresize=1&expanddevtools=1&fontsize=14&hidenavigation=1&moduleview=1&theme=dark"   style="width:100%; height:20px; border:0; border-radius: 4px; overflow:hidden;" rel="React Todo">![Foo](https://codesandbox.io/static/img/play-codesandbox.svg)</a>

---


<div style=" border: 1px solid black">
<img src="https://cloud.netlifyusercontent.com/assets/344dbf88-fdf9-42bb-adb4-46f01eedd629/23b9b236-746e-409c-8e86-30b4385e3b72/hr1-raypham.gif" alt="hr-line" width="100%" height="22">
</div>

<hr>

<details>

---
---

## _Email_

[bryan.guner@gmail.com](#)

## _Phone_

*551-254-5505*

## Social

-   [GitHub](https://github.com/bgoonz)
-   [code pen](https://codepen.io/bgoonz)
-   [Glitch](https://glitch.com/@bgoonz)
-   [Instagram](https://www.instagram.com/bgoonz/)
-   [LinkedIn](https://www.linkedin.com/in/bryan-guner-046199128/)
-   [Replit](https://repl.it/@bgoonz/)
-   [Redit](https://www.reddit.com/user/bgoonz1)
-   [runkit](https://runkit.com/bgoonz)
-   [stack-exchange](https://meta.stackexchange.com/users/936785/bryan-guner)


---
---




