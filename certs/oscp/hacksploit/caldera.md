Caldera is a cyber security framework designed to easily automate adversary emulation, assist manual red teams and automate incident response.

It is built on the MITRE ATT&CK framework and utilizes a client-server system, where the server is used to setup agents(clients) and initiate operations

The framework consist of two components:
1. The core system. This is the framework code, consisting of what is available in this repository. Included is an asynchronous command-and-control (C2) server with a REST API and web interface.
2. Plugins. These repositories expand the core framework capabilities and provide additional functionality. Examples include agents reporting, collections of TTPs and more.