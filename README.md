# movai-ports-and-messages-ce

This repository will provide you the following:
- A set of ports and messages metadata supported on the movai-flow&trade.

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
  - Websocket: Used in ports that receive messages through websockets.

## Ports
- AioHTTP:
  - Websocket: In port, used for websocket messages
- MovAI:
  - ContextClient: In and Out port, used on the client node to send commands to and recieve reply from a context server through redis.
  - ContextServer: In and out port, used on nodes which act as servers to recieve input from context client nodes and reply with a response.
  - Dependency: In port, used to connect another node with a depends port. Usually used to assert dependency between nodes. Meaning if one node runs, the other one also does.
  - Depends: Out port, can be used to connect another node with a dependency port. Usually used to assert dependency between nodes. Meaning if one node runs, the other one also does.   
  - Init: In port, the callback associated with this port runs once the node starts. Like the init method of a class.
  - TransitionFor: In port, used in state nodes for state transitions. Connecting a link to this port will stop the other node starts this one.
  - TransitionTo:  Out port, used in state nodes for state transitions. Connecting a link to this port will stop this node and starts the next one.
- Redis:
  - Subscriber: In port, port used to subscribe to redis key. The callback is activated when there is a change in the key.
  - VarSubscriber: In port, port used to subscrive to a redis variable. It's similar to the subscriber above but has a context. You can set these vars in the callback as shown below:
    - Syntax: ```Var('Context').Function('variable_name', 'variable_value')```
    - Context:
      - 'Flow' -> Cleared at the start and end of a flow run.
      - 'Robot' -> Stays in the robot but cleaned when you re install a robot.
    - Function:
      - 'set' -> Set variable value
      - 'get' -> Get variable value
      - 'delete' -> Delete variable value
- ROS1:
  - ActionClient: In and Out ports, action client port.
  - ActionServer: In and Out ports, action server port.
  - NodeletClient: Out port, used to connect to a nodelet server.
  - NodeletServer: In port, used to connect to a nodelt client.
  - ParameterServer: Out port, used in nodes to set parameters in the parameter server. Context is set when the protocol is selected in the node template.
  - PluginClient: Out port, used to connect to a plugin server. Used in nodes such as global_planner to connect to server such as move_base.
  - PluginServer: In port, used to connect to a plugin client. Used in nodes such as move_base to connect to plugins such as local_planner. 
  - Publisher: Out port, ros topic publisher.
  - ReconfigureClient: Out port, used to update the reconfigure parameters by connecting to a reconfigure server.
  - ReconfigureServer: In port, used in nodes to recieve update requests from the client nodes.
  - ServiceClient: Out port, service client port.
  - ServiceServer: In port, service server port.
  - Subscriber: In port, ros topic subscriber.
  - TFPublisher: Out port, publsh to a TF tree. The from and to frame ids are set in the node template.
  - TFSubscriber: In port, subscribe to a specific transform in the TF tree. The from and to frame ids are set in the node template.
  - Timer: In port, independent port which activates the callback with a frequency. The frequency and the one_shot parameter is set in the node template. The port need not be connected to any other port to function.
  - TopicHz: In port, used to subscribe to the frequency of a topic. The message associated is Any, so any topic can be linked to this port.
