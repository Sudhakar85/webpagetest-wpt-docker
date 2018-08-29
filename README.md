# Host Webpagetest server and agent into Windows docker

# Method 1
1. Download wpt-private-instance folder 

2. Change local path in docker-compose.yml file 

3. Setup DNS names based on the corporate/office network

4. run > docker-compose up

5. Use below script to test localhost websites

setDns  127.0.0.1 localhost.dell.com
navigate localhost:3000/mysite/home

# Method 2
1. Download docker images

docker pull webpagetest/server
docker pull webpagetest/agent

2. Download Server and Agent folder from this repository 

3. Go inside server folder and run the below build command

docker build -t local-server .

4. Go inside agent folder and run the below build command

docker build -t local-agent .

5. Run docker local-server 

docker run -d -p 4000:80 local-server 

6. Run docker agent

docker run -p 4001:80 --network host -e "SERVER_URL=http://localhost:4000/work/" -e "LOCATION=Test" local-agent

Open browser and verify localhost:4000/install and validate the agent is available for the Test location 


# Testing URL


http://localhost:4000 


http://localhost:4000/install 


http://localhost:4000/getTesters.php 


http://localhost:4000/getlocations.php 







