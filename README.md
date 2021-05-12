# SeniorProjectSAR

Code: main.ipynb
All code for this project can be found in the Jupyter Notebook file main.ipynb. Running the code requires connection to a hard drive owned by the Yale Social Robotics Laboratory.

CSV Output: output folder
There are also sample output CSV's in the output folder of this repository. Descriptions of these files can be found below.

Gaze Intersection Related CSV Output:

All of the csv’s listed below were obtained after analyzing the video found at the following path in the hard drive: '1_EXP05/week_1/rosbag_mm_2017-07-10-14-35-44_0.mbag_video_0.avi'. All of the csvs listed below have the same structure. The columns are “frame”, “valid_eye_gaze,” “left_eye_intersection,” “right_eye_intersection,” and “avg_eye_intersection.” The “frame” column refers to which frame of the video the intersection was calculated. The “valid_eye_gaze” column is a boolean value of either 0 or 1, where 0 means for the given frame, OpenFace could not find a gaze vector, and 1 means a gaze vector was found. The other three columns contain information about the intersection found when using the left eye gaze vector, the right eye gaze vector, and the average 3D gaze vector between the eyes. The data found in each of these columns is an array of the intersections found. The array could have anywhere from 0 to 3 elements in it. If the array is not empty, each element of the array will be a an array with the first element be a string describing what the gaze vector intersected with, and the second element will be the 3D coordinates of the intersection.
1. child_intersection_flipped_example.csv: results of 3D gaze vector intersection algorithm for the child when Y coordinates are negated for the child 
2. parent_intersection_flipped_example.csv: results of 3D gaze vector intersection algorithm for the parent when Y coordinates are negated for the child
3. child_intersection_not_flipped_example.csv: results of 3D gaze vector intersection algorithm for the child when Y coordinates are not negated for the child
4. parent_intersection_not_flipped_example.csv: results of 3D gaze vector intersection algorithm for the child when Y coordinates are not negated for the child

Gaze Clustering Related CSV Output:

1. test_values_noise_res.csv:
This csv contains the noise results of running the clustering algorithm forcing 3, 2, or 1 clusters on participant1’s 3D average gaze vectors, 2D gaze vector, and pose rotation data, where epsilon is not pre-set. The columns are method, num_training_sessions, child_total_noise, child_average_noise, child_std_noise, parent_total_noise, parent_average_noise, parent_std_noise. The method column refers to which data we are using in the clustering algorithm (participant1’s 3D average gaze vectors, 2D gaze vector, or pose rotation). The column num_training_sessions refers to how many training sessions were found in participant 1 data. The columns child_total_noise and parent_total_noise refer to how many total noise points were found for the child and parent data sets respectively after clustering. The columns child_average_noise and parent_average_noise refer to the average number of noise points found per training session for the child and parent data sets respectively after clustering. The columns child_std_noise and parent_std_noise refer to the sum of the mean noise points found and the standard deviation found for the child and parent data sets respectively after clustering.

2. epsilon_noise.csv:
This csv contains the noise results of running the clustering algorithm forcing 3, 2, or 1 clusters on participant 1’s 3D average gaze vector data for different epsilon values. The columns of this csv are eps_value, child_mean_noise, child_std_noise, child_mean_std, parent_mean_noise, parent_std_noise, and parent_mean_std. Eps_value refers to what epsilon value was used. The child_mean_noise and parent_mean_noise columns refer to the average noise points found among participant 1 training sessions. The child_std_noise and parent_std_noise columns refer to the standard deviation noise points found among participant 1 training sessions. The child_mean_std and parent_mean_std columns refer to the sum of the respective mean and standard deviation columns.


All CSV’s found in the folder output/final_clustering_2:

The files in this folder refer to the result of clustering a single participant’s 3D average gaze vectors with an epsilon value of 0.95. Each csv is labeled as the participant’s string + “.csv”. The column labels for all of these files are session, num_clusters_child,  eps_max_child, child_noise, child_info, num_clusters_parent, eps_max_parent, parent_noise, parent_info. The session column refers to what number session the clustering results is from for the particular participant. The columns num_clusters_child and num_clusters_parent refer to the number of clusters found for the child and caregiver data respectively. The columns eps_max_child and eps_max_parent refer to the epsilon value used when clustering the child and caregiver data respectively. These values should always be 0.95. The columns child_noise and parent_noise refer to the number of noise points found when clustering the child and caregiver data respectively. The columns child_info and parent_info contain arrays with information on each cluster found in the child and caregiver data respectively. The dictionaries for each cluster contain the mean and standard deviation value for the X, Y, and Z 3D gaze vector components for points in the cluster.
