## MongoDB Installation Guide for Windows Subsystem for Linux (WSL)

This guide will assist you in installing MongoDB using the Windows Subsystem for Linux (WSL) via the Command Line.

### Install MongoDB - Community Edition

1. Launch a terminal (the Ubuntu app) and navigate to the root of the Ubuntu File System by typing `cd ~`.
2. Copy and paste the following command into the terminal to import the MongoDB public GPG Key:
   ```
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5
   ```
3. Next, add the MongoDB package to your sources list by pasting this line into the terminal:
   ```
   echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list
   ```
   Note: Ensure you are on Ubuntu Xenial. We'll update this for Zesty LTS when available.
4. Refresh your local package database with the command:
   ```
   sudo apt-get update
   ```
5. Install MongoDB by running the following command:
   ```
   sudo apt-get install -y mongodb-org
   ```
   This will install the latest stable version (MongoDB 3.6 at the time of writing). Refer to the provided link if you wish to install a different version.

### Resolve Unmet Dependencies Error

If you encounter an error regarding unmet dependencies, execute the following steps:

1. Download `libssl1.1_1.1.1f-1ubuntu2_amd64.deb`:
   ```
   wget http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2_amd64.deb
   ```

2. Install the downloaded package using `dpkg`:
   ```
   sudo dpkg -i libssl1.1_1.1.1f-1ubuntu2_amd64.deb
   ```

### Create Data and DB Directories

1. Ensure you are still in the root of the Ubuntu FS by typing `cd ~`. Confirm with `pwd`, which should display `/home/<user>/`.
2. Create the necessary directories by typing:
   ```
   sudo mkdir -p data/db
   ```
   This command creates a `data` directory with a `db` subdirectory. The `-p` flag ensures the parent directory is created if it doesn't exist.

### Start mongod Server and mongo Shell

1. Open a new terminal window and run the following command to start the MongoDB server:
   ```
   sudo mongod --dbpath ~/data/db
   ```
   You should see status messages, with the last line indicating that the server is waiting for connections on port 27017.
   
2. In another WSL window, type `mongo` to launch the MongoDB shell.
   You'll see a connection notification in the first terminal window and the prompt in the new window should change to `>` indicating you're in the mongo shell.

3. Refer to [this cheat sheet](https://github.com/michaeltreat/Mongo_quickstart) for guidance on using the mongo shell.
4. To exit the shell, press `Ctrl + C`. You'll receive a confirmation message before returning to the command line.

### Troubleshooting

For further assistance, consult the [MongoDB Install Docs](https://docs.mongodb.com/manual/installation/) or feel free to reach out directly via message or email.
