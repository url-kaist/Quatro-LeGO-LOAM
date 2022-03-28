# Quatro-LeGO-LOAM
## Robust Global Registration Quatro (22 ICRA) + LeGO-LOAM (18 IROS)
- For more details for each algorithm, <br>
  Quatro https://github.com/url-kaist/quatro <br>
  LeGO LOAM https://github.com/RobustFieldAutonomyLab/LeGO-LOAM <br>
  
## Test Env.

The code is tested successfully at
* Linux 18.04 LTS
* ROS Melodic

## How to Build

### ROS Setting
1. Install the following dependencies

```
sudo apt install cmake libeigen3-dev libboost-all-dev
```

2. Install [ROS](http://torch.ch/docs/getting-started.html) on a machine.
3. ~~Thereafter, [jsk-visualization](https://github.com/jsk-ros-pkg/jsk_visualization) is required to visualize Ground Likelihood Estimation status of [Patchwork](https://github.com/LimHyungTae/patchwork)~~

~~(Note that Patchwork is not directly related to Quatro. Patchwork is just used as preprocessing before feature extraction & matching. More details are [here](#How-to-Run-Quatro))~~
Actually, in Quatro-LeGO-LOAM, We don't use Patchwork.

* Then, run the following script. We use [catkin tools](https://catkin-tools.readthedocs.io/en/latest/),

```
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src
git clone git@github.com:url-kaist/quatro.git
cd quatro && mkdir build && cd build
# To build Quatro, `pmc-src` should be placed in `build` directory in catkin workspace
# i.e. `~/catkin_ws/build/pmc-src`
cmake ..
mv pmc-src/ ../../../build/
cd ~/catkin_ws
catkin build quatro 
```

**Note that without `pmc-src`**, the below error occurs!

``` 
CMake Error at quatro/CMakeLists.txt:53 (add_subdirectory):
  add_subdirectory given source "~/catkin_ws/build/pmc-src" which
  is not an existing directory.
 ```
 
4. Lastly, `git clone` this repo(Quatro-LeGO-LOAM) in your workspace and then `catkin_make`.
 
## Example
