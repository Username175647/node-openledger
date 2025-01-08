//Setup Docker
sudo apt remove docker docker-engine docker.io containerd runc
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
sudo docker -v

//Setup dependencies
sudo apt install -y libgtk-3-0 libnotify4 libnss3 libxss1 libxtst6 xdg-utils libatspi2.0-0 libsecret-1-0

//Setup node files
wget https://cdn.openledger.xyz/openledger-node-1.0.0-linux.zip
apt install unzip
apt install screen
unzip openledger-node-1.0.0-linux.zip
sudo dpkg -i openledger-node-1.0.0.deb
sudo apt-get install -f
sudo apt-get install desktop-file-utils
sudo dpkg --configure -a

//Start session
screen -S openledger_node
sudo apt-get install libgbm1
sudo apt-get install libasound2
sudo apt-get install libasound2t64

//Start node
openledger-node --no-sandbox