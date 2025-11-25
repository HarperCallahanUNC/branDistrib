# Data from: A high-performance brain-computer interface for finger decoding and quadcopter game control in an individual with paralysis

[https://doi.org/10.5061/dryad.1jwstqk4f](https://doi.org/10.5061/dryad.1jwstqk4f)

## Description of the data and file structure

**Finger Decoding and Quadcopter Data**

These data are reported in Willsey et al. 2024 and consist of several sessions of finger decoding experiments and one session of Quadcopter data. These data are needed by the code released as part of this manuscript to reproduce the offline analysis presenting the key findings in that manuscript. See the manuscript and the released code for more details.

### Files and variables

#### File: FingerDecodingQuadcopterData.zip

**Description:** 

The main data provided are .mat files contained in subfolders entitled "RedisMat." These files primarily contain the raw data from online finger decoding sessions, although one file contains the position of the quadcopter from a quadcopter session. The  variables are:

* Binned spike band data, *binnedNeural_hlfp*
* Binned redis and xpc timestamps, *binnedNeural_redisClock* and *binnedNeural_xpcClock*
* Redis clock data, binned_taskOutput_stream_redis_clock
* Position of the 5 virtual fingers with the first 2 columns denoting each DOF for the thumb and the following 4 columns denoting the position for the other 4 fingers, *binned_taskOutput_stream_estimated*
* Position of the finger targets, *binned_taskOutput_stream_target*
* *x*, *y*, *z* are variables in a .mat file for the quadcopter session and denote the position of the quadcopter in 3D space

In subfolders entitled "Decoders," there are .mat files and .pt files. The .pt files are the trained decoding algorithm parameters that can be loaded into the model. In the .mat files, there are three variables:

* *mask* corresponds to a 1x256 array where channels included in the decoding algorithm are denoted with "1" and channels not included are denoted with "0"
* *myMean* corresponds to a 1x4 array offset for each decoded DOF that is subtracted from the output of the decoding algorithm
* *mySDev* corresponds to a 1x4 array; 1/*mySDev* is a gain value applied to the output of the decoding algorithm after subtracting the offset above

In the OpenLoopData folder, there are .mat files of offline data from one session where the participant attempted to move his fingers in sync with the virtual fingers. These files contain the following variables:

* Binned spike band data, *binnedNeural_hlfp*, and corresponding Redis timestamps, *binnedNeural_redisClock* 
* Target position for each degree of freedom for each finger, *taskOutput_stream_target*, and corresponding Redis timestamps, taskOutput_stream_redis_clock
* Stream of data that indicates whether virtual fingers are stationary (a value of 1 or 3) or moving toward their target (a value of 2), *taskOutput_stream_hand_color*

## Code/software

The code needed to run an offline analysis on this data is available on GitHub (see Related Works section).
