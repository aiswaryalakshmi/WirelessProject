# WirelessProject

## Install the Node command line tool
### To install the Node module:

1. Download Google Chrome for Desktop.
1. Install the current Long-Term Support version of Node.
1. Install Lighthouse. The -g flag installs it as a global module.

```
npm install -g lighthouse
```

## Run the lighthouse cmd commands

```
cmd < lighthouse_commands.txt
```

## Packet-level throttling

Packet-level throttling tools are able to make the most accurate network simulation. While this approach can model real network conditions most effectively, it also can introduce more variance than request-level or simulated throttling.

The comcast Go package appears to be the most usable Mac/Linux commandline app for managing the network connection.<br>
Note: It changes the entire machine's network interface.

## comcast set up

```
# Install with go
go get github.com/tylertreat/comcast
# Ensure your $GOPATH/bin is in your $PATH (https://github.com/golang/go/wiki/GOPATH)

# To use the recommended throttling values:
comcast --latency=150 --target-bw=1638 --dry-run

# To disable throttling
# comcast --stop
```

## Using Lighthouse with comcast
```
# Enable system traffic throttling
comcast --latency=150 --target-bw=1638

# Run Lighthouse with its own throttling disabled
lighthouse --throttling.requestLatencyMs=0 --throttling.downloadThroughputKbps=0 --throttling.uploadThroughputKbps=0 # ...

# Disable the traffic throttling once you see "Gathering trace"
comcast --stop
```
