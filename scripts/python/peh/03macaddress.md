Media access control
 - permanent
 - physical
 - unique

Source and Destination MAC's are used on networks Layer 2/3

Networks can filter by MAC's
 - changing MACs can impersonate/bypass this

```sh
# display current network
ifconfig
# turn off network device before modifying
ifconfig eth0 down
# modify hardware id / mac address
ifconfig eth0 hw ether 00:11:22:33:44:55
# turn on network device 
ifconfig eth0 up
```

Using a module to execute system commands
 - The `subprocess` module contains a number of functions
 - These functions allow us to *execute system commands*.
 - Commands depend on the OS which execute the script

[Syntax example](https://docs.python.org/3/library/subprocess.html):
```python
#!/usr/bin/env python3
import subprocess

subprocess.call("ifconfig", shell=True)
```

Now lets implement everything into a simple script

```python
import subprocess

# shell=True will output the command
subprocess.call("ifconfig eth0 down", shell=True)
subprocess.call("ifconfig eth0 hw ether 00:11:22:33:44:55", shell=True)
subprocess.call("ifconfig eth0 up", shell=True)
```

We can break this down a little better
 - `interface` - not always `eth0` could be `wlan0`
 - `mac_addr` - we want to swap this to remain anonymous on a network

```python
import subprocess

interface = "eth0"
mac_addr = "10:00:10:00:00:00"

print("[+] Changing MAC address for " + interface + " to " + mac_addr)

subprocess.call("ifconfig " + interface + " down", shell=True)
subprocess.call("ifconfig " + interface + " hw ether " + mac_addr, shell=True)
subprocess.call("ifconfig " + interface + " up", shell=True)

print("MAC Address has been updated 🎉")
```

or in `golang`

```go
package main

import (
	"fmt"
	"os"
	"os/exec"
)

func main() {
	interfaceName := "eth0"
	macAddr := "10:00:10:00:00:00"

	fmt.Println("[+] Changing MAC address for", interfaceName, "to", macAddr)

	// Bring down the interface
	if err := exec.Command("ifconfig", interfaceName, "down").Run(); err != nil {
		fmt.Fprintf(os.Stderr, "Error bringing down interface: %v\n", err)
		os.Exit(1)
	}

	// Change MAC address
	if err := exec.Command("ifconfig", interfaceName, "hw", "ether", macAddr).Run(); err != nil {
		fmt.Fprintf(os.Stderr, "Error changing MAC address: %v\n", err)
		os.Exit(1)
	}

	// Bring up the interface
	if err := exec.Command("ifconfig", interfaceName, "up").Run(); err != nil {
		fmt.Fprintf(os.Stderr, "Error bringing up interface: %v\n", err)
		os.Exit(1)
	}

	fmt.Println("MAC Address has been updated 🎉")
}
```

Lets add user input to this script

```python
interface = input("select device >")
mac_addr = input("new MAC >")
```

or in golang

```go
reader := bufio.NewReader(os.Stdin) 

// Take user input for the interface 
fmt.Print("Select device > ") 
interfaceName, _ := reader.ReadString('\n') 
interfaceName = strings.TrimSpace(interfaceName) 

// Take user input for the new MAC address 
fmt.Print("New MAC > ") 
macAddr, _ := reader.ReadString('\n') 
macAddr = strings.TrimSpace(macAddr) 

fmt.Println("[+] Changing MAC address for", interfaceName, "to", macAddr)
```


Lets modularize it and make two functions
 - `generate_random_mac`
 - `change_mac_address`

```python
#!/usr/bin/env python3
import subprocess
import random

def generate_random_mac():
    # Generate random MAC address
    rand_mac = ""
    for _ in range(6):
        # Generate two random hexadecimal characters
        hex_pair = ''.join(random.choice('0123456789ABCDEF') for _ in range(2))
        rand_mac += hex_pair + ":"
    # Remove the trailing colon
    rand_mac = rand_mac[:-1]
    return rand_mac

def change_mac_address(interface):
    # Generate a random MAC address
    mac_addr = generate_random_mac()

    # Bring down the interface
    subprocess.call(["ifconfig", interface, "down"])

    # Change MAC address
    subprocess.call(["ifconfig", interface, "hw", "ether", mac_addr])

    # Bring up the interface
    subprocess.call(["ifconfig", interface, "up"])

# Change MAC address for eth0 interface
change_mac_address("eth0")
```


Or in golang

```go
package main

import (
	"fmt"
	"math/rand"
	"os"
	"os/exec"
	"time"
)

// Function to generate a random MAC address
func generateRandomMAC() string {
	rand.Seed(time.Now().UnixNano())

	const hexChars = "0123456789ABCDEF"
	macAddr := make([]byte, 12)
	for i := range macAddr {
		macAddr[i] = hexChars[rand.Intn(len(hexChars))]
	}
	// Insert colons to separate pairs
	for i := 2; i < len(macAddr); i += 3 {
		macAddr[i] = ':'
	}
	return string(macAddr)
}

// Function to change the MAC address of a network interface
func changeMACAddress(interfaceName string) error {
	// Generate a random MAC address
	macAddr := generateRandomMAC()

	// Bring down the interface
	if err := exec.Command("ifconfig", interfaceName, "down").Run(); err != nil {
		return err
	}

	// Change MAC address
	if err := exec.Command("ifconfig", interfaceName, "hw", "ether", macAddr).Run(); err != nil {
		return err
	}

	// Bring up the interface
	if err := exec.Command("ifconfig", interfaceName, "up").Run(); err != nil {
		return err
	}

	return nil
}

func main() {
	// Specify the network interface (change this to your interface name)
	interfaceName := "eth0"

	// Change MAC address for the specified interface
	if err := changeMACAddress(interfaceName); err != nil {
		fmt.Fprintf(os.Stderr, "Error changing MAC address: %v\n", err)
		os.Exit(1)
	}

	fmt.Println("MAC address changed successfully!")
}
```

