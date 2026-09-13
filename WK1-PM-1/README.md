Kali Linux 2026.2 — VirtualBox Setup
Setup
Host: Windows 10
Virtualization: Oracle VirtualBox

Kali files:

kali-linux-2026.2-virtualbox-amd64.vbox  → VM definition
kali-linux-2026.2-virtualbox-amd64.vdi   → Virtual disk

To add the VM:

VirtualBox → Machine → Add → select .vbox

Problems & Fixes
1. UUID Conflict
Error:

Has the same UUID as an existing virtual machine

Checked registered VMs with:

VBoxManage list vms

Removed the stale registration without deleting files:

VBoxManage unregistervm "Kali Linux"

2. VT-x Disabled
Error:

VT-x is disabled in the BIOS

BIOS changes:

Virtualization Technology                  Enabled
Virtualization Technology for Directed I/O Disabled

3. Windows Audio Lost
Windows showed:

No output devices found

Device Manager showed Conexant and Intel(R) with Code 45.

In BIOS:

Audio Device → Enabled

After saving and restarting, Windows detected the audio hardware again.

4. Kali IPv4 and DNS Configuration
Kali initially had an IPv6 address but no visible IPv4 address.

After checking the network configuration, Kali was found to have:

Interface: eth0
IPv4:      10.0.0.2/24
Gateway:   10.0.0.1
DNS:       10.0.0.1

Internet connectivity was confirmed by pinging an IP address:

ping -c 4 8.8.8.8

The ping succeeded, confirming that the IPv4 network connection was working.

The actual problem was DNS resolution. The following command was used to configure reliable DNS servers:

sudo nmcli connection modify "Wired connection 1" ipv4.dns "8.8.8.8 1.1.1.1"

The connection was restarted:

sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"

DNS was verified with:

nmcli device show eth0 | grep IP4.DNS

Result:

IP4.DNS[1]: 8.8.8.8
IP4.DNS[2]: 1.1.1.1

DNS resolution was then successfully tested:

ping -c 4 google.com

Result
Kali Linux 2026.2 running in VirtualBox
VT-x/virtualization working
UUID conflict resolved
Windows host audio restored
Internet connectivity verified
DNS resolution verified

Date: 10 September 2026
