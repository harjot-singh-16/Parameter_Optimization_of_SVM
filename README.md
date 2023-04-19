# Parameter_Optimization_of_SVM

We are optimizing the parameters of SVM(Support Vector Machine) for multiclass dataset.

# Dataset Analysis 

1. Title of Database: Pen-Based Recognition of Handwritten Digits

2. Source:
	E. Alpaydin, Fevzi. Alimoglu
	Department of Computer Engineering
	Bogazici University, 80815 Istanbul Turkey
	alpaydin@boun.edu.tr
	July 1998

3. Past Usage:
	F. Alimoglu (1996) Combining Multiple Classifiers for Pen-Based
	Handwritten Digit Recognition, 
	MSc Thesis, Institute of Graduate Studies in Science and 
	Engineering, Bogazici University.
	http://www.cmpe.boun.edu.tr/~alimoglu/alimoglu.ps.gz

	F. Alimoglu, E. Alpaydin, "Methods of Combining Multiple Classifiers 
	Based on Different Representations for Pen-based Handwriting
	Recognition," Proceedings of the Fifth Turkish Artificial 
	Intelligence and Artificial Neural Networks Symposium (TAINN 96), 
	June 1996, Istanbul, Turkey.
	http://www.cmpe.boun.edu.tr/~alimoglu/tainn96.ps.gz

	
4. Relevant Information:

	We create a digit database by collecting 250 samples from 44 writers.
	The samples written by 30 writers are used for training,
	cross-validation and writer dependent testing, and the digits 
	written by the other 14 are used for writer independent testing. This
	database is also available in the UNIPEN format.

	We use a WACOM PL-100V pressure sensitive tablet with an integrated 
	LCD display and a cordless stylus. The input and display areas are
	located in the same place. Attached to the serial port of an Intel 
	486 based PC, it allows us to collect handwriting samples. The tablet
	sends $x$ and $y$ tablet coordinates and pressure level values of the
	pen at fixed time intervals (sampling rate) of 100 miliseconds. 

	These writers are asked to write 250 digits in random order inside 
	boxes of 500 by 500 tablet pixel resolution.  Subject are monitored 
	only during the first entry screens. Each screen contains five boxes
	with the digits to be written displayed above. Subjects are told to
	write only inside these boxes.  If they make a mistake or are unhappy
	with their writing, they are instructed to clear the content of a box 
	by using an on-screen button. The first ten digits are ignored 
	because most writers are not familiar with this type of input devices,
	but subjects are not aware of this. 

	In our study, we use only ($x, y$) coordinate information. The stylus
	pressure level values are ignored. First we apply normalization to 
	make our representation invariant to translations and scale 
	distortions. The raw data that we capture from the tablet consist of
	integer values between 0 and 500 (tablet input box resolution). The 
	new coordinates are such that the coordinate which has the maximum 
	range varies between 0 and 100. Usually $x$ stays in this range, since
	most characters are taller than they are wide.  

	In order to train and test our classifiers, we need to represent 
	digits as constant length feature vectors. A commonly used technique
	leading to good results is resampling the ( x_t, y_t) points. 
	Temporal resampling (points regularly spaced in time) or spatial
	resampling (points regularly spaced in arc length) can be used here. 
	Raw point data are already regularly spaced in time but the distance
	between them is variable. Previous research showed that spatial
	resampling to obtain a constant number of regularly spaced points 
	on the trajectory yields much better performance, because it provides 
	a better alignment between points. Our resampling algorithm uses 
	simple linear interpolation between pairs of points. The resampled
	digits are represented as a sequence of T points ( x_t, y_t )_{t=1}^T,
	regularly spaced in arc length, as opposed to the input sequence, 
	which is regularly spaced in time.

	So, the input vector size is 2*T, two times the number of points
	resampled. We considered spatial resampling to T=8,12,16 points in our
	experiments and found that T=8 gave the best trade-off between 
	accuracy and complexity.


5. Number of Instances
	pendigits.tra	Training	7494
	pendigits.tes	Testing		3498
	
	The way we used the dataset was to use first half of training for 
	actual training, one-fourth for validation and one-fourth
	for writer-dependent testing. The test set was used for 
	writer-independent testing and is the actual quality measure.

6. Number of Attributes
	16 input+1 class attribute

7. For Each Attribute:
	All input attributes are integers in the range 0..100.
	The last attribute is the class code 0..9


Sample 10 gives best Accuracy.
![image](https://user-images.githubusercontent.com/104484529/233072889-149ab5b3-de1f-4417-bb18-34f67ecb70c7.png)
