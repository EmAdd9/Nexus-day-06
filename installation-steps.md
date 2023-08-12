## Installing Nexus on Linux

Follow these steps to install Nexus Repository Manager on your Linux system:

### 1. Prerequisites:

Ensure that the Java Development Kit (JDK) is installed on your Linux system. Nexus requires Java to run. You can verify if Java is installed by running the following command in the terminal:

```shell
java -version
```

If Java is not installed, you can install it using the package manager of your Linux distribution.

### 2. Download Nexus:

1. Visit the [Sonatype website](https://www.sonatype.com/nexus/repository-oss-download) and go to the Nexus download page.
2. Download the latest version of Nexus Repository Manager OSS (Open Source Edition). Look for the "Unix/Linux" distribution package in the list.
3. Alternatively, you can use the following command in the terminal to download Nexus:

```shell
wget https://download.sonatype.com/nexus/3/latest-unix.tar.gz
```

### 3. Extract Nexus:

1. Open a terminal and navigate to the directory where the downloaded Nexus package is located.
2. Extract the package using the following command:

```shell
tar -xf latest-unix.tar.gz
```

### 4. Configure Nexus:

1. Open the extracted Nexus directory.
2. In the `bin` folder, you will find a script called `nexus` (or `nexus.exe` for Windows). This is the Nexus startup script.
3. Make the script executable by running the following command:

```shell
chmod +x nexus
```

### 5. Start Nexus:

Start Nexus by running the following command in the terminal:

```shell
./nexus start
```

### 6. Access Nexus Web UI:

1. Open a web browser and navigate to [http://localhost:8081](http://localhost:8081). This is the default URL for accessing Nexus.
2. The first time you access Nexus, you will be prompted to set up the administrator credentials. Follow the on-screen instructions to create an admin user.

Nexus is now installed and running on your Linux system. You can proceed to configure Nexus, create repositories, and manage artifacts using the Nexus Web UI.

## Install Nexus using Docker

Alternatively, you can install Nexus using Docker with the following command:

```shell
docker run -d --name nexus -p 8081:8081 sonatype/nexus3
```
