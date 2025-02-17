# RS to Velodyne
A ros tool for converting Robosense pointcloud to Velodyne pointcloud format, which can be directly used for downstream algorithm, such as LOAM, LEGO-LOAM, LIO-SAM, etc.

## Currently support:


### 1. [robosense XYZIRT] to [velodyne XYZIRT / XYZIR / XYZI]: (Recommended)
RS-16, RS-32, RS-Ruby, RS-BP and RS-Helios LiDAR point cloud.

### 2. [robosense XYZI] to [velodyne XYZIR]:
RS-16 and RS-Ruby LiDAR point cloud, More LiDAR model support is coming soon. 

### Notice: For rslidar_sdk v1.5+(2022), minor modifications should be made in the code. Please see https://github.com/HViktorTsoi/rs_to_velodyne/issues/11. This fix will soon be merged into the main stream.

## Usage

### 1. XYZIRT input
For **XYZIRT** format point clouds from `/rslidar_points` (Notice that, you need the latest 
[rslidar_sdk](https://github.com/RoboSense-LiDAR/rslidar_sdk) driver to get this type of point cloud):
```
rosrun rs_to_velodyne rs_to_velodyne XYZIRT XYZIRT
# or
rosrun rs_to_velodyne rs_to_velodyne XYZIRT XYZIR
# or
rosrun rs_to_velodyne rs_to_velodyne XYZIRT XYZI
``` 
The output point clouds are **XYZIRT** / **XYZIR** / **XYZI** point cloud `/velodyne_points` in Velodyne's format.

### 2. XYZI input
For **XYZI** format point clouds from `/rslidar_points`:
```
rosrun rs_to_velodyne rs_to_velodyne XYZI XYZIR
``` 
The output point clouds are **XYZIR** point cloud `/velodyne_points` in Velodyne's format.

### 3. XYZI input XYZIRT Output
```
rosrun rs_to_velodyne rs_to_velodyne XYZIT XYZIR
``` 
The output point clouds are **XYZIRT** point cloud `/velodyne_points` in Velodyne's format.

### 4. Airsim format to Velodyne Format
```
rosrun rs_to_velodyne airsim_velodyne
```
or 
``````
cd into scripts folder
python3 airsim_velodyne.py
``````

## Subscribes
`/rslidar_points`: sensor_msgs.PointCloud2, from Robosense LiDAR.

## Publishes
`/velodyne_points`: sensor_msgs.PointCloud2, the frame_id is `velodyne`.
