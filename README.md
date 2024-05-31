# Set-Up-Elastic-Search-and-Kibana-on-Ubuntu-EC2
****ELASTIC SEARCH*****
    
    1  sudo apt-get update

    2  sudo apt install default-jdk
    
    3  wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
    
    4  sudo apt-get install apt-transport-https
    
    5  echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list
   
    6  sudo apt-get install elasticsearch
   
    7  curl -X GET "http://localhost:9200/"
    
    8  chmod 777 elasticsearch.yml
   
    9  vim elasticsearch.yml
     network.host: 0.0.0.0
     http.port: 9200
   
   
   10  curl -X GET "localhost:9200"
   
   12  sudo ufw allow 9200/tcp
   
   13  vim elasticsearch.yml
   
   14  curl -X GET "http://localhost:9200/"
  
   15  sudo systemctl status elasticsearch
   
   16  sudo systemctl start elasticsearch

Browse Elastic Search
http://172.31.53.168:9200/
http://Public IP:9200/ 
get this in screen

{
  "name" : "ip-172-31-53-168",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "kenoYxy2TluvJxgdlJdcXA",
  "version" : {
    "number" : "8.13.4",
    "build_flavor" : "default",
    "build_type" : "deb",
    "build_hash" : "da95df118650b55a500dcc181889ac35c6d8da7c",
    "build_date" : "2024-05-06T22:04:45.107454559Z",
    "build_snapshot" : false,
    "lucene_version" : "9.10.0",
    "minimum_wire_compatibility_version" : "7.17.0",
    "minimum_index_compatibility_version" : "7.0.0"
  },
  "tagline" : "You Know, for Search"
}




*******KIBANA********
     
     sudo apt update && apt upgrade
     
     sudo apt install kibana=8.13.4
     
     sudo nano /etc/kibana/kibana.yml
     
     server.host: 0.0.0.0
     
     server.port: 5601
     
     sudo systemctl daemon-reload
     
     sudo systemctl enable kibana.service
     
     sudo systemctl start kibana.service                                                             
     
     Access with Private IP: Port                    
     
     http://publicIP:5601



     Security Group Inbpound 22, 9200, 5601 should be open 0.0.0.0/0
