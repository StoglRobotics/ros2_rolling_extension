# ros2_rolling_extension
| :exclamation:  Note   :exclamation:                                                                                                                              |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|This isn't really an extension yet, but it mimics the [`ros2-humble`-extension](https://snapcraft.io/docs/ros2-humble-extension). Used for testing and could then be added to the official repos as extension.|
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
If you want ot build your own `my-ros2-rolling-code` in snap you can include this as follows:
```yaml
parts:
  my-ros2-rolling-code:
          <other stuff neeeded to build your code>
        build-environment:
        -   ROS_VERSION: '2'
        -   ROS_DISTRO: rolling

  ros2-rolling/ros2-launch:
      source: 'https://github.com/StoglRobotics/ros2_rolling_extension.git'
      source-branch: master
      plugin: nil
      override-build: >-
        install -D -m 0755 launch
        ${CRAFT_PART_INSTALL}/snap/command-chain/ros2-launch
      build-packages:
        - ros-rolling-ros-environment
        - ros-rolling-ros-workspace
        - ros-rolling-ament-index-cpp
        - ros-rolling-ament-index-python
```
Don't foget to specify the `build-environment` for your 
