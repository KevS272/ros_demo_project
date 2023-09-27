# ros_demo_project
A demo project that shows a proposed structure of a modularized and containerized ROS system. It includes two submodules, where module 1 includes a talker/listener node in two packages whereas module 2 includes a node that subscribes to the topic of the talker and outputs a colored image based on the message data.

## Requirements
- Docker Engine
- Docker Compose plugin (If you're using Compose version 1, you need to use "docker-compose" instead of "docker compose" in your commands!)

## Setup
### 1. Clone the repository recursively!
```bash
git clone --recursive https://github.com/KevS272/ros_demo_project.git
```

### 2. Run Docker Compose up
```bash
sudo docker compose up
```

The Docker images get built and after that, compose will start up a container that automatically builds the Colcon workspace and starts the launch file that was specified in `docker/ros_entrypoint.sh` which gets copied into the image during the build process.

You can stop the nodes at any time using `CTRL` + `C` in the command line. The compose will stop the container (it does not delete it!). This means you can start the container again using `sudo docker compose up`.

#### Optional:
If you want to run the container detached, add the `-d` flag to the compose command like this:
```bash
sudo docker compose up -d
```
If you do this, you will have to `sudo docker compose stop` to stop the container or `sudo docker compose down` to completely remove it.

### 3. RECOMMENDED: Install Foxglove for visualization
Module 1 automatically starts a Foxglove websocket for visualization purposes through its launchfile.

Go to the [Foxglove website](https://foxglove.dev/download) and follow the instructions for installation

### 4. RECOMMENDED: Open Foxglove and connect to the websocket:
Click on `Open connection` and choose `Foxglove WebSocket`. In the websocket URL field, paste the following URL, which is the one from the module1 container:
```
ws://localhost:8765
```
After that, click on open.

### 5. RECOMMENDED: Load the provided demo Foxglove layout:
Click on the Layout dropdown menu in the top right corner of the Foxglove window and choose `Import from file`.
Navigate to this repo and load the `foxglove_demo_panel.json`. Now, you should see both the talker message as well as the changing color image in Foxglove.
