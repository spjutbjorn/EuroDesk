# openrouteservice

**Category:** Routing / Fleet Planning
**Type:** Self-hosted or managed
**Jurisdiction:** Germany (EU) via HeiGIT / Heidelberg ecosystem
**Website:** [openrouteservice.org](https://openrouteservice.org)

## What It Is

openrouteservice is a route planning and geospatial API platform for directions, optimization, isochrones, matrix calculations, and logistics-oriented mapping workflows. It is useful for logistics planners, field services, mobility teams, and public-sector planning functions that need routing capabilities without defaulting to non-EU mapping platforms.

## Hosting Options

| Option | Description |
|---|---|
| **Self-hosted** | Run openrouteservice on your own EU-hosted infrastructure |
| **Managed API** | Use the hosted service where it meets your sovereignty requirements |

## Good Fit For

- Fleet and route planning
- Field service dispatching
- Public mobility and planning analysis
- Travel, tourism, and territory-based operations

## Self-Hosted Setup

### Requirements
- Linux server
- Docker
- OpenStreetMap data extracts

### Docker Example

```bash
docker run -d \
  --name ors-app \
  -p 8082:8082 \
  -e REBUILD_GRAPHS=True \
  -v $PWD/ors-config:/home/ors/config \
  -v $PWD/ors-data:/home/ors/files \
  openrouteservice/openrouteservice:latest
```

## Key Features

- Route planning and travel-time matrices
- Geospatial search and isochrone analysis
- Self-hosted API option
- OpenStreetMap-based routing workflows
- Useful for logistics and spatial planning roles

## Compliance Notes

- Prefer self-hosting when route data includes identifiable users, clients, or sensitive operational routes.
- Review map tile, geocoding, and integration dependencies for non-EU data exposure.
- Treat travel histories and dispatch patterns as operationally sensitive data.

## Trade-offs

- More technical to deploy than consumer mapping apps
- Requires map data management and performance planning
- Best when integrated into dispatch, scheduling, or planning workflows

## EuroDesk Verdict

openrouteservice fills a genuine gap for logistics, mobility, and planning-oriented office roles that need European route intelligence with self-hosting options.
