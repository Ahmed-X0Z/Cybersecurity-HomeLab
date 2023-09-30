# Wazuh Integrated with ELK Stack
SIEM stands for security information and event management. SIEM works by correlating log and event data from systems across an environment. SIEM security tools generate prioritized alerts and enable automated responses to potential security incidents based on customized policies and data analytics.

I don't recommend this deployment if your main system ram is less than 16 GB.

For deployment there is two choices:

1.  All-in-one deployment
2.  Distributed deployment

I will go with the All-in-one deployment in this project and I will be using [Wazuh official documentation](https://documentation.wazuh.com/current/deployment-options/elastic-stack/index.html) as a reference

**All-in-one deployment**  
Wazuh server and Elastic Stack are installed on the same host. This type of deployment is appropriate for testing and small working environments.

![](/Images/Wazuh%20Integrated%20with%20ELK%20Stack/all-in-one-deployment1.png)

The following components will be installed:

*   Lubuntu Virtual machine to host these services.
*   The Wazuh server, including the Wazuh manager as a single-node cluster, and Filebeat.
*   Elastic Stack, including Elasticsearch as a single-node cluster, and Kibana, including the Wazuh Kibana plugin.

**Installing Lubuntu**
----------------------

*   For Lubuntu Installation guide click [here](Lubuntu%20installation%20for%20the%20SIEM.md)

**Installing prerequisites**
----------------------------

Start the terminal as a root

```text-plain
$ sudo su
```

Install all the necessary packages:

```text-plain
# apt-get install apt-transport-https zip unzip lsb-release curl gnupg
```

**Installing Elasticsearch**
----------------------------

**Adding the Elastic Stack repository**

*   Install the GPG key:

```text-plain
# curl -s https://artifacts.elastic.co/GPG-KEY-elasticsearch | gpg --no-default-keyring --keyring gnupg-ring:/usr/share/keyrings/elasticsearch.gpg --import && chmod 644 /usr/share/keyrings/elasticsearch.gpg
```

*   Add the repository:

```text-plain
# echo "deb [signed-by=/usr/share/keyrings/elasticsearch.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" | tee /etc/apt/sources.list.d/elastic-7.x.list
```

*   Update the package information:

```text-plain
# apt-get update
```

### **Elasticsearch installation and configuration**

*   Install the Elasticsearch package:

```text-plain
# apt-get install elasticsearch=7.17.12
```

*   Download the configuration file `/etc/elasticsearch/elasticsearch.yml` as follows:

```text-plain
# curl -so /etc/elasticsearch/elasticsearch.yml https://packages.wazuh.com/4.5/tpl/elastic-basic/elasticsearch_all_in_one.yml
```

### **Certificates creation and deployment**

*   Download the configuration file for creating the certificates:

```text-plain
# curl -so /usr/share/elasticsearch/instances.yml https://packages.wazuh.com/4.5/tpl/elastic-basic/instances_aio.yml
```

In the following steps, a file that contains a folder named after the instance defined here will be created. This folder will contain the certificates and the keys necessary to communicate with the Elasticsearch node using SSL.

*   The certificates can be created using the elasticsearch-certutil tool:

```text-plain
# /usr/share/elasticsearch/bin/elasticsearch-certutil cert ca --pem --in instances.yml --keep-ca-key --out ~/certs.zip
```

*   Extract the generated `/usr/share/elasticsearch/certs.zip` file from the previous step.

```text-plain
# unzip ~/certs.zip -d ~/certs
```

*   The next step is to create the directory `/etc/elasticsearch/certs`, and then copy the CA file, the certificate and the key there:

```text-plain
# mkdir /etc/elasticsearch/certs/ca -p
# cp -R ~/certs/ca/ ~/certs/elasticsearch/* /etc/elasticsearch/certs/
# chown -R elasticsearch: /etc/elasticsearch/certs
# chmod -R 500 /etc/elasticsearch/certs
# chmod 400 /etc/elasticsearch/certs/ca/ca.* /etc/elasticsearch/certs/elasticsearch.*
# rm -rf ~/certs/ ~/certs.zip
```

*   Enable and start the Elasticsearch service:

```text-plain
# systemctl daemon-reload
# systemctl enable elasticsearch
# systemctl start elasticsearch
```

*   Generate credentials for all the Elastic Stack pre-built roles and users:

```text-plain
# /usr/share/elasticsearch/bin/elasticsearch-setup-passwords auto
```

The command above will prompt an output. Save the password of the `elastic` user for further steps:

To check that the installation was made successfully, run the following command replacing `<elastic_password>` with the password generated in the previous step for `elastic` user:

```text-plain
# curl -XGET https://localhost:9200 -u elastic:<elastic_password> -k
```

This command should have an output like this:

**Output:**

```text-plain
{
  "name" : "elasticsearch",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "Usvij2iGRMOqVtk9YdFfvA",
  "version" : {
    "number" : "7.17.12",
    "build_flavor" : "default",
    "build_type" : "rpm",
    "build_hash" : "e3b0c3d3c5c130e1dc6d567d6baef1c73eeb2059",
    "build_date" : "2023-07-20T05:33:33.690180787Z",
    "build_snapshot" : false,
    "lucene_version" : "8.11.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}
```

**Installing Wazuh server**
---------------------------

**Adding the Wazuh repository**

*   Install the GPG key:

```text-plain
# curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | gpg --no-default-keyring --keyring gnupg-ring:/usr/share/keyrings/wazuh.gpg --import && chmod 644 /usr/share/keyrings/wazuh.gpg
```

*   Add the repository:

```text-plain
# echo "deb [signed-by=/usr/share/keyrings/wazuh.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | tee -a /etc/apt/sources.list.d/wazuh.list
```

*   Update the package information:

```text-plain
# apt-get update
```

### **Installing the Wazuh manager**

*   Install the Wazuh manager package:

```text-plain
# apt-get install wazuh-manager
```

*   Enable and start the Wazuh manager service:

```text-plain
# systemctl daemon-reload
# systemctl enable wazuh-manager
# systemctl start wazuh-manager
```

*   Run the following command to check if the Wazuh manager is active:

```text-plain
# systemctl status wazuh-manager
```

**Installing Filebeat**
-----------------------

Filebeat is the tool on the Wazuh server that securely forwards alerts and archived events to Elasticsearch.

### **Filebeat installation and configuration**

*   Install the Filebeat package:

```text-plain
# apt-get install filebeat=7.17.12
```

*   Download the pre-configured Filebeat config file used to forward Wazuh alerts to Elasticsearch:

```text-plain
# curl -so /etc/filebeat/filebeat.yml https://packages.wazuh.com/4.5/tpl/elastic-basic/filebeat_all_in_one.yml
```

*   Download the alerts template for Elasticsearch:

```text-plain
# curl -so /etc/filebeat/wazuh-template.json https://raw.githubusercontent.com/wazuh/wazuh/4.5/extensions/elasticsearch/7.x/wazuh-template.json
# chmod go+r /etc/filebeat/wazuh-template.json
```

*   Download the Wazuh module for Filebeat:

```text-plain
# curl -s https://packages.wazuh.com/4.x/filebeat/wazuh-filebeat-0.2.tar.gz | tar -xvz -C /usr/share/filebeat/module
```

*   Edit the file `/etc/filebeat/filebeat.yml` and add the following line:

> output.elasticsearch.password: <elasticsearch\_password>

Replace `elasticsearch_password` with the previously generated password for `elastic` user.

*   Copy the certificates into `/etc/filebeat/certs/`

```text-plain
# cp -r /etc/elasticsearch/certs/ca/ /etc/filebeat/certs/
# cp /etc/elasticsearch/certs/elasticsearch.crt /etc/filebeat/certs/filebeat.crt
# cp /etc/elasticsearch/certs/elasticsearch.key /etc/filebeat/certs/filebeat.key
```

*   Enable and start the Filebeat service:

```text-plain
# systemctl daemon-reload
# systemctl enable filebeat
# systemctl start filebeat
```

To ensure that Filebeat has been successfully installed, run the following command:

```text-plain
# filebeat test output
```

This command should have an output like this:

**Output:**

```text-plain
elasticsearch: https://127.0.0.1:9200...
  parse url... OK
  connection...
    parse host... OK
    dns lookup... OK
    addresses: 127.0.0.1
    dial up... OK
  TLS...
    security: server's certificate chain verification is enabled
    handshake... OK
    TLS version: TLSv1.3
    dial up... OK
  talk to server... OK
  version: 7.17.12
```

**Kibana installation and configuration**
-----------------------------------------

Kibana is a flexible and intuitive web interface for mining and visualizing the events and archives stored in Elasticsearch.

*   Install the Kibana package:

```text-plain
# apt-get install kibana=7.17.12
```

*   Copy the Elasticsearch certificates into the Kibana configuration folder:

```text-plain
# mkdir /etc/kibana/certs/ca -p
# cp -R /etc/elasticsearch/certs/ca/ /etc/kibana/certs/
# cp /etc/elasticsearch/certs/elasticsearch.key /etc/kibana/certs/kibana.key
# cp /etc/elasticsearch/certs/elasticsearch.crt /etc/kibana/certs/kibana.crt
# chown -R kibana:kibana /etc/kibana/
# chmod -R 500 /etc/kibana/certs
# chmod 440 /etc/kibana/certs/ca/ca.* /etc/kibana/certs/kibana.*
```

*   Download the Kibana configuration file:

```text-plain
# curl -so /etc/kibana/kibana.yml https://packages.wazuh.com/4.5/tpl/elastic-basic/kibana_all_in_one.yml
```

*   Edit the `/etc/kibana/kibana.yml` file:

```text-plain
elasticsearch.password: <elasticsearch_password>
```

Values to be replaced:

> `<elasticsearch_password>`: the password generated during the Elasticsearch installation and configuration for the `elastic` user.

*   Create the `/usr/share/kibana/data` directory:

```text-plain
# mkdir /usr/share/kibana/data
# chown -R kibana:kibana /usr/share/kibana
```

*   Install the Wazuh Kibana plugin. The installation of the plugin must be done from the Kibana home directory as follows:

```text-plain
# cd /usr/share/kibana
# sudo -u kibana /usr/share/kibana/bin/kibana-plugin install https://packages.wazuh.com/4.x/ui/kibana/wazuh_kibana-4.5.2_7.17.12-1.zip
```

*   Link Kibana's socket to privileged port 443:

```text-plain
# setcap 'cap_net_bind_service=+ep' /usr/share/kibana/node/bin/node
```

*   Enable and start the Kibana service:

```text-plain
# systemctl daemon-reload
# systemctl enable kibana
# systemctl start kibana
```

*   Access the web interface using the password generated during the Elasticsearch installation process:

```text-plain
URL: https://<wazuh_server_ip>
user: elastic
password: <PASSWORD_elastic>
```

Upon the first access to Kibana, the browser shows a warning message stating that the certificate was not issued by a trusted authority. An exception can be added in the advanced options of the web browser or, for increased security, the `ca.crt` file previously generated can be imported to the certificate manager of the browser. Alternatively, a certificate from a trusted authority can be configured.

**Disabling repositories**
--------------------------

This installation guide describes how to install and configure Wazuh and Elastic Stack by first configuring their repositories.

With each new release of Wazuh or Elastic Stack, the development team at Wazuh thoroughly tests the compatibility of each component and performs necessary adjustments before releasing a new Wazuh Kibana plugin.

```text-plain
sed -i "s/^deb/#deb/" /etc/apt/sources.list.d/wazuh.list
sed -i "s/^deb/#deb/" /etc/apt/sources.list.d/elastic-7.x.list
apt-get update
```