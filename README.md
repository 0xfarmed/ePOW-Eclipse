# 🚀 Beginner-Friendly Guide to Mining $BITZ on Eclipse (Ubuntu)

This guide will help you set up ePOW mining for Eclipse $BITZ tokens on Ubuntu in simple steps.

## What You'll Need

- Ubuntu Linux system
  Get a sever or VPS from Contabo - https://my.contabo.com/

  Get 4 vCPU Cores , costs about 5$ a month and should be good for our use-case.
  
  <img width="1226" alt="Screenshot 2025-04-12 at 11 22 35 AM" src="https://github.com/user-attachments/assets/7871f5f6-263d-4068-b910-c3385fc774ed" />

- Terminal access
  Get Terminus for connect to the above server - https://termius.com/download/macos

- Connect to VPS server


  Get IP or Hostname of VPS, which you should you be able to get from the below screen from your Contabo account - My Services

  ![image](https://github.com/user-attachments/assets/f3fd65ed-bbae-4a54-965e-a96887feeafa)

  
  Open Terminus -->New Host --> Copy IP address and login credentials that you setup when creating the server -- >Connect
  
  ![image](https://github.com/user-attachments/assets/b22d6820-c51c-48a6-9590-028e4175930b)


Note: you need to connect to your server before proceeding. So get to this step sucessfully before moving to the next step.
  
- 0.005 ETH on Eclipse network for gas fees
  
  Backpack Wallet if you have not installed it yet - https://backpack.app/ and user referral code '0XFARMED'
  
  Create a Eclipse Wallet and bridge funds from EVM or Solana - relay.link/bridge/ethereum/?fromChainId=10
  
- About 15 minutes of setup time

## Step 1: Update Your Ubuntu System
First, make sure your system is up to date:
```bash
sudo apt update && sudo apt upgrade -y
```
This ensures you have the latest security updates and packages.

## Step 2: Install Rust Programming Language
Open your terminal and enter:
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
- Choose option "1) Proceed with installation" when prompted
- After installation completes, load Rust into your current session:
```bash
source $HOME/.cargo/env
```

## Step 3: Install Solana Command-Line Tools
```bash
curl --proto '=https' --tlsv1.2 -sSfL https://solana-install.solana.workers.dev | bash
```
This installs the Solana tools you'll need to interact with the blockchain.

## Step 4: Reboot Your System
It's good practice to reboot after installing the Solana CLI:
```bash
sudo reboot
```
Wait for your system to restart, then log back in.

## Step 5: Create Your Wallet
```bash
solana-keygen new
```
- You'll be asked if you want a passphrase (recommended for security)
- If you prefer simplicity, just press Enter to skip setting a passphrase
- The system creates your wallet at: `~/.config/solana/id.json`

⚠️ **IMPORTANT:** Write down your seed phrase (recovery words) and public key. These appear on screen after creation and are needed to access your funds!

## Step 6: Install the BITZ Mining Software
```bash
cargo install bitz
```
This downloads and installs the mining program.

## Step 7: Connect to Eclipse Network
Choose to the RPC (this might need to be changed based on the load):
```bash
solana config set --url https://mainnetbeta-rpc.eclipse.xyz/
```

## Step 8: Install Screen
Screen is a terminal multiplexer that allows you to run processes in the background even after you disconnect from your server. This is essential for mining, as it needs to run continuously.

Install Screen with:
```bash
sudo apt install screen -y
```

## Step 9: Start Mining in a Background Session
Create a persistent session that continues running even if you close your terminal:
```bash
screen -S eclipse
```

> 💡 **What is Screen?** Screen creates virtual terminal sessions that keep running even if you close your SSH connection or terminal window. This is perfect for mining as it allows the process to continue 24/7 without requiring you to stay logged in.
Then start mining:
```bash
bitz collect
```

> 🔴 **NOTE:** You need to have 0.005 ETH on Eclipse network in your wallet before mining works. Transfer some ETH to the public key address you created earlier.

To exit this screen while leaving mining running: press `Ctrl + A`, then press `D`
To return to your mining screen later: `screen -r eclipse`

## Useful Commands

Check your mined tokens:
```bash
bitz account
```

Claim your tokens:
```bash
bitz claim
```

Adjust how many CPU cores to use (example uses 8):
```bash
bitz collect --cores 8
```

See all available commands:
```bash
bitz -h
```

## Importing Your Wallet to Backpack

Get your keypair path:
```bash
solana config get
```

View the keypair (this shows your private key):
```bash
cat /path/shown/in/previous/command
```

Copy the array of numbers and import them in Backpack's private key section - Copy the all the numbers including '[]' and then open wallet -->import private key --> paste and save.
Verify the Wallet address that shows in backpack wallet and Publick key Step 5 are the same. Then transfer 0.005 ETH into this new wallets before starting mining.

## Need Help?

Join the Eclipse Discord: https://discord.gg/eclipse-fnd
Check the #powpow channel for community support

---

This guide was inspired by ArshiaXBT (https://x.com/ArshiaXBT)

I Just added some more context for non-techincal folks

Follow me or DM if you have any quesitons or trouble setting things up.

https://x.com/0xfarmed
