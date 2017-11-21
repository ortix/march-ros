#  Getting Started

First we create a new directory for out Catkin workspace
```bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src
```

We can clone the repository and initialize the included submodule
```bash
# note the trailing dot '.' which clones the repo in the current directory
git clone https://github.com/Ortix92/march-ros.git .
git submodule update --init --remote
```

Return to the workspace root and build
```bash
cd ~/catkin_ws
catkin_make
```

Once the workspace has been built we source our workspace and run the node.
```bash
source devel/setup.bash
rosrun ethercat slaver
```
