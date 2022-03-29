# movai-ports-and-messages-ce

This repository will provide you the following:
- A set of ports and messages metadata supported on the movai-flow&trade;

## Release Status
| Package         | Noetic |
| :---:           | :---:  |
| movai_ports_and_messages_ce      | [![Deploy - To Nexus On Github Release](https://github.com/MOV-AI/movai_ports_and_messages_ce/actions/workflows/DeployOnGitRelease.yml/badge.svg)](https://github.com/MOV-AI/movai_ports_and_messages_ce/actions/workflows/DeployOnGitRelease.yml)

## Deploy Status (branch → main)
| Package         | Noetic |
| :---:           | :---:  |
| movai_ports_and_messages_ce      | [![Deploy - On branch main/release Push](https://github.com/MOV-AI/movai_ports_and_messages_ce/actions/workflows/DeployOnMergeMain.yml/badge.svg)](https://github.com/MOV-AI/movai_ports_and_messages_ce/actions/workflows/DeployOnMergeMain.yml)

## Continuous Integration Status

| Package         | Noetic |
| :---:           | :---:  |
| movai_ports_and_messages_ce  | [![CI - On main/dev/release branches](https://github.com/MOV-AI/movai_ports_and_messages_ce/actions/workflows/TestOnPR.yml/badge.svg)](https://github.com/MOV-AI/movai_ports_and_messages_ce/actions/workflows/TestOnPR.yml)


# Usage:

## Installation
- Get the latest released package from [releases page](https://github.com/MOV-AI/movai_ports_and_messages_ce/releases)
- Install the package using apt
```
sudo apt install ./ros-noetic-movai-ports-and-messages-ce_1.0.0-x_all.deb
```

## How to use
- Once installed, please restart your spwner container/
- The ports will appear on your node template/IO Configuration tab, when adding a new port.
- The movai_msg list will appear on the callback in the Message section in the Callback Details Menu.
- The information regarding each message and port are given in the next sectins.

## Callback
- place_holder: When a new port is created, this callback is used as a holder. It does not have any functions and it should not be edited or deleted.

## Messages
- movai_msgs:
  - Any: Ports with this message type can be linked to any other port regardles of their message type (eg: Port to measure frequency of a topic).
  - Context: Used to send a dictionry of data between two nodes through redis without a link in the flow, similar to the action client-server.
  - Init: Message type for the movai init port (details below).
  - Parameter: Used in ports which can get and set parameters in the ROS parameter server.
  - Reconfigure: Used in ports which can use the ROS reconfigure functionalities.
  - redis_sub: Used in ports to subscribe to a redis variable or redis key.
  - TF: Used in the ROS TF subscriber and publisher port (explained below).
  - Timer: Used in the ROS timer port (explained below).
  - Transition: Used for transition ports (explained below) in a state node.
  - Websocket: Used in ports that receive messages through websockets

## Ports
- AioHTTP:
  - Websocket: In port used for websocket messages
- MovAI:
  - ContextClient: Used on the client node to send commands to and recieve reply from a context server.
  - ContextServer: Used on nodes which act as servers to recieve input from context client nodes and reply with a response.
  - Dependency: 
  - Depends:
  - Init:
  - TransitionFor:
  - TransitionTo:
- Redis:
  - Subscriber:
  - VarSubscriber:
- ROS1:
  - ActionClient
  - ActionServer
  - NodeletClient
  - NodeletServer
  - ParameterServer
  - PluginClient
  - PluginServer
  - Publisher
  - ReconfigureClient
  - ReconfigureServer
  - ServiceClient
  - ServiceServer
  - Subscriber
  - TFPublisher
  - TFSubscriber
  - Timer
  - TopicHz
