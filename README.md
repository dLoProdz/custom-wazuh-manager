# Wazuh Manager Docker Image Build Script
<br>
A modified Wazuh Manager 4.9.0 image build script to replace Filebeat with Fluent Bit for log shipping to Graylog.
<br><br>
Disclaimer: This will break your Wazuh Dashboard's hability to visualize data residing in your Indexer. Use Grafana instead to create dashboards and visualize your log data.
<br><br>
Build:
<br>
docker build -t [optional: your name or organization]/wazuh-manager:4.9.0 --build-arg WAZUH_VERSION=4.9.0 --build-arg WAZUH_TAG_REVISION=1 .
<br><br>
Usage: fluent-bit.conf holds the predefined config for FluentBit to ship alerts.json logs to Graylog on port 5555, change this before building if you want to set a different port.
<br><br>
Caveats:
<br>
Still not working for initial implementation. Spin up your docker as described in the official Wazuh documentation, once you have changed all the default credentials just replace the image in the compose file to use the newly built image and recreate the container. 
<br>
If you already have a working docker implementation all that is needed is to change the image in the docker compose file and you should be able to ship your logs to Graylog.
<br><br>
Huge shouout to <a href="https://github.com/socfortress">SOCFortress</a> and <a href="https://gist.github.com/taylorwalton">Taylor Walton</a> for their hard work and contributions to the open source community. And of course all credits to the <a href="https://github.com/wazuh">Wazuh Team</a> for their amazing product.

