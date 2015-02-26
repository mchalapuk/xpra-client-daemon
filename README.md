# Xpra Client Daemon

Daemon that continously tries to connect to configured xpra servers.
It is intended to be run as unpriovileged user.

## Installation

Simply download the script and make it an executable file.

```bash
BIN_DIR=~/bin # change this if you want
mkdir -p $BIN_DIR
wget https://github.com/muroc/xpra-client-daemon/raw/master/xpra-client \
  -O $BIN_DIR/xpra-client
wget https://github.com/muroc/xpra-client-daemon/raw/master/xpra-client \
  -O $BIN_DIR/xpra-client-daemon
chmod +x $BIN_DIR/xpra-client*
```

If `BIN_DIR` is no on the `PATH`, modify `PATH` in rc file of your shell.

```bash
RC_FILE=~/.bashrc # change if you are not using bash
echo "PATH=$BIN_DIR:$PATH" >> $RC_FILE
. $RC_FILE
```

## Configuration

Each xpra server needs a directory at location
`~/.xpra/client-daemon/${SERVER_NAME}`. If directory is present,
it means that server is configured.

## Usage

### The basics

Currently, only tcp xpra servers that listen at port 8080 are supported
(address configurability is planned).

```bash
xpra-client-daemon start # starts client daemons for all configured servers
xpra-client-daemon stop # stops client daemons for all configured servers
xpra-client-daemon status # prints status info for all client daemons
xpra-client-daemon usage # prints usage information
```

Script `xpra-client` connects to xpra server just once in foreground
(no daemon behaviour).

```bash
xpra-client browser # connects to xpra server at tcp:browser:8080
```

## Contribution

Push requests are very welcome.

### TODO

 * configurable address of xpra server in
   `~/.xpra/client-daemon/${SERVER_NAME}/config`
 * single-server daemon operations (e.g. `xpra-client-daemon browser start`)
 * *Background* section before *Installation* in README.md
 * gif-animated usage at the top of README.md file

