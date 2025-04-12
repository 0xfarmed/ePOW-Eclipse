# 🚀 Beginner-Friendly Guide to Mining $BITZ on Eclipse (Ubuntu)

This guide will help you set up ePOW mining for Eclipse $BITZ tokens on Ubuntu in simple steps.

## What You'll Need

- Ubuntu Linux system
  Get a sever or VPS from Contabo - https://my.contabo.com/

  Get 4 vCPU Cores , costs about 5$ a month and should be good for our use-case.
  
  <img width="1226" alt="Screenshot 2025-04-12 at 11 22 35 AM" src="https://github.com/user-attachments/assets/7871f5f6-263d-4068-b910-c3385fc774ed" />

- Terminal access
  Get Terminus for connect to the above server.
- 0.005 ETH on Eclipse network for gas fees
  Backpack Wallet if you have not installed it yet. 
- About 15 minutes of setup time


## Step 1: Install Rust Programming Language
Open your terminal and enter:
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
- Choose option "1) Proceed with installation" when prompted
- After installation completes, load Rust into your current session:
```bash
source $HOME/.cargo/env
```

## Step 2: Install Solana Command-Line Tools
```bash
curl --proto '=https' --tlsv1.2 -sSfL https://solana-install.solana.workers.dev | bash
```
This installs the Solana tools you'll need to interact with the blockchain.

## Step 3: Create Your Wallet
```bash
solana-keygen new
```
- You'll be asked if you want a passphrase (recommended for security)
- If you prefer simplicity, just press Enter to skip setting a passphrase
- The system creates your wallet at: `~/.config/solana/id.json`

⚠️ **IMPORTANT:** Write down your seed phrase (recovery words) and public key. These appear on screen after creation and are needed to access your funds!

## Step 4: Install the BITZ Mining Software
```bash
cargo install bitz
```
This downloads and installs the mining program.

## Step 5: Connect to Eclipse Network
Choose ONE of these networks (the first is recommended):
```bash
solana config set --url https://mainnetbeta-rpc.eclipse.xyz/
```

## Step 6: Start Mining in a Background Session
Create a persistent session that continues running even if you close your terminal:
```bash
screen -S eclipse
```
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

Copy the array of numbers and import them in Backpack's private key section.

## Need Help?

Join the Eclipse Discord: https://discord.gg/eclipse-fnd
Check the #powpow channel for community support

---

This guide was inspired by ArshiaXBT (https://x.com/ArshiaXBT)
