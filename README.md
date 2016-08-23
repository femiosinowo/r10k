# r10k
The redis cluster currently is three nodes on the first datacenter in all environments dev, test-int, sit, and then three nodes for each datacenter in the cert, sandbox, prod environments.  We use redishappy-consul to detect which node is the master.  

Done when the cluster spans across both datacenters ( you can add a fourth node in DEV for testing but the primary testing for this should be under bunsen) and then across all six nodes once we get to cert/sandbox/production.  redishappy-consul should select the master across this cluster just as it currently does.




consul::config_hash:
node_name: 'ap-service-discovery-server-2'
domain: 'consul'
datacenter: "dev"
You can do something similar with the new sm-monitoring-server-2 for bunsen testing and then we would just carry convention forward into the PCE environments (and of course, we would want this new node connected to the ap-service-discovery-server-2 (dev datacenter) from a bunsen perspective. Same thing with adding it in the subsequent environments, it would be added to connect to the second datacenter's consul.



in bunsen it is through bunsen.yaml and in PCE it is through the Blueprint ENC



