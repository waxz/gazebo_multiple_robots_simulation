# gazebo_multiple_robots_simulation
multiple robots simulation in gazebo, slam and navigation


  
# how to use
- ### one robot, gmapping
  
  ```sh
  roslaunch gazebo_multiple_robots_simulation warehouse_simulation_gmapping.launch
  ```
- ### one robot, amcl

  ```sh
  roslaunch gazebo_multiple_robots_simulation warehouse_simulation_localization.launch
  ```

  ```sh
  roslaunch amcl demo_USlam.launch
  ```


- ### multiple robots, amcl
  ```sh
  roslaunch gazebo_multiple_robots_simulation warehouse_simulation_localization_multiplerobot.launch
  ```
  ```sh
  roslaunch amcl demo_Slam_multiplerobot.launch 
  ```
# other useful tool
- ### [map2gazebo](https://github.com/waxz/map2gazebo)
  create gazebo model from `/map`
  
  add to world file
  ```
    <model name="my_mesh">
      <pose>0 30 0  0 0 -1.5707963</pose>
      <static>true</static>
      <link name="body">
        <visual name="visual">
          <geometry>
            <mesh><uri>model://map.stl</uri></mesh>
          </geometry>
        </visual>
        <collision name="collision">
          <geometry>
            <mesh><uri>model://map.stl</uri></mesh>
          </geometry>
          <laser_retro>0.0</laser_retro>
        </collision>
      </link>
    </model>
  ```

-  ### [velodyne_simulator](https://bitbucket.org/DataspeedInc/velodyne_simulator)

[turtlebot3_waffle_lidar.gazebo.xacro](urdf/turtlebot3_waffle_lidar.gazebo.xacro)
```xml
  <xacro:include filename="$(find velodyne_description)/urdf/VLP-16.urdf.xacro"/>
  <xacro:VLP-16 parent="base_link" name="velodyne" topic="/velodyne_points" organize_cloud="${organize_cloud}" hz="10" samples="440" gpu="${gpu}">
    <origin xyz="0 0 0.4" rpy="0 0 0" />
  </xacro:VLP-16>
```
