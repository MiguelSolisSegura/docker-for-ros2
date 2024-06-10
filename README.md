# TortoiseBot ROS2 Docker

This repository contains Docker images and Docker Compose configuration files for managing the bringup of the TortoiseBot robot in a ROS2 environment. The goal is to simplify the setup and usage of the TortoiseBot simulation and real robot systems through containerization.

## Overview

The repository is structured to provide Docker images for different aspects of the TortoiseBot environment, including simulation, mapping, and RViz2 for visualization. Docker Compose is used to manage and run these containers efficiently.

## Docker Images

The following Docker images are created and used in this project:

- **tortoisebot-ros2-gazebo**: Contains everything necessary for starting the Gazebo simulation in ROS2.
- **tortoisebot-ros2-slam**: Contains everything necessary for starting the mapping system, including RViz2 for visualization.
- **tortoisebot-ros2-real**: Contains everything necessary for starting all the real robot systems, including the camera and laser.
- **tortoisebot-ros2-slam-real**: Contains everything necessary for starting the mapping system for the real robot.

## Prerequisites

Ensure you have Docker and Docker Compose installed on your system. You can follow the instructions below to install them if they are not already installed:

```sh
sudo apt-get update
sudo apt-get install docker.io docker-compose
sudo service docker start
sudo usermod -aG docker $USER
newgrp docker
```

## Getting Started

### Cloning the Repository

Clone this repository to your local machine:

```sh
git clone https://github.com/MiguelSolisSegura/tortoisebot_ros2_docker.git
cd tortoisebot_ros2_docker
```

### Building the Docker Images

Build the Docker images using the provided Dockerfiles:

```sh
docker-compose build
```

### Running the Containers

Start all the containers using Docker Compose:

```sh
docker-compose up
```

Verify that the expected containers are up and running:

```sh
docker ps
```

Expected Output:

```
IMAGE                         CREATED                STATUS                NAMES
tortoisebot-ros2-gazebo       About a minute ago     Up About a minute     tortoisebot-ros2-gazebo_1
tortoisebot-ros2-slam         About a minute ago     Up About a minute     tortoisebot-ros2-slam_1
```

### Testing the Simulation and Mapping

To test the Gazebo simulation and mapping process, ensure that the containers are running and open RViz2 to visualize the mapping process.

## Stopping the Containers

To stop the running containers, use the following command:

```sh
docker-compose down
```

## Troubleshooting

If your simulation does not load properly the first time, relaunch it, and it should work correctly.

In some cases, the `gzserver` process might not die properly even after stopping the simulation, causing issues. Find and kill the process manually with the following commands:

```sh
ps faux | grep gz
kill -9 <process_id>
```

## Contributing

Contributions are welcome! Please fork this repository, create a new branch, and submit a pull request with your changes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact

For any questions or issues, please open an issue on this repository or contact the repository owner at [your_email@example.com].

---

Happy coding with TortoiseBot and Docker!
