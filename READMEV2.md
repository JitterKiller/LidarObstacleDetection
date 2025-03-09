# Lidar Obstacle Detection

**Lidar Obstacle Detection** is a project that processes real-world LIDAR point cloud data to detect obstacles in driving environments. The pipeline filters, segments, and clusters raw data to distinguish road surfaces from obstacles, making it a valuable tool for autonomous driving applications.

![Lidar Obstacle Detection Demo](https://user-images.githubusercontent.com/30608533/65621434-65750100-dfcc-11e9-864f-b9a93de1b16e.gif)

## Table of Contents

- [Overview](#overview)
- [Pipeline Workflow](#pipeline-workflow)
- [Installation of PCL](#installation-of-pcl)
  - [Ubuntu](#ubuntu)
  - [macOS](#macos)
  - [Windows](#windows)
- [Building and Running the Project](#building-and-running-the-project)
- [Contributing](#contributing)
- [License](#license)

## Overview

The main goal of this project is to process LIDAR point cloud data by:
- **Filtering** the raw data to remove noise,
- **Segmenting** the scene into road and obstacles, and
- **Clustering** the obstacles to generate bounding boxes.

These steps help in accurately detecting and visualizing obstacles in a driving environment.

## Pipeline Workflow

The project follows these key steps:

1. **Reading a PCD File:** Load the raw point cloud data.
2. **Data Filtering:** Remove noise and downsample data for efficient processing.
3. **Segmentation:** Distinguish between road surfaces and potential obstacles.
4. **Clustering:** Group the segmented data to identify individual obstacles.
5. **Bounding Box Calculation:** Enclose each detected cluster with a bounding box.
6. **Rendering:** Visualize the processed road and obstacles in the viewer.

## Prerequisites

Before building the project, make sure you have the following tools installed on your system:

- **CMake:** Used to configure and generate build files for your project.
- **Point Cloud Library (PCL):** Required for processing the LIDAR data.

### CMake Installation

#### Ubuntu

```bash
sudo apt update
sudo apt install cmake
```
#### macOS

#### Install via [Homebrew](https://brew.sh/)
```bash
brew update
brew options pcl
brew install pcl
```
#### Windows
1. Download [CMake](https://cmake.org/download/)
2. Install CMake:
   Run the installer and follow the instructions. Make sure to select the option to add CMake to the system PATH during installation.
3. Verify Installation:
   Open PowerShell and run:
  ```powershell
  cmake --version
  ```
If CMake is installed correctly, it should display the installed version.

## Installation of PCL

Before building the project, ensure that the Point Cloud Library (PCL) is installed on your system.

### Ubuntu

```bash
sudo apt install libpcl-dev
```

### macOS

#### Install via [Homebrew](https://brew.sh/)
```bash
brew update
brew options pcl
brew install pcl
```

### Windows

1. **Download [Visual Studio Community](https://visualstudio.microsoft.com/downloads/):**  
   Install Visual Studio with the _Desktop Development with C++_ workload.

2. **Install vcpkg Packet Manager:**
   ```powershell
   git clone https://github.com/microsoft/vcpkg.git
   cd vcpkg
   .\bootstrap-vcpkg.bat
   .\vcpkg integrate install
   ```
   Then depending on your machine, you either run this command if you're on Windows 64 bits
    ```powershell
    [System.Environment]::SetEnvironmentVariable('VCPKG_DEFAULT_TRIPLET','x64-windows', 'User')
    ```
   Or if you're Windows ARM
    ```powershell
    [System.Environment]::SetEnvironmentVariable('VCPKG_DEFAULT_TRIPLET','arm64-windows', 'User')
    ```
3. **Install PCL via vcpkg:**
    ```powershell
   .\vcpkg install pcl
    ```

## Building and Running the Project

Clone the repository and follow these steps to build and run the project:

```bash
git clone https://github.com/enginBozkurt/LidarObstacleDetection.git
cd LidarObstacleDetection
mkdir build 
cd build
cmake ..
make
./environment
```
