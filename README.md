Here's a step-by-step guide for deploying an OpenVPN server on Linode, based on your instructions:

---

### Deploying OpenVPN on Linode

This guide will help you set up an OpenVPN server on a Linode instance running Ubuntu, enabling secure connections through a VPN.

---

#### Step 1: Deploy a Linode with Ubuntu
1. Log in to your Linode account.
2. Create a new Linode and choose **Ubuntu** as your operating system.
3. Select a data center, plan, and configure the instance according to your needs.
4. Once deployed, make a note of your Linode’s IP address.

#### Step 2: Update Your Server
1. Access your Linode via SSH:
   ```bash
   ssh root@your_linode_ip
   ```
2. Update and upgrade the packages:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

#### Step 3: Download the OpenVPN Installation Script
Download the OpenVPN install script provided by angristan:
   ```bash
   curl -O https://raw.githubusercontent.com/angristan/openvpn-install/master/openvpn-install.sh
   ```

#### Step 4: Make the Script Executable
1. Set the necessary permissions to run the script:
   ```bash
   chmod 777 openvpn-install.sh
   ```

#### Step 5: Run the OpenVPN Install Script
1. Start the OpenVPN installation script:
   ```bash
   ./openvpn-install.sh
   ```

#### Step 6: Accept Default Options
1. Press **Enter** to go with the default options as prompted during the setup process.

#### Step 7: Name the Client
1. When asked, name the client profile (for example, **Atlanta**).

#### Step 8: Transfer the Configuration File
1. Once the installation completes, a configuration file will be created for your client. The file is typically saved as `Atlanta.ovpn` in the server.
2. Copy the configuration file to your local machine. You can use `scp`:
   ```bash
   scp root@your_linode_ip:/root/Atlanta.ovpn ~/Atlanta.ovpn
   ```

#### Step 9: Install an OpenVPN Client Locally
1. On your local machine, download and install the OpenVPN client:
   - For **Windows**: [Download OpenVPN](https://openvpn.net/community-downloads/)
   - For **macOS**: Install through [Tunnelblick](https://tunnelblick.net/)
   - For **Linux**: Install via package manager, e.g., `sudo apt install openvpn` for Debian/Ubuntu.

#### Step 10: Connect Using Your VPN
1. Open your OpenVPN client and import the `Atlanta.ovpn` file.
2. Connect to the VPN by selecting the imported configuration file.
3. You are now connected to the internet securely through your VPN server.

---

Your OpenVPN server is now ready on Linode, and your device can connect through the VPN for secure internet access.
