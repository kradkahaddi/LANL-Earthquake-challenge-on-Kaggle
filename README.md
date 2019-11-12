# LANL-Earthquake-challenge-on-Kaggle
My jupyter notebook from the competition. This is the last state of the notebook, I scored in the top 69% place in the competition

The base concept is derived from Siraj Rival's video on how to tackle the contest. After that, I used a wavelet filter that I found on the public notebooks section. (All attributions are available in the relevant sections of the notebook). I also used a peak detection algorithm I found online. This was the game changer because I used the peak detection algorithm to measure activity in each sample.

The algorithms I created to do this were:

Tangential measures:

left_side_diff_max()
left_side_diff_mean()
right_side_diff_max()
right_side_diff_mean()

These functions measured the relative activity (or peakedness) around "peaks" by drawing straight line tangents between the peaks and their surrounds. max() would find the maximum peakedness or maximum tangent slope while mean() would find the mean tangent value and thus the mean relative peakedness.
A small return value (small tangent slope) means that peak has a uniform value and the region has high activity.
A large return value (large tangent slope) means that the peak is isolated and there is no activity in the surroundings.

Next I also measured the number of groups of activity in a sample using:
num_groups_data()

A sample with lots of activity would have many groups or a larger return value. A sample with very isolated activity would have a smaller return value. The idea was that there should be difference in activity before and after an earthquake.

I also used spread_of_data()
to measure the interval between the first and last peak in a sample.

The main disadvantage of the method using the peak detection algorithm is that I was limited to manually selecting the height of the peak I wanted to detect.
