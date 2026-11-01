# ros_ethercat_eml
ros_ethercat_eml package is a ROS 2 (ament_cmake) wrapper around the EML library. It has no ROS runtime dependency and logs to stderr.

Downstream packages use `find_package(ros_ethercat_eml)` and link `ros_ethercat_eml::ros_ethercat_eml`.

EML stands for Ethercat Master Library, but be aware that this is not a certified EtherCAT product.

# Disclaimer
This library is not guaranteed and not tested to be fully EtherCAT conformant, but it can be used to communicate with certain devices that use EtherCAT protocol at their Data Link Layer.
