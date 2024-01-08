## piunifi.sh

A bash script to automate the setup and configuration of a Raspberry Pi for use as a UniFi Controller for Ubiquiti network devices.

This is a modified version of the script with the following changes:

- Install mongodb
- Install tailscale
- Remove some of the prompts
- Enable automatic updates

## IMPORTANT  

**If you already have a Unifi Controller running on the same network which you intend to replace with this piunifi you should backup the network settings from the existing controller to a file. This file can then be imported into the piunifi controller. Otherwise you will have to reset all your network devices to adopt them under the new piunifi controller.**

## Usage

NOTE: this script expects [raspios_oldstable_lite_arm64-2023-12-06](https://downloads.raspberrypi.com/raspios_oldstable_lite_arm64/images/raspios_oldstable_lite_arm64-2023-12-06/). I have not tested it on any other image.

1. Run `wget https://raw.githubusercontent.com/MaxAFriedrich/piunifi/main/piunifi.sh` to download the script
2. Read through the script to make sure you understand what it does and are okay with it
3. Run `chmod +x piunifi.sh` to make it executable
4. Run `sudo ./piunifi.sh` to run the script
5. Follow the instruction to set up tailscale when prompted
6. Wait for the system to reboot and finish initialising

## Known issues

You will need to ignore the browser SSL certificate error when accessing UniFi controller web interface. If you are accessing from a trusted private internal network this may not be an issue. However, if intend on access securely from an external/public network you should install a valid SSL certificate. There are a number of existing articles and videos on how to do this.

## Troubleshooting

Give the unifi service a few minutes to start upon reboot.  
The web interface is accessed on port 8443 and you must use https not http (Example: https://IPADDRESSOFPI:8443)  

If you still cannot access the web interface try checking the status of the service with the following command:  
`sudo systemctl status unifi`

The command output should contain `Starting unifi...` and eventually `Started unifi.`  
Otherwise check for errors in the status output.
