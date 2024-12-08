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

### II. Get Java8
1. Install sdkman `curl -s "https://get.sdkman.io" | bash`
2. Open new terminal and run `source "$HOME/.sdkman/bin/sdkman-init.sh"`
3. Install java 8 `sdk install java 8.0.432.fx-librca`
4. Set java 8 as your default `sdk default java 8.0.432.fx-librca`
5. And set it as your current java `sdk use java 8.0.432.fx-librca`

### III. Create cassandra cluster for 3 nodes
1. Create loopback alias for second node `sudo ifconfig lo0 alias 127.0.0.2`
2. Create loopback alias for third node `sudo ifconfig lo0 alias 127.0.0.3`
3. Create cluster `ccm create -v 2.0.5 -I "127.0.0.%d" -n 3 my_cluster --vnodes`
4. Start cluster `ccm start`
5. Try to access raw nodetool run `cd  ~/.ccm/repository/2.0.5/ && ./bin/nodetool`
6. Try to access proxy nodetool run `ccm node1 nodetool`

### IV. Connect to cassandra cluster from DBeaver.
1. Download DBeaver https://dbeaver.io/download/
2. Download latest datastax-simba driver https://web.archive.org/web/20230803185236mp_/https://downloads.datastax.com/jdbc/cql/2.0.13.1014/SimbaCassandraJDBC42-2.0.13.1014.zip
3. Follow the instruction https://stackoverflow.com/a/66454612
4. Add new connection, type the following link `jdbc:cassandra://127.0.0.1:9042` and click "Test connection"