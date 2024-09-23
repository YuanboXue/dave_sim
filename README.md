Lab notebook

Project: Dataset collection based on BlueROV2

Background: 
Aiming at the underwater dataset collection, we carried out the outdoor experiment in Sun Yat-Sen University (Zhuhai Campus). The goal is collecting dataset for localization with ground truth provided by the tags.

Period: 09/16/2024 – 09/21/2024

Content:
09/16/2024
Experimental setup:
Take a boat to Zhuhai. 
Successfully passed through customs. The customs require unpacking and approval based on the statement letter (questioning why the application form only has PolyU's seal and not Sun Yat sen University's seal, explaining and approval based on the invitation email from DING Shuoshuo).
Test the magnets.

09/17/2024

Experimental setup:
    • Due to long-distance transportation, check if all screws are tightened.
      
    • Wear gloves and install tags on the side walls of the pool.
      
    • Put the battery into the pressure chamber, seal it, and measure the pressure.

Tasks performed:
    • Check the balance of the robot in the water 
      
    • Manipulate it to see if it can move 
      
    • Check whether the signals are there or not 
      
    • Measure the relative position of all tags

Procedures Followed:
    • When measuring the pressure, 1) use a vacuum pump to evacuate the cavity of the underwater robot, and 2) detect whether the pressure value inside the cavity changes within a time threshold, thereby determining the sealing of the underwater robot. 
      
      Easy and convenient operation, no need for pressure. Effectively avoiding damage to electronic devices caused by pressure, improving detection efficiency, and reducing detection costs. 
      
      Among them, the pressure threshold is 10-15, the time threshold is 10-15 minutes.
      
    • Do not activate the stabilization mode, especially on land, activate the manual mode

Results:
    1. Observations:
    • UUV sank to the bottom of the pool, with 4 weights, without kickboards
    • UUV can move via joystick but unstable pitch angle and yaw angle
    • When underwater, UUV can successfully receive the rostopic of all sensors
    2. Data collected:
    • 09_17_trail1是：tag No.1（多）
    • 09_17_trail2是：tag No.4（单）（怀疑是4不是2，hy也觉得是4）
    • 09_17_trail3是：tag No.1（多）
    3. Analysis:
       None.

Conclusion:
    [Summarize the findings of the day’s experiment]
    [Discuss any deviations from expected results]
    [Note any potential sources of error]

Next Steps:
    Collect more data of various trajectories

Additional Notes: 
每次先把下面电池舱的蓝色气压帽拧下来，然后用一字螺丝刀撬电池盖子，再拔出来。因为每次拔都是薅那俩线，所以要注意那俩不要松（松的话，就用那个扳指一样的拧那个帽，拧的时候要注意，固定另一面的小螺母，不然会转空）。每次安上的时候，先扣黑色盖，再拧上蓝色气压帽。扣上黑色盖和拧上蓝色气压帽的时候都注意一下硅脂够不够，不够就补。

09/18/2024

Experimental setup:
    • Adjust for proper counterweight
      
    • Buy kickboard

Tasks performed:
    • Make sure the UUV can float on the water instead of sinking
      
    • Convert stereo camera messages in the rosbag to images for detection (./bag_to_image.py)
      
    • Collect data with raincoat, rain pants and rubber boots

Procedures Followed:
    • With single tag in the field of view, manually let the UUV move slowly and collect data
      
    • Include different trajectories (straight line, T line, circular trajectory, “8” trajectory)

Results:
    1. Observations:
    • UUV float on the water with kickboards and ribbons
    • UUV can detect the tag within a very small distance (30-40 cm)
    2. Data collected:
    • 09_18_trail2是：tag No.4（单）
    • 09_18_trail3是：tag No. 5
    • 09_18_trail4是：tag No. 2
    • 09_18_trail5 和 09_18_trail6是手柄操作长轨迹，包括直线、圆等等
    3. Analysis:
       Found the tags are wrong. The ratio of black area and white area is not correct. Haochen recreate the tags. We need to collect data again for all trajectories.

Conclusion:
    Poor water quality in outdoor swimming pools
   The QR code used for localization cannot be without white borders, nor can it have too few white borders. Can download the Apriltag Detector for detection from the Google Play Store.

Next Steps:
    Print the new correct tags using PVC board. Recollect datasets.

Additional Notes: 
    None.

09/19/2024

Experimental setup:
    • Test new tags if they can be detected by the stereo camera mounted on UUV
    • Place these new tags and record their relative positions

Tasks performed:
    • Controlling the robot by hand along the boundary of the swimming pool to follow a rectangular trajectory
      
    • Detect these new correct tags (1*1 and 2*2 tags) and follow different trajectories (straight line, T line, circular trajectory, “8” trajectory)

Procedures Followed:
    • With single tag in the field of view, manually let the UUV move slowly and collect data
      
    • Include different trajectories (straight line, T line, circular trajectory, “8” trajectory)

Results:
    1. Observations:
    • Exist two datasets with low frequency and data loss of BlueROV2 IMU and pressure sensor
    2. Data collected:
    • 09_19_trail1是：along the boundary of the swimming pool to follow a rectangular trajectory
    • 09_19_trail2是：along the boundary of the swimming pool to follow a rectangular trajectory
    • 09_19_trail3, 09_19_trail4, 09_19_trail5是：tag No. N1 (straight line, T line, circular trajectory, “8” trajectory)
    • 09_19_trail6: from N1 to N2 tag (low frequency, sometimes data loss) (run the detection script meanwhile)
    • 09_19_trail7: UUV light on, from N1 to N2 tag (low frequency, sometimes data loss) (not run the detection script when record rosbag)
    3. Analysis:
       Due to the poor water quality, we print the 40cm * 40cm PVC board. It cannot be too small. And it cannot be too large because of the water depth. Actually the water depth is 84 cm and the UUV height is around 39.5 cm. So the board could be larger, but we are told the water depth is around 50 cm so we print 40cm*40cm.
       Water quality is poor -> the detection distance is small -> the trajectory is short 
       Water quality is poor -> the tag should occupy most of the field of view to be detected -> pitch angle could not large

Conclusion:
    We’ve collected dataset with all sensor measurements along a certain trajectory.

Next Steps:
    Collect more data
    Another scheme with third perspective (iphone in the air)

Additional Notes: 
    The data loss issue should be solved. If low frequency, we can still utilize the dataset. But if lose data, the dataset could not be used.

09/20/2024

Experimental setup:
    • Place these new correct tags at each corner of the pool so that when the UUV moves along the sidewalls, at each corner, the tags could be utilized as landmark (may be possible)

Tasks performed:
    • Controlling the robot by hand along the boundary of the swimming pool to follow a rectangular trajectory
    • Detect these new correct tags at each corner
      
Procedures Followed:
    • manually let the UUV move slowly along the sidewalls and collect data
    • make sure the tags are in the field of view at each corner
    • take a top-down view on the second floor

Results:
    1. Observations:
    • On the second floor, the 1*1 tag could be detected
    • In the first few round of collection, the BlueROV2 IMU and pressure sensor both lose data and have low frequencies. We shut down all extra terminals but once we start the operation IMU frequency begin to decrease
    • Suddenly, at 12 noon, the imu frequency does not decrease and hold 20 hz. And we quickly collected several sets of data.
    2. Data collected:
    • 09_20_trail1是：along the boundary of the swimming pool to follow a rectangular trajectory. Without the imu data and press data.
    • 09_20_trail2是：along the boundary of the swimming pool to follow a rectangular trajectory (low frequency and data loss)
    • 09_20_trail3是：along the boundary of the swimming pool to follow a rectangular trajectory (low frequency and data loss of IMU and press)
    • 09_20_trail4是：along the boundary of the swimming pool to follow a rectangular trajectory (nice imu frequency: 19.7~20)
    • 09_20_trail5是：along the boundary of the swimming pool to follow a rectangular trajectory (nice imu frequency: 19.4~20)
    • 09_20_trail6, 09_20_trail7是：along the boundary of the swimming pool to follow a rectangular trajectory (nice imu frequency)
    3. Analysis:
       btok is a great tool to monitor memory requirements of various threads
       it is necessary to monitor the rostopic hz when operating not just the start point

Conclusion:
    We’ve collected dataset with all sensor measurements along sidewalls. We also collected dataset with a tag on the top of BlueROV2 and anoather tag on the side of pool.

Next Steps:
    Use the iphone to record a video of the calibration board and calculate the intrinsic parameters.
    Time alignment, etc. (data process)

Additional Notes: 
    For the recoding from the third perspective, the IMU is 10hz without data loss. Also, the first two rounds are manual operations. And the 3rd and 4th round are joystick operations.

For the reason of low mavros frequency and data loss (imu topic and pressure topic both under mavros), 也许是因为ros不适合存储大量图片信息

或许可能可以的解决办法是，在上位机运行并保存图片，ros只record 时间戳和帧号，然后后处理时候对应

不保证可行，但据说大疆的运动相机是这么干的

浮心要在上面,重心要在下面,pitch控制不了，所以得配重时候保证前后重量平衡。对于调整重力和浮力，一个方法是垂直推进器装在外面（然后中间的原垂直推进器位置放泡沫），第二个办法是skid底板改用泡沫材质

工具箱改定制派力肯Pelican（防水）
板子用嘉立创定制
