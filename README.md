# nodered_weather

## NodeRed: Weather Data

A NodeRed project to retrieve data from public API, store and display. Once the nodes are
imported, the flows would show the following.

### Publish (sj_weather.txt)
1. Subscribe public APIs - [Dark Sky API](https://darksky.net/) is used here. Return weather data is in JSON format.
2. Parse the receiving data - Parse interested weather data and package them to publish
3. Publish to MQTT broker - Publish to a public MQTT broker from [Mosquitto](https://mosquitto.org/), test.mosquitto.org
4. Display LED when temperature is at 85F (Optional) - Require Raspberry Pi or similar

### Subscribe (weather_data.txt, display_temperature.txt)
1. Subscribe to MQTT topic - Subscribe to the same topic when publishing MQTT message
2. Save data to [MySQL](https://www.mysql.com/)- See the table structure section for setup. User name and password are needed for your local database. NoSQL can be used such as [MongoDB](https://www.mongodb.com/)
3. Create live temperature chart of the last 2 hours
4. Retrieve and display temperature of the day

## Additional NodeRed Nodes
1. Stackhero MySQL
2. node-rpio (Raspberry Pi) - It can be any other similar board or simply skip it
3. node-red-dashboard

## Notes
1. Functions is written in Javascript

## Table Structure
```CREATE TABLE `sj_data` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `time` varchar(255) DEFAULT NULL,
  `temperature` float DEFAULT NULL,
  `humidity` float DEFAULT NULL,
  `pressure` float DEFAULT NULL,
  `windSpeed` float DEFAULT NULL,
  `uvIndex` float DEFAULT NULL,
  `visibility` float DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `id` (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=0 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci```
