# ROS Application Demo Snap

This snap demonstrates creating a simple ROS application as a snap using the
ROS core libraries in an Ubuntu 18.04 base snap.

The application is a simple talker/listener does not need the ROS core libraries
within the snap.


## Building

### Build and install the base snap
The snap is dependant on the [core18-ros](https://github.com/slimjim777/core18/tree/ros-base) snap.

```bash
# Fetch the base snap
git clone -b ros-base https://github.com/slimjim777/core18.git
cd core18

# Build the snap
sudo snapcraft
sudo snapcraft clean

# Install the snap
sudo snap install --dangerous --jailmode core18-ros_0.1_amd64.snap
```

### Build and install the application snap

```bash
# Fetch the base snap
git clone https://github.com/slimjim777/ros-app.git
cd ros-app

# Build the snap
sudo snapcraft cleanbuild

# Install the application snap
sudo snap install --dangerous --devmode ros-app_1.0_amd64.snap
```

Note that the application snap currently needs to be installed in `devmode`.

## Running the application

```bash
$ ros-app.launch-project

...
NODES                                                                                                                              
  /                                                                                                                                
    listener (listener/listener_node)                                                                                              
    talker (talker/talker_node)                                                                                                    
                                                                                                                                   
auto-starting new master                                                                                                           
process[master]: started with pid [6333]                                                                                           
ROS_MASTER_URI=http://localhost:11311                                                                                              
                                                                                                                                   
setting /run_id to 56d1efa0-b287-11e8-9f22-4437e6597978                                                                            
process[rosout-1]: started with pid [6363]                                                                                         
started core service [/rosout]
process[talker-2]: started with pid [6373]
process[listener-3]: started with pid [6380]
[ INFO] [1536315499.378274141]: Hello world 0
[ INFO] [1536315499.478320026]: Hello world 1
[ INFO] [1536315499.578291665]: Hello world 2
[ INFO] [1536315499.678290443]: Hello world 3
[ INFO] [1536315499.778302255]: Hello world 4
[ INFO] [1536315612.801269790]: Hello world 5
[INFO] [1536315612.801877]: I heard Hello world 5
[ INFO] [1536315612.901271386]: Hello world 6
[INFO] [1536315612.901833]: I heard Hello world 6
[ INFO] [1536315613.001287531]: Hello world 7
[INFO] [1536315613.001841]: I heard Hello world 7
```
