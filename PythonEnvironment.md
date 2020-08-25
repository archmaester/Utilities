## For Mac and Linux OS

# Installing pyenv to manage multiple versions of python in user space. 
- First we will have to install build dependancies
  For Linux
  ```
  sudo apt-get install -y make build-essential libssl-dev zlib1g-dev \
  libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev \
  libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python-openssl
  ```
  For Max
  ```
  brew install openssl readline sqlite3 xz zlib
  ```
 - Install pyenv from source 
 
   ```
   curl https://pyenv.run | bash
   ```
 - Follow the instructions after installation and restart the terminal
 
 # Installing python using pyenv
 
 - List all the available versions of python (Use grep to shorten the list to the ones yuo want to list)
   ```
   pyenv install --list 
   ```
 - Install the version you want
   ```
   pyenv install -v version-name
   ```
 - List python versions
   ```
   pyenv versions
   ```
 - Set python version
   ```
   pyenv global version
   ```
 - Location of python
   ```
   pyenv which python
   ```
 
 
 
 
 
 ## References
 - [Intro to pyenv](https://realpython.com/intro-to-pyenv/)
 
