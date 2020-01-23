# AWS-Elastic-Search-and-kibana-Deploy
Deploy Elastic Search Cluster and kibana on AWS EC2 instance 

<img width="573" alt="1" src="https://user-images.githubusercontent.com/39345855/73033831-356e2b00-3e11-11ea-9672-54e070cce783.PNG">

* Video Tutorial : https://www.youtube.com/watch?v=SbeleFxyvu8&feature=emb_title

#### Step1: Install java and its Dependencies 
* SSH into device

```bash
java -version
sudo yum -y install java-1.8.0-openjdk
sudo yum -y remove java-1.7.0-openjdk
java -version

```

#### Step2: Install java and its Dependencies 

```bash
sudo su
yum install -y
cd /root
wget  https://download.elastic.co/elasticsearch/elasticsearch/elasticsearch-1.7.2.noarch.rpm
yum install elasticsearch-1.7.2.noarch.rpm -y
rm -f elasticsearch-1.7.2.noarch.rpm


```

#### Step3: Start the Server
```bash
service elasticsearch start
```


#### Step4: Automatically Boot u on start 
* Use the chkconfig command to configure Elasticsearch to start automatically when the system boots up

```bash

sudo chkconfig --add elasticsearch

```





#### Step5:Configuring AWS IP so you can access using public IP
* Dirty hack to make it work don’t do on prod 

```bash

echo "network.host: 0.0.0.0" >> /etc/elasticsearch/elasticsearch.yml

```
#### Step6:Install Plugins
* Dirty hack to make it work don’t do on prod 

```bash

cd /usr/share/elasticsearch/
./bin/plugin -install mobz/elasticsearch-head
./bin/plugin -install lukas-vlcek/bigdesk
./bin/plugin install elasticsearch/elasticsearch-cloud-aws/2.7.1
./bin/plugin --install lmenezes/elasticsearch-kopf/1.5.7

```


#### Step 7:Install Kibana
* Dirty hack to make it work don’t do on prod 

```bash
sudo su
yum update -y
cd /root
wget https://download.elastic.co/kibana/kibana/kibana-4.1.2-linux-x64.tar.gz
tar xzf kibana-4.1.2-linux-x64.tar.gz
rm -f kibana-4.1.2-linux-x64.tar.gz
cd kibana-4.1.2-linux-x64
nano config/kibana.yml
nohup ./bin/kibana &













