# ros2-web-bridge + cmd_vel_publisher in ROS2 foxy

![ros2_web_bridge_test](https://user-images.githubusercontent.com/44196066/136336240-dcf57b23-d1a3-4a72-94a6-2985072e8ce6.png)

## Basically this package based on ros2_web_bridge pkg
please check https://github.com/RobotWebTools/ros2-web-bridge for the fundamental installation


## Install

1. Prepare for ROS 2
    Please reference the [documentation](https://index.ros.org/doc/ros2/Installation/) to install ROS 2.
2. Install `Node.js`
    You can install Node.js:
    * Download from Node.js offical [website](https://nodejs.org/en/), and install it.
    * Use the Node Version Manager ([nvm](https://github.com/creationix/nvm)) to install it.
3. Clone and install dependencies
    Note that a ROS 2 installation has to be sourced before installing dependencies.
    ```bash
    $ git clone https://github.com/RobotWebTools/ros2-web-bridge.git
    $ cd ros2-web-bridge
    $ source /opt/ros/$DISTRO/setup.sh  # or a source installation
    $ npm install
    ```

## Run Examples

1. Make sure to source a ROS 2 installation, e.g.:
    ```bash
    $ source /opt/ros/$DISTRO/setup.sh  # or a source installation
    ```
2. Start `ros2-web-bridge` module:
    ```bash
    $ node bin/rosbridge.js
    ```
    If you want to start in client mode (i.e. connecting the bridge to an existing websocket server), do this instead:
    ```bash
    $ node bin/rosbridge.js --address ws://<address>:<port>
    ```
3. Start the [express](https://www.npmjs.com/package/express) server:
    ```bash
    $ cd examples && node index.js
    ```
4. Open your browser, and navigate to URL: http://localhost:3000/html/publisher.html

## Example of publishing Cmd_vel and check local PC
1. Open your browser, and navigate to URL :
    (default) ws/example/html/cmd_vel_pub.html

2. Set Connection as same as your ws://<address>:<port>
  and check the button "connect!"
    (default)_http://localhost:9090 (it can be changable as your flavor)

3. If you can see the connected sign, you are fully ready for sending the topic

(I took a test using turtlebot_node as the picture)
![ros2_web_bridge_w_gazebo](https://user-images.githubusercontent.com/44196066/136336121-dc4b0d68-2507-4441-aafc-4525356ca684.png)
* Subscribe to a topic.
  ```JavaScript
  // Define a topic with its type.
  var example = new ROSLIB.Topic({
    ros : ros,
    name : '/example_topic',
    messageType : 'std_msgs/String'
  });

  // Subscribe to a topic.
  example.subscribe(function(message) {
    console.log(`Receive message: ${message}`);
  });
  ```

## Contributing

If you want to contribute code to this project, first you need to fork the
project. The next step is to send a pull request (PR) for review. The PR will be reviewed by the project team members. Once you have gained "Look Good To Me (LGTM)", the project maintainers will merge the PR.

## License

This project abides by [Apache License 2.0](https://github.com/RobotWebTools/ros2-web-bridge/blob/develop/LICENSE).
