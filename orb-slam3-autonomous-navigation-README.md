# ORB-SLAM3 Autonomous Navigation

**Stereo visual SLAM on embedded hardware for real-time localization where GPS isn't available.**

## Overview

This project implements autonomous navigation using ORB-SLAM3 for stereo visual simultaneous localization and mapping (SLAM), deployed on embedded hardware (Jetson Orin Nano) and integrated with ROS. It targets environments where GPS signal is unreliable or unavailable — indoors, dense urban canyons, or GPS-denied field conditions — by relying purely on visual odometry and mapping for real-time pose estimation.

## Tech Stack

- **ROS** — sensor integration, node communication, and navigation stack
- **ORB-SLAM3** — stereo visual SLAM for localization and mapping
- **Jetson Orin Nano** — embedded compute platform for onboard processing
- **C++** — core implementation

## Architecture

- A stereo camera rig feeds synchronized image pairs into ORB-SLAM3.
- ORB-SLAM3 extracts ORB features, tracks them across frames, and maintains a sparse map alongside real-time pose estimates.
- Pose estimates are published as ROS topics and consumed by the navigation stack for path planning and obstacle avoidance.
- All processing runs onboard the Jetson Orin Nano to keep the system self-contained and GPS-independent.

## Getting Started

### Prerequisites

- ROS (Noetic or later)
- ORB-SLAM3 dependencies (Pangolin, OpenCV, Eigen3, DBoW2, g2o)
- Jetson Orin Nano (or compatible embedded platform) with a stereo camera


## Notes

- Camera calibration files must match your specific stereo rig — recalibrate before deployment on new hardware.
- Performance is sensitive to lighting and feature-rich environments; low-texture scenes will degrade tracking quality.

## License

MIT
