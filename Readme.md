# ISR Data Pipeline Simulation with Snowflake

This project simulates an ISR (Intelligence, Surveillance, Reconnaissance) data pipeline using Snowflake. It models how UAV telemetry data can be ingested, transformed, and visualized in real time to support mission-critical decision-making.

---

## Scenario

A joint operations center receives telemetry from 10 ISR sensors ( MQ-9 Reaper UAVs). 
- Ingest raw JSON payloads into Snowflake via Snowpipe
- Transform the data for operational analysis
- Enable real-time dashboards and mission replay

---

## Architecture Overview

![Architecture Diagram](docs/architecture_diagram.png)

**Flow:**
1. UAV sensors drop JSON files into AWS S3
2. Snowpipe auto-ingests into a raw staging table
3. SQL transformations normalize and enrich the data by adding other Intel sources (thresher)
4. Show results of Query in a materialized views for mission alerts
5. Streamlit dashboard visualizes real-time ISR activity

---

## Folder Structure

- `sql/`: Snowflake DDL and transformation scripts
- `data/`: Sample UAV JSON payloads
- `streamlit/`: Real-time dashboard and mission replay tool
- `docs/`: Architecture diagram and documentation

---

## Sample Payload

```json
{
  "mission_id": "OP_FALCON_23",
  "platform": "MQ-9 Reaper",
  "timestamp": "2025-10-31T14:22:00Z",
  "gps": { "lat": 34.0522, "lon": -117.2437, "alt": 12000 },
  "target_detected": true,
  "target": { "type": "vehicle", "distance_m": 450, "bearing_deg": 87 },
  "sensor": { "camera_id": "CAM-07", "resolution": "1080p", "mode": "infrared" }
}
