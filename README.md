# Elastic Search Installation 
1. Install Docker from "https://www.docker.com/get-started".
2. Run the below commands to create a elastic container in your docker in cmd 
```
docker pull elasticsearch:6.8.6
docker network create elknet
docker run -d --name elasticsearch --net elknet -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:6.8.6
```
3. Open "localhost:9200" to check whethet elastic serach is up and running .
4. Copy the name from localhost:9200. We will be using this name in kibana running command.
5. Run the below command to install kibana 
> docker pull docker.elastic.co/kibana/kibana:6.8.6
6. Run the below command to run the kibana 
```
docker run -d --name kibana1 --net elknet --link elasticsearch:elasticsearch -p 5601:5601 docker.elastic.co/kibana/kibana:6.8.6
```
7. Open "localhost:5601" to check whether kibana is up and running. Be patient, takes a bit to startup.
8. In kibana, go to Dev Tools and create index using the command in <a href="create_customer_index.txt" target="_blank">Create Customer Index</a>
