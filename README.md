# VSCode ROS2 Workspace for ASLab

This ROS2 setup with VSCode is based on [this template](https://github.com/athackst/vscode_ros2_workspace). See its [README](https://github.com/athackst/vscode_ros2_workspace/blob/foxy/README.md) for a more in-depth look on how to use this workspace.

# If you are not using a computer with Nvidia graphic card, switch to branch [foxy-no-nvidia](https://github.com/aslab/ros2_docker/tree/foxy-no-nvidia)
## Prerequisites

You should already have Docker and VSCode with the remote containers plugin installed on your system.

* [Docker](https://docs.docker.com/engine/install/)
* [VSCode](https://code.visualstudio.com/)
* [VSCode remote containers plugin](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
* [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#pre-requisites)
```
distribution=$(. /etc/os-release;echo $ID$VERSION_ID) \
&& curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add - \
&& curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list

sudo apt-get update

sudo apt-get install -y nvidia-docker2
```


### Open this repository in VSCode

Clone this repository in your computer and open it in VSCode (File->Open Folder). 

When you open it for the first time, you should see a little popup that asks you if you would like to open it in a container.  Say yes!

![template_vscode](https://user-images.githubusercontent.com/6098197/91332551-36898100-e781-11ea-9080-729964373719.png)

If you don't see the pop-up, click on the little green square in the bottom left corner, which should bring up the container dialog

![template_vscode_bottom](https://user-images.githubusercontent.com/6098197/91332638-5d47b780-e781-11ea-9fb6-4d134dbfc464.png)

In the dialog, select "Remote Containers: Reopen in container"

VSCode will build the dockerfile inside of `.devcontainer` for you.  If you open a terminal inside VSCode (Terminal->New Terminal), you should see that your username has been changed to `ros`, and the bottom left green corner should say "Dev Container"

![template_container](https://user-images.githubusercontent.com/6098197/91332895-adbf1500-e781-11ea-8afc-7a22a5340d4a.png)


## Update the template with your code

1. Specify the repositories you want to include in your workspace in `ros2.repos` or delete `ros2.repos` and develop directly within the `/src` folder.
2. Create src folder `mkdir src`
3. If you are using a `ros2.repos` file:
   1. Import the contents `Terminal->Run Task..->import from workspace file`
2. Install dependencies `Terminal->Run Task..->install dependencies`
3. Develop!

## Running your code
Once the docker image is running and your code from 'src/ros2.repos' imported, compile your workspace:
   ```
   colcon build --symlink-install
   ```
### Comments
At the moment the `ros2.repos` loads [this](https://github.com/aslab/ign_simulation) repository. See its README for more information in how to use it. Omit the install parts and the source commands as the environment is already set up in the container.
