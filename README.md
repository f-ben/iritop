# iritop

##  Simple Iota IRI Node Monitor

This is a simple monitor that runs from the command line. Typically this is run on the IRI node itself, however, as soon as the node is allowed to externally expose getNodeInfo and getNeighbors information, then this tool can be run from a remote shell as well.

The primary motivation to build this tool for me was to have a way of continously monitoring my Iota IRI nodes using a lightweight tool that can be run on both the server terminal and from a remote command line.

The Monitoring tool will show basic information on the node like version, milestone information and jre memory usage. It will also show the details of the neighbors connected to the node. Transaction counts are shown for Total, New, Random, Sent and Invalid transactions.

Where possible, the tool will highlight where the statistics are outside the norm by highlighting in yellow or red.

![IRITopScreenshot](https://raw.githubusercontent.com/maeck70/iritop/master/img/IRITop.png)

## Installation
1. Clone repository
```sh
git clone https://github.com/f-ben/iritop.git && cd ./iritop
```
2. Install python3 and python3 package manager
```sh
sudo apt-get install python3 python3-pip python3-setuptools -y
```
3. Requirements are listed in `requirements.txt` and can be automatically installed via:
```sh
sudo pip3 install -r requirements.txt
```
4. Run with default settings:
```sh
./iritop.py
```

## Usage

- Start without a `--node` argument will assume 'http://localhost:14265' as the node address for the web service calls.
- Provide an address using `--node http://myirinode:14265` if you want to specify a specific address.
- Use 'Q' to exit from the tool.
- Use 'B' to toggle into baseline mode (baseline mode zeroes all transactions and shows increment from baseline mode start).
- Use 'O' to obscure addresses (Helpful if you desire to post a screenshot of the IRI node status).
- Use 'S' to go into sort column mode. As soon Sort column mode is activated the headers will show a number that corresponds with a specific column. Press that number key to activate sorting. Initiating sorting on the same column again reverses the sort order.  

## Arguments

```sh
  -h, --help            show this help message and exit
  -v, --version         show program's version number and exit
  -c CONFIG, --config CONFIG
                        configuration file. Defaults to ~/.iritop
  -n NODE, --node NODE  set the node we are connecting with. Default:
                        http://localhost:14265
  -p POLL_DELAY, --poll-delay POLL_DELAY
                        node poll delay. Default: 2s
  -b BLINK_DELAY, --blink-delay BLINK_DELAY
                        blink delay. Default: 0.5s
  -t URL_TIMEOUT, --url-timeout URL_TIMEOUT
                        URL Timeout. Default: 5s
  -o, --obscure-address
                        Obscure addresses. Default: Off
  -U USERNAME, --username USERNAME
                        IRI Username if required.
  -P PASSWORD, --password PASSWORD
                        IRI Password if required.
  -s SORT, --sort SORT  Sort column # (-# for reverse sorting)
```

## Configuration File

The configuration can also be set in yaml formatted file. By default the configuration file from ~/.iritop is read. All configuration parameters can be provided in the config file.

File should be in `yaml` format. Example:

```
node: http://mynode.com:14265
poll_delay: 2
blink_delay: 0.3
username: admin
password: verySecret123
sort: -3
```
