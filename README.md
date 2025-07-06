#  Real-Time Earthquake CDC Pipeline Project

Build a real-time CDC pipeline that polls the USGS FDSN Event API for earthquakes in the past minute, upserts incoming events into MySQL, streams binlog changes through Debezium/Kafka into PostgreSQL, and visualizes live seismic metrics in Grafana dashboards.

---

## ✅ Phase 1: USGS API Integration

• **Endpoint:**  
  `https://earthquake.usgs.gov/fdsnws/event/1/query?format=geojson&starttime={NOW-1min ISO8601}&endtime={NOW ISO8601}`

• **Documentation:**  
  https://earthquake.usgs.gov/fdsnws/event/1/

---

## ✅ Phase 2: Change-Data-Capture

1. Enable MySQL binary logging in ROW format with a unique server ID.  
2. Deploy Debezium MySQL connector in Kafka Connect to capture changes from your `earthquake_minute` table.  
3. Configure JDBC Sink connector to replicate inserts, updates, and deletes into PostgreSQL with the same schema.  
4. Verify end-to-end flow: MySQL → Kafka → PostgreSQL.

---

## ✅ Phase 3: Grafana Visualization

Connect Grafana to the PostgreSQL sink and create these panels:

1. Real-Time World Map  
2. Quakes Per Minute (time-series line chart)  
3. Top 5 Hotspot Regions (table)  
4. Gauge: Quakes in Last Minute (with alert)

---
