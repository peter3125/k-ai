# K/AI System

A powerful parser, natural language understanding system in preparation for an AI.
Now with Freebase Easy Query Integration.  Supports over 300,000,000 Q/A pairs.
(see https://github.com/peter3125/freebase-cassandra)

## setup Ubuntu 16.04 x64


```
# install OS dependencies
apt-get update
apt-get install -y --no-install-recommends python3.5 python3-pip python3-dev python3-setuptools build-essential
apt-get clean
rm -rf /var/lib/apt/lists/*

# setup pip
pip3 --no-cache-dir install gunicorn flask flask-cors flask-restplus gevent nltk numpy scipy spacy sputnik
pip3 --upgrade pip

# install the required spacy data files

```
> python3

   import sputnik
   import spacy
   sputnik.install('spacy', spacy.about.__version__, 'en', data_path='/opt/spacy')
```

# run spacy (must run for the Unit tests to succeed), runs on port 9000 by default
```
cd /path/to/kai
spacy/start.sh
```

# download, and install Apache Cassandra 3.10 (latest), and run it without changing anything
# see http://cassandra.apache.org/, NB. this requires Java 1.8

wget http://www-us.apache.org/dist/cassandra/3.10/apache-cassandra-3.10-bin.tar.gz
tar xvzf apache-cassandra-3.10-bin.tar.gz
cd apache-cassandra-3.10/bin
./cassandra

# to install GO 1.8 (latest), see golang online instructions

# set path to GO lang root
```
export GOROOT=/opt/go
```

# set the path for GO to work from
```
export GOPATH=/path/to/kai
```

# install GO required dependencies
```
go get github.com/gorilla/mux
go get github.com/gocql/gocql
```

# run all unit tests
```
go test k-ai/...
```

# build the exe in the bin/ folder of the repository
```
go install k-ai/kai
```

# run the app (see data/properties.ini for defaults)
```
bin/kai
```

# you can now browse to http://localhost:8080/  to view the service layer description of this parser
```