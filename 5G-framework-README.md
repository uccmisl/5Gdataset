#README for 5G/mmWave simulation framework
The framework developed runs using the NS3 simulator. This requires some configuration prior to running the program to ensure the environment is set up correctly. Please follow the instructions in this readme to execute the program.

##Configuring the environment
These commands are taken directly form the NS3 website and can be found [here](https://www.nsnam.org/docs/tutorial/html/getting-started.html#building-ns-3 "NS3 Tutorial"). The waf executable can be found in the NS3 directory. In this program waf is located at `/ns3-mmwave-new-handover/`. The following commands assume you have changed your working directory to the above location.

Please make sure all dependencies for ns3 are installed prior to using this 5G framework

# minimum dependencies for ubuntu 19.10
sudo apt-get install net-tools build-essential git gcc g++ python python3 python3-dev python3-setuptools git mercurial -y


### CONFIGURING NS3
This commands must be run prior to any other commands, from within `/ns3-mmwave-new-handover/`.

    ./waf configure --enable-examples --enable-tests

### BUILDING NS3
This must be run prior to attempting any execution.

    ./waf build

##Running the Program
There are 2 ways to run the program, via the python scripts located at `/scripts` or by calling the waf executable directly.

### RUNNING VIA PYTHON
This is the recommended method of running the program. This command assumes you have changed your working directory to `/scripts` prior to running the below command.

### output the script help screen
    python start_mmwave.py -h 

### run the script
    python start_mmwave.py -ue 1 -enb 1 -t 1 -src "../ns3-mmwave-new-handover" -log "../mmwave_logs/" -x 100 -y 100 -z 100 -xVel 100 -yVel 100 -zVel 100 -i 0.1

| Flag | Description |
| ------------ | ------------ |
| `-t` | The simulation time to run the program for. |
| `-ue` | The number of UE to include in the simulation. |
| `-enb` | The number of eNodeB to in the simulation. |
| `-src` | The directory location of the NS3 waf executable. |
| `-log` | The directory to store logs. |
| `-x ` | The length of the x-axis defining the area to simulate. |
| `-y` | The length of the y-axis defining the area to simulate. |
| `-z`  | The length of the z-axis defining the area to simulate. |
| `-xVel` | The maximum acceptable velocity along the x-axis. |
| `-yVel` | The maximum acceptable velocity along the y-axis. |
| `-zVel` | The maximum acceptable velocity along the z-axis. |
| `-i` | The interval in seconds. |


### RUNNING VIA WAF
Important things to note when running via waf...
- Does not generate some of the traces that running via python will generate.
- Will not output progress in an easy to read format.
- Can be slower than running via python.
- No trace files will be formatted or parsed.

It is assumed you have changed your working directory to `/ns3-mmwave-new-handover/` prior to calling the below command.

      ./waf --run="my_sim_modified --simTime=1 --numUe=1 --numEnb=1 --maxX=100 --maxY=100 --maxZ=100 --maxXVel=100 --maxYVel=100 --maxZVel=100 --interval=0.1"

| Flag |  Description |
| -------- | -------- |
| `--simTime` | The simulation time to run the program for. |
| `--numUe` | The number of UE to include in the simulation. |
| `--numEnb` | The number of eNodeB to in the simulation. |
| `--maxX` | The length of the x-axis defining the area to simulate. |
| `--maxY` | The length of the y-axis defining the area to simulate. |
| `--maxZ` | The length of the z-axis defining the area to simulate. |
| `--maxXVel` | The maximum acceptable velocity along the x-axis. |
| `--maxYVel` | The maximum acceptable velocity along the y-axis. |
| `--maxZVel` | The maximum acceptable velocity along the z-axis. |
| `--interval` | The interval in seconds. |


### once the script completes, a new folder called 'mmwave_log' is created
This folder contains UL and DL logging details for the numberous UE(s) and eNB(s), across a range of parameters
