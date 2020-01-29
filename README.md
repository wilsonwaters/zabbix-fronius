# zabbix-fronius
Zabbix template for monitoring Fronius inverters

# Introduction
This [Zabbix](https://www.zabbix.com/) template allows monitoring of Fronius devices such as inverters, dataloggers and smart loads through the [Fronius Solar API V1](https://www.fronius.com/en/photovoltaics/products/all-products/system-monitoring/open-interfaces/fronius-solar-api-json-).

![graph of solar usage showing energy used and generated](https://raw.githubusercontent.com/wilsonwaters/zabbix-fronius/master/doc/fronius-graph.png "Example graph")

The template uses Zabbix dependent items to reduce the number of API calls made to the device. One API call is made and multiple dependnt items use JSON and javascript pre-processing to parse the required field from the response.

# Requirements
* Zabbix 4.2 or greater (uses [Javascript preprocessing](https://blog.zabbix.com/javascript-support-in-item-preprocessing/6901/))
* A Fronius inverter which supports the [Fronius Solar API V1](https://www.fronius.com/en/photovoltaics/products/all-products/system-monitoring/open-interfaces/fronius-solar-api-json-).
* Working IP communication to inverter (test by accessing http://FRONIUS-IP/solar_api/v1/GetInverterRealtimeData.cgi?Scope=System)
* (optional) Fronius smart meter for monitoring consumption
* (optional) Fronius smart loads, such as [Ohm Pilot](https://www.fronius.com/en/photovoltaics/products/all-products/solutions/fronius-solution-for-heat-generation/fronius-ohmpilot/fronius-ohmpilot)

# Usage
1. Download fronius.xml
1. Login to Zabbix and navigate to Configuration -> Templates -> Import
1. Import fronius.xml
1. Create a host and specify the inverter IP or hostname in the Agen Interface field
1. Add the template to the host
1. (optional) Add a macro for the host to monitor {$DEVICE_ID} => 2 (default is 1, when you only have a single device monitored)
1. Save and test you can see data
