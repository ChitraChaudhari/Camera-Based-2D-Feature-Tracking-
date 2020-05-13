# Camera Based 2D Feature Tracking

<img src="images/keypoints.png" width="820" height="248" />

The idea of main project is to build a collision detection system - that's the overall goal for the Final Project. As a preparation for this, this project now build the feature tracking part and test various detector / descriptor combinations to see which ones perform best. This project consists of four parts:

* First part focus on loading images, setting up data structures and putting everything into a ring buffer to optimize memory load. 
* Then, integrate several keypoint detectors such as HARRIS, FAST, BRISK and SIFT and compare them with regard to number of keypoints and speed. 
* Next part then focus on descriptor extraction and matching using brute force and also the FLANN approach.
* In the last part, once the code framework is complete, we will test the various algorithms in different combinations and compare them with regard to some performance measures. 

## Dependencies for Running Locally
* cmake >= 2.8
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* OpenCV >= 4.1
  * This must be compiled from source using the `-D OPENCV_ENABLE_NONFREE=ON` cmake flag for testing the SIFT and SURF detectors.
  * The OpenCV 4.1.0 source code can be found [here](https://github.com/opencv/opencv/tree/4.1.0)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory in the top level directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./2D_feature_tracking`.

# Results

After implementation of keypoint-detection, descriptor extraction and keypoint-matching in 10 consecutive images, the results obtained are presented in the following sections.

## Keypoint-detected

Total number of keypoints detected by each method for every image are listed in the table bellow:

|Detector   |1	|2	|3	|4	|5	|6	|7	|8	|9	|10 |
|-----------|---|---|---|---|---|---|---|---|---|---|
|SHITOMASHI	|127|120|123|120|120|115|114|125|112|113|
|HARRIS	    |17	|14	|18	|21	|26	|43	|18	|31	|26	|34 |
|FAST	    |420|431|408|430|389|417|422|413|401|405|
|BRISK	    |254|274|277|275|293|278|289|268|262|252|
|ORB        |91	|102|106|113|109|124|129|127|124|125|
|AKAZE	    |164|157|159|154|163|168|174|175|176|176|
|SIFT	    |138|131|122|135|136|141|136|149|156|136|

## Matched keypoints

Total number of matched keypoints for every single combination of detectors and descriptors are also provided in the following table
                    
|                   |1-2|2-3|3-4|4-5|5-6|6-7|7-8|8-9|9-10|
|-------------------|---|---|---|---|---|---|---|---|----|
|SHITOMASI - BRISK	|96	|95	|90	|93	|92	|85	|94	|91	|91  |
|SHITOMASI - BRIEF	|105|105|100|102|100|97	|102|100|101 |
|SHITOMASI - ORB	|103|105|99	|102|100|95	|101|102|100 |
|SHITOMASI - FREAK	|93	|97	|96	|95	|92	|88	|88	|92	|92  |
|SHITOMASI - AKAZE	|NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA  |
|SHITOMASI - SIFT	|115|109|104|103|101|101|97	|107|99  |
|HARRIS - BRISK	    |12	|10	|14	|15	|16	|16	|15	|23	|21  |
|HARRIS - BRIEF	    |14	|11	|15	|20	|24	|26	|16	|24	|23  |
|HARRIS - ORB	    |12	|12	|15	|18	|24	|20	|15	|24	|22  |
|HARRIS - FREAK	    |13	|13	|15	|15	|17	|20	|12	|21	|18  |
|HARRIS- AKAZE	    |NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA  |
|HARRIS - SIFT	    |14	|11	|16 |19	|22	|22	|13	|24	|22  |
|FAST - BRISK	    |215|216|199|211|191|207|217|206|211 |
|FAST - BRIEF	    |321|334|301|336|277|329|326|316|310 |
|FAST - ORB	        |308|311|301|323|281|316|323|306|315 |
|FAST - FREAK	    |252|250|240|258|231|268|248|256|251 |
|FAST - AKAZE	    |NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA  |
|FAST - SIFT        |315|327|303|316|295|328|320|305|303 |
|BRISK - BRISK	    |168|169|158|170|173|186|174|170|184 |
|BRISK - BRIEF	    |174|194|183|177|183|194|208|186|179 |
|BRISK - ORB	    |155|167|156|161|158|181|165|171|172 |
|BRISK - FREAK	    |154|174|154|168|160|182|169|175|167 |
|BRISK - AKAZE	    |NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA  |
|BRISK - SIFT	    |177|189|174|176|169|193|196|176|188 |
|ORB - BRISK	    |60	|65	|65	|76	|72	|82	|82	|72	|72  |
|ORB - BRIEF	    |37	|38	|38	|53	|42	|61	|60	|61	|60  |
|ORB - ORB	        |38	|57	|49	|52	|59	|69	|70	|66	|71  |
|ORB - FREAK	    |38	|33	|37	|41	|33	|40	|41	|40	|43  |
|ORB - AKAZE	    |NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA  |
|ORB - SIFT	        |66	|79	|78	|79	|82	|93	|94	|93	|92  |
|AKAZE - BRISK	    |122|113|120|119|117|119|133|139|127 |
|AKAZE - BRIEF	    |107|115|110|107|117|129|134|136|129 |
|AKAZE - ORB	    |98	|97	|96	|84	|95	|122|106|112|119 |
|AKAZE - FREAK	    |102|105|95	|98	|100|117|126|117|115 |
|AKAZE - AKAZE	    |127|128|124|119|125|131|138|139|142 |
|AKAZE - SIFT	    |134|136|129|138|139|149|149|154|150 |
|SIFT - BRISK	    |56	|62	|56	|61	|57	|55	|56	|63	|75  |
|SIFT - BRIEF	    |64	|68	|63	|65	|53	|59	|73	|69	|84  |
|SIFT - ORB	        |NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA  |
|SIFT - FREAK	    |59	|61	|52	|63	|52	|51	|51	|53	|67  |
|SIFT - AKAZE	    |NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA	|NA  |
|SIFT - SIFT	    |81	|80	|84	|95	|92	|83	|83	|101|104 |

## Time-taken

The time taken for keypoint detection and descriptor extraction for all combinations is listed below.

|                |1-2   |2-3   |3-4   |4-5   |5-6   |6-7   |7-8   |8-9   |9-10  |
|----------------|------|------|------|------|------|------|------|------|------|
|SHITOMASI-BRISK |68    |42	   |41	  |40	 |39	|38	   |57	  |39	 |37    |
|SHITOMASI-BRIEF |41.6  |40    |39.5  |38.6  |37.2  |37.06 |38.3  |38.13 |37.19 |
|SHITOMASI-ORB	 |41.2  |40    |38.5  |37.7  |36.5  |36.24 |37.16 |37.8  |37.4  |
|SHITOMASI-FREAK |125.61|117.79|113.75|107.54|106.57|105.64|105.77|105.86|103.42|
|SHITOMASI-AKAZE |NA	|NA	   |NA	  |NA    |NA	|NA    |NA	  |NA	 |NA    |
|SHITOMASI-SIFT	 |75.37	|46.32 |78.89 |61.47 |59.91	|56.8  |59.55 |58.68 |56.44 |
|HARRIS-BRISK	 |39.95	|39.01 |38.99 |39.53 |55.64	|54.58 |39.46 |40.41 |42.85 |
|HARRIS-BRIEF	 |36.75	|35.66 |38.79 |38.47 |50.59	|49.47 |38.91 |40.03 |43.35 |
|HARRIS-ORB	     |36.11	|34.97 |36.87 |37.21 |53.19	|52.12 |37.77 |39.05 |43.73 |
|HARRIS-FREAK	 |117.64|115.92|114.99|107.74|126.6	|124.62|105.97|106.6 |113.42|
|HARRIS-AKAZE	 |NA	|NA	   |NA	  |NA    |NA	|NA    |NA	  |NA	 |NA    |
|HARRIS-SIFT	 |66.27	|64.33 |75.26 |73.86 |88.54	|95	   |74.85 |69.75 |82.08 |
|FAST-BRISK      |22.07	|14.81 |14.8  |13.86 |13.31	|13.66 |13.16 |12.83 |13.22 |
|FAST-BRIEF	     |11.68	|9.49  |8.3	  |7.3	 |7.38	|7.91  |7.88  |8.39	 |8.37  |
|FAST-ORB	     |8.36	|7.89  |7.58  |7.36  |7.19	|7.32  |7.41  |7.61  |7.6   |
|FAST-FREAK	     |106.05|101.9 |94.09 |90.36 |92.72	|95.64 |93.01 |89.35 |90.57 |
|FAST-AKAZE 	 |NA	|NA	   |NA	  |NA    |NA	|NA    |NA	  |NA	 |NA    |
|FAST-SIFT	     |93.79	|87.75 |86.46 |81.84 |80.49	|81.99 |81.24 |81.06 |77.97 |
|BRISK-BRISK	 |772.23|765.95|764.59|764.01|764.67|762.05|758.15|763.17|767.5 |
|BRISK-BRIEF	 |757.39|757.75|754.58|749.57|753.3 |755.48|757.32|755.36|750.15|
|BRISK-ORB	     |762.89|763.33|752.66|749.42|754.66|757.97|754.15|753.95|755.84|
|BRISK-FREAK	 |844.73|837.21|827.79|826.09|831.52|827.11|826.74|824.18|821.65|
|BRISK-AKAZE	 |NA	|NA	   |NA	  |NA    |NA	|NA    |NA	  |NA	 |NA    |
|BRISK-SIFT	     |376.9	|369.7 |370.7 |408.5 |375.4	|373.9 |363.2 |372.3 |382.6 |
|ORB-BRISK	     |247.9	|248.6 |247.8 |249.4 |268.1	|274.2 |252.3 |249.2 |250.2 |
|ORB-BRIEF	     |10.3	|10.7  |9.7   |9.7   |9.4   |9.6   |10.5  |9.8   |10.1  |
|ORB-ORB	     |14.1	|15.2  |13.8  |14.5	 |14	|13.9  |15.4  |14.8	 |13.6  |
|ORB-FREAK	     |47.3	|44.3  |45.5  |43.1	 |43.5	|43.3  |44.3  |44.9	 |43.7  |
|ORB-AKAZE	     |NA	|NA	   |NA	  |NA    |NA	|NA    |NA	  |NA	 |NA    |
|ORB-SIFT	     |47.8	|51.6  |50.4  |48.5	 |49	|52.7  |53.7  |56.8	 |53.5  |
|AKAZE-BRISK	 |311.1	|315.7 |315.5 |341.5 |320.5	|318.2 |320.3 |318.7 |314.3 |
|AKAZE-BRIEF	 |71.9	|72.2  |74.9  |74.4	 |74.3	|75.2  |75.6  |96.2	 |85.7  |
|AKAZE-ORB	     |78.9	|75.9  |77.6  |73.4  |79.1  |91.9  |80.2  |87.9	 |84.1  |
|AKAZE-FREAK	 |107.8	|99.1  |98.8  |108.5 |108.5	|102.7 |108.9 |108.  |111.8 |
|AKAZE-AKAZE	 |126.1	|120.5 |127.3 |125.6 |120.6	|122.1 |122.9 |124.4 |122   |
|AKAZE-SIFT	     |92.1	|95.5  |94.5  |95.5	 |99.2	|98.2  |101.2 |110.3 |99.5  |
|SIFT-BRISK	     |351.5	|321.6 |319.9 |319.5 |324.1	|321.2 |320.2 |326.6 |323.4 |
|SIFT-BRIEF	     |117.7	|100.5 |100.3 |115.4 |101.5	|102.9 |100.8 |104.9 |106.1 |
|SIFT-ORB	     |NA	|NA	   |NA	  |NA    |NA	|NA    |NA	  |NA	 |NA    |
|SIFT-FREAK		 |149.2	|133.7 |132.1 |137.7 |132.8	|137.7 |157   |146.5 |143.8 |
|SIFT-AKAZE	     |NA	|NA	   |NA	  |NA    |NA	|NA    |NA	  |NA	 |NA    |
|SIFT-SIFT	     |173.3	|171.7 |171.2 |171	 |189.5	|174.5 |172.3 |215.6 |201.2 |


## Here are few observations during performance evaluation:

- For matching with SIFT descriptor we need to use FLANN. SIFT does not work with BF
- SIFT detector and ORB descriptor do not work together. Insifficient Memory error
- AKAZE detector works only with AKAZE descriptor

## TOP3 Detector - Descriptor Combinations

|TOP3 COMBINATION	|AVERAGE TIME (ms)	|AVERAGE MATCH|
|-------------------|-------------------|-------------|
|FAST-ORB	        |309	            |7.59         |
|FAST-BRIEF	        |316	            |8.52         |
|ORB-BRIEF	        |50	                |9.97         |

