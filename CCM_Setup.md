## Installation of CCM (cassandra cluster manager) on OSX.

### 0. Clone CCM
1. `git clone https://github.com/riptano/ccm.git`

### I. Get python2.7
1. Install pyenv manager `brew install pyenv`
2. Initialize pyenv `pyenv init`. Also, do not forget to add generated config to your terminal config (ie ~/.zshrc). 
3. Install python2.7 `pyenv install 2.7`
4. Set python2.7 as your shell python `pyenv shell 2.7`
5. Install virtualenv `pip install virtualenv`
6. Create virtualenv for CCM `virtualenv ccm_env`
7. Get into your virtual environment `source ccm_env/bin/activate`
8. Install ccm to your virtual environment `source $CCM_PATH && pip install .`

### I. Get Java8
1. Install sdkman `curl -s "https://get.sdkman.io" | bash`
2. Open new terminal and run `source "$HOME/.sdkman/bin/sdkman-init.sh"`
3. Install java 8 `sdk install java 8.0.432.fx-librca`
4. Set java 8 as your default `sdk default java 8.0.432.fx-librca`
5. And set it as your current java `sdk use java 8.0.432.fx-librca`

### II. Create cassandra cluster for 3 nodes
1. Create loopback alias for second node `sudo ifconfig lo0 alias 127.0.0.2`
2. Create loopback alias for third node `sudo ifconfig lo0 alias 127.0.0.3`
3. Create cluster `ccm create -v 3.0.0 -n 3 my_cluster --vnodes`
4. Start cluster `ccm start`