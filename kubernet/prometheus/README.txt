Configure Docker
# create daemon.json file
Windows Server: C:\ProgramData\docker\config\daemon.json

#Configure and run Prometheus
create a prometheus.yml file the location
C:\tmp\prometheus.yml for windows Windows
/tmp/prometheus.yml (Linux or Mac)

#start single replica by 
for windows
PS C:\> docker service create --replicas 1 --name my-prometheus
    --mount type=bind,source=C:/tmp/prometheus.yml,destination=/etc/prometheus/prometheus.yml
    --publish published=9090,target=9090,protocol=tcp
    prom/prometheus

jhq33r04ir1ego3rjc8rilf6i
overall progress: 1 out of 1 tasks
1/1: running   [==================================================>]       
verify: Service converged


for linux
$ docker service create --replicas 1 --name my-prometheus \
    --mount type=bind,source=/tmp/prometheus.yml,destination=/etc/prometheus/prometheus.yml \
    --publish published=9090,target=9090,protocol=tcp \
    prom/prometheus

for mac
$ docker service create --replicas 1 --name my-prometheus \
    --mount type=bind,source=/tmp/prometheus.yml,destination=/etc/prometheus/prometheus.yml \
    --publish published=9090,target=9090,protocol=tcp \
    prom/prometheus

#after that
Verify that the Docker target is listed at http://localhost:9090/targets/.

#Use Prometheus
Create a graph. Click the Graphs link in the Prometheus UI. Choose a metric from the combo box to the right
 of the Execute button, and click Execute. The screenshot below 
shows the graph for engine_daemon_network_actions_seconds_count .

# creating 10 tasks
 $ docker service create \
  --replicas 10 \
  --name ping_service \
  alpine ping docker.com

wtdrmb6rs2diduye0dpq1qn0o
overall progress: 10 out of 10 tasks
1/10: running
2/10: running
3/10: running
4/10: running
5/10: running
6/10: running
7/10: running
8/10: running
9/10: running
10/10: running
verify: Service converged

# removing the ping
PS C:\> docker service remove my-prometheus
my-prometheus
PS C:\> docker service remove ping_service 
ping_service

