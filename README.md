# MRCP Client

Media Resource Control Protocol (MRCP) Test Client application.

This can be used for light testing of MRCP requests into the LumenVox
MRCP-API server when requesting ASR and TTS operations.

MRCPv1 (RTSP) and MRCPv2 (SIP) connectivity is supported.

Note that this is only distributed in binary form, and is designed for
testing purposes only. This utility is not designed for use in production,
as unnecessary latency and only basic error checking is in place.

## Installing the Application

To install the application, you must download and extract the binary, installing
it into your `/usr/local/bin/` folder as shown here:

```shell
curl -L https://github.com/lumenvox/mrcp-client/releases/download/v4.1.2/simple_mrcp_client-4.1.2.tar.gz -o simple_mrcp_client.tar.gz
sudo tar -xvzf simple_mrcp_client.tar.gz -C /usr/local/bin/
sudo chmod +x /usr/local/bin/simple_mrcp_client
```

Or, using a single command:

```shell
curl -Lp https://github.com/lumenvox/mrcp-client/releases/download/v4.1.2/simple_mrcp_client-4.1.2.tar.gz | sudo tar -xvzf - -C /usr/local/bin/ && sudo chmod +x /usr/local/bin/simple_mrcp_client
```

> Note that the application is designed to run on 64-bit Linux systems only,
> and has been tested on CentOS7, CentOS8, RockyLinux8, Ubuntu 20.04 LTS.
> Other operating systems should also work (such as RHEL variants) as there
> are minimal dependencies. Openssl is required for the optional encryption
> of traffic

## Running the Application

There are many optional parameters available for the test application. To see
a list of possible options, simply run the executable without any parameters:

```shell
simple_mrcp_client
```

This will display a list of options, parameters as well as some simple
examples

> Please note that if you are running this on a machine that is remote from
> the LumenVox mrcp-api, you may need to permit network (firewall) access
> and you will need to specify the target (mrcp-api) machine's IP address
> as well as the local machine's IP address (where the utility resides) so
> that full connectivity can be established.

## Running With Docker

If you would like to run the application with a container as opposed to
downloading the binary directly, you can use the `docker-compose.yaml`
found at the root of this project. Assuming you have Docker installed, you
can start the container from the root of this project with the following
command:
```shell
docker-compose up -d
```
This will start a container, `simple_mrcp_client`, which contains the
binary for the application. To enter the container, use the following
command:
```shell
docker exec -it simple_mrcp_client bash
```
This will open up a Bash shell from which you can run the application. The
application is already on the PATH, so you can run it with the following
command:
```shell
simple_mrcp_client
```
Running without any options will bring up a description of how to use the
application.

When you are done with the container, you can bring it down with the
following command, run from the root of this project:
```shell
docker-compose down
```

### Mapped folders
The docker-compose.yaml configures several folders to be mounted into the
container. To use these folders, you must first create them at the root of
the project. The following folders are mapped by default:
* `./grammars`
* `./ssml`
* `./audio`

Once the folders have been created, you can start the container. The
folders are mounted to the root folder inside the container (`/`). The
mounts are dynamic, so adding files to those folders in the container will
also add them to your local disk, and vice versa.
 
## Connecting to your MRCP Server

Please see our [mrcp-api](https://github.com/lumenvox/mrcp-api) project for
details of configuring your MRCP server and connecting this to the LumenVox
cluster.
