# jmeter-performace-testing

This repo encapsulates the use of JMeter as a performance testing tool. The download instruction for the JMeter and plugins. It also contains a sample performance test with JMeter hitting localhost and results shown on graph.

## Setup

### Installation

Install using brew using command: `brew install jmeter`

### Installing Plugins


Follow the following steps to install plugins

- Go to `Options` > `Plugins Manager`.
- If plugins not already installed go to `Available Plugins` Tab.
- Click on `Apply Changes and Restart JMeter`.

#### SSL Handshake Error

If you are getting the SSL Handshake error as mentioned in this [link](https://jmeter-plugins.org/wiki/PluginsManagerNetworkConfiguration/) follow the following steps:

- Download the plugin and unzip it.
- Copy the following files:
  - `./lib/jmeter-plugins-cmn-jmeter-0.4.jar` to jmeter_ext directory located at `/usr/local/Cellar/jmeter/{version}/libexec/`. Replace the `{version}` with the version that you have installed on your system.
  - `./lib/ext/jmeter-plugins-graphs-basic-2.0.jar` to jmeter_ext directory located at `/usr/local/Cellar/jmeter/{version}/libexec/ext/`. Replace the `{version}` with the version that you have installed on your system.
  
#### Recommended plugins to install are:

- https://jmeter-plugins.org/?search=jpgc-graphs-
- https://jmeter-plugins.org/wiki/PerfMon/ 
  - Usage Guide: https://www.blazemeter.com/blog/how-monitor-your-server-health-performance-during-jmeter-load-test/

  
#### Response Time
#### Average Thread over Time
#### ...


### Creating a JMeter Test

To create a JMeter test against localhost do the following:

- Open JMeter running command `jmeter`
- Name the `Test Plan`
- Add a `Thread Group`
  - Increase `Number of Threads (user)` count
  - Increase `Loop Count`
- Add `HTTP Request` Sampler i.e. Get request for localhost on port 8080 and path /login
- Add `View Result Tree` listner to view the results of the run.

- Run test with command `jmeter -n -t ./src/localhost-load-test.jmx -l ./out/localhost-load-test-results.csv`

### Generating HTML report

To generate and test adding a HTML report do the following:

- Add a response assertion to check that the `Response Code` Equals `200`
- Run test with command `jmeter -n -t ./src/localhost-load-test.jmx -l ./out/localhost-load-test-results.csv -e -o ./out/localhost-load-test-report/`

### Open Existing Tests

Use the following command to open existing test files: `jmeter -t ./src/localhost-load-test.jmx`

### Add basic graph

- Now graphs can be added to your JMeter tests by clicking on `Thread Group`. Then `Edit` > `Add` > `Listners` > Listner Name


