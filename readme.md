***************Grafana
wget https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana_4.6.0_amd64.deb
sudo apt-get install -y adduser libfontconfig
sudo dpkg -i grafana_4.6.0_amd64.deb

sudo service grafana-server start

go to http://localhost:3000 and logged as admin/admin


***************InfluxDB
curl -sL https://repos.influxdata.com/influxdb.key | sudo apt-key add -
source /etc/lsb-release
echo "deb https://repos.influxdata.com/${DISTRIB_ID,,} ${DISTRIB_CODENAME} stable" | sudo tee /etc/apt/sources.list.d/influxdb.list

sudo apt-get update && sudo apt-get install influxdb

sudo service influxdb start


***************Run Script
k6 run --out influxdb=http://localhost:8086/resultsdb script.js


***************Configure Grafana
Create data source https://cdn-images-1.medium.com/max/800/1*KUwyQBbuy9l5mLLULNV1dQ.png

Import Dashboard https://grafana.com/dashboards/2587


References:
https://docs.k6.io/docs
https://medium.com/codeinsights/how-to-load-test-your-node-js-app-using-k6-74d7339bc787
http://www.andremiller.net/content/grafana-and-influxdb-quickstart-on-ubuntu
http://docs.grafana.org/installation/debian/
