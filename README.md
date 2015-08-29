# PXP Agent

This is the agent for the Puppet Remote Execution Protocol (PXP), based on the
the Puppet Communications Protocol (PCP).

## Building from source

### Build requirements
 - a C++11 compiler (clang/gcc 4.7)
 - gnumake
 - cmake
 - boost
 - ruby (2.0 and newer)

Build with make and make install

## Configuring the agent

The PXP agent can be configured using a config file or supplying arguments on the command line.

The agent will first look in the user's home directory for *.pxp-agent* and then in
*/etc/pxp/agent.cfg. A different config file can be specified by passing the --config-file flag

The config files use the JSON format. Options must be specified as entries of a
single JSON object. Example:

```
{
    "server" : "wss://127.0.0.1:8090/pxp/",
    "ca" : "/Users/psy/work/pxp-agent/test-resources/ssl/ca/ca_crt.pem",
    "cert" : "/Users/psy/work/pxp-agent/test-resources/ssl/certs/0005_agent_crt.pem",
    "key" : "/Users/psy/work/pxp-agent/test-resources/ssl/certs/0005_agent_key.pem"
}
```

## Config options

The PXP agent has the following configuration options

**config-file (optional)**

Specify which config file to use.

**server (required)**

The PXP server you wish to connect the agent to, example wws://192.168.0.1:8061/pxp/

**ca (required)**

The location of your CA certificate, example /etc/puppet/ssl/ca/ca_crt.pem

**cert (required)**

The location of the pxp-agent certificate, example /etc/puppet/ssl/certs/bob_crt.pem

**key (required)**

The location of the pxp-agent's private key, example /etc/puppet/ssl/certs/bob_key.pem

**logfile (optional)**

Location of the file where log output should be written to, example /var/log/pxp/agent.log.
If logfile is not configured output will be logged to the console

**spool-dir (optional)**

The location where the outcome of non-blocking requests will be stored; the
default location is /tmp/pxp-agent/

### Starting the agent

The agent can be started by running
```
pxp-agent
```
in the ./build/bin directory
