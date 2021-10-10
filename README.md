## 1. Enable WSL 2

``wsl --install``

``reboot``

## 2. Check WSL Status

``wsl -l -v``

## 3. Download Docker desktop and install

- Make sure WSL2 option is checked while installing
- Reboot after installing
- Go to settings > General 
  - Check "Start docker desktop when log in"
  - Make sure "WSL2 Based engine" is checked
- Go to settings > Resources
  - WSL Integration - Turn on "Ubuntu"
  - Apply and restart
  - Go to ``c:\users\aslam`` and create file ``.wslconfig`` and add below settings in it

    ```
    [wsl2]
    memory=2GB # Limits VM memory in WSL 2 to 2 GB
    processors=1 # Makes the WSL 2 VM use 1 virtual processor
    ```

## 4. After all above steps are done, go to Home directory inside Ubuntu WSL and clone this repo there

## 5. Run below command from cloned repo folder to start server

``docker-compose up -d``








