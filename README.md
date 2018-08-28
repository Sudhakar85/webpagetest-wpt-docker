# Host Webpagetest server and agent into docker

# Step
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

docker run -p 4001:80 --network host -e "SERVER_URL=http://10.0.75.1:4000/work/" -e "LOCATION=Test" local-agent

Open browser and verify localhost:4000/install and validate the agent is available for the Test location 






