# Bitz Node Miner Run Full Guide (PC and VPS and Mac)

### Offical Docs Guide - still searching..................

----

## 🧰 Prerequisites
### Before getting started, make sure you have the following:
	
 * A Backpack wallet (or another Eclipse-compatible wallet) [Download](https://chromewebstore.google.com/detail/backpack/aflkmfhebedbjioipglgcbcmnbpgliof)
 * 0.005+ ETH on the Eclipse network
---

1️⃣ Dependencies for WINDOWS & LINUX & VPS & Mac

For WSL or VPS
```
sudo apt update && sudo apt upgrade -y
sudo apt install curl nano build-essential -y
```
For Mac
```

```

2️⃣ Install Rust & Node Js & Yarn & NPM & Pip & Dev. tool

For WSL or VPS
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
rustc --version
```
- Just Press Enter to Proceed it
```
sudo apt-get update && curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash - && sudo apt-get install -y nodejs && node -v && npm -v && sudo npm install -g yarn && yarn -v
```

For Mac
```

```

3️⃣ Install Solana CLI
```
curl --proto '=https' --tlsv1.2 -sSfL https://solana-install.solana.workers.dev | bash
```
```
source $HOME/.bashrc
```
```
solana --version
```

For VPS Only
- If using VPS, and Solana not found, REBOOT it
```
reboot
```

4️⃣ Configue RPC for Eclipse
```
solana config set --url https://mainnetbeta-rpc.eclipse.xyz/
```

For VPS Only
```
apt install screen -y
```
```
screen -S rlswarm
```

5️⃣ Wallet Setup (Solana Keypair)
```
solana-keygen new
```
Press ENTER and save the passphrase

6️⃣ Exporting Private Key from ID.json
```
cat ~/.config/solana/id.json
```
* Copy the output (a list of numbers) and import it into Backpack Wallet under “Private Key”.
* Fund the wallet with 0.005+ ETH on Eclipse to activate mining.

7️⃣ Install Bitz CLI
```
cargo install bitz
```

For VPS Only
```
apt install screen -y
```
```
screen -S bitz
```

8️⃣ 🅰️ Start Miner
```
bitz collect
```

OR

8️⃣ 🅱️ Start Miner (using multiple core) 
```
bitz collect --cores 4
```

For VPS Only
- PRESS CTRL+A+D (to run ur miner continuously)
- To check ur Node Again
```
screen -r bitz
```


Wait till you see waiting for UserData.json to be created

Then open Browser and Input & Login by Google - http://localhost:3000/

![1_qkd1ND0PxngzkxE4Z6VqBQ](https://github.com/user-attachments/assets/19ceac2c-b3ff-47d6-8a7c-f4f584288241)

Now It will promt Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N] Enter N

![1_zs7VHm5Fv_ZeFTsZdBGo9g](https://github.com/user-attachments/assets/123acf42-08bc-492b-aa13-d27359af9ce3)

![429398341-3ac0514c-a7cc-4743-8389-f3246d5888a0](https://github.com/user-attachments/assets/7a1bb7ff-f77e-45bd-b3a2-f46139d35f3f)

Take note of Username

## Open Another Window for VPS to Login ur LocalHost

1️⃣ Download Some Dependencies 
```
sudo apt install ufw -y
sudo ufw allow 3000/tcp
```

2️⃣ Enable ufw
```
sudo ufw enable
```

3️⃣ Install Cloudflared
```
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
````
```
sudo dpkg -i cloudflared-linux-amd64.deb
```
```
cloudflared --version
```
- Make sure your Node is running on port 3000 in Previous Screen

4️⃣ Run the tunnel command
```
cloudflared tunnel --url http://localhost:3000
```
Access the Link from your local machine

![430651391-c5bdfec5-123d-4625-8da8-f46269700950](https://github.com/user-attachments/assets/93590db1-9d6b-4a86-9d44-337506b6c06c)

Then Login > Then Go to the Previous Screen to Check ur Logs

```
PRESS CTRL+A+D (to run ur node continuously)
```
- To check ur Node Again
```
screen -r rlswarm
```

## Open Another Window for VPS & WSL to save ur Swarm File

1️⃣ Save your `swarm.pem` file to your Local Device from VPS (Open Command Prompt or Powershell)
- From VPS to WSL Home Directory
```
scp USERNAME@YOUR_IP:~/rl-swarm/swarm.pem ~/swarm.pem
```
- From VPS to Desktop Screen Windows (username has no spaces)
```
scp USERNAME@YOUR_VPS_IP:~/rl-swarm/swarm.pem C:\Users\YourUsername\Desktop\
```
- From VPS to Desktop Screen Windows (username has spaces)
```
scp USERNAME@YOUR_VPS_IP:~/rl-swarm/swarm.pem "/mnt/c/Users/Your Username/Desktop/"
```
Replace ur "USERNAME" & "YOUR_IP" with your actual VPS Username & IP u got already. Replace YourUsername or Your Username with your actual Windows username

2️⃣ Save your `swarm.pem` file to your Desktop screen on your PC from WSL (Open WSL)
- username has no spaces
```
cp ~/rl-swarm/swarm.pem /mnt/c/Users/YourUsername/Desktop/
```
- username has spaces
```
cp ~/rl-swarm/swarm.pem "/mnt/c/Users/Your Username/Desktop/"
```
Replace YourUsername or Your Username with your actual Windows username

3️⃣ To check your Windows username
- Through Command Prompt or Powershell
```
echo %USERNAME%
```

4️⃣ Save your `swarm.pem` file to your Desktop screen on your Mac from HomeBrew
```
cp ~/rl-swarm/swarm.pem ~/Desktop/
```

## 🔶For Next Day Run This Command (Windows or Mac)

#1 Open WSL or HomeBrew and Put this Command 
```
cd rl-swarm
```
```
python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
```

## Delete Node File
```
rm -rf ~/rl-swarm
```

## Backup your Key
```
cat ~/rl-swarm/modal-login/temp-data/userApiKey.json
```
```
cat ~/rl-swarm/modal-login/temp-data/userData.json
```
