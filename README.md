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
 
## Connecting to your MRCP Server

Please see our [mrcp-api](https://github.com/lumenvox/mrcp-api) project for
details of configuring your MRCP server and connecting this to the LumenVox
cluster.
