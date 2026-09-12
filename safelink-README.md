# SafeLink — Neighborhood Safety Network

**Interactive GIS platform visualizing safety incidents and emergency resources geographically.**

## Overview

SafeLink is a web-based GIS platform that maps safety incidents and emergency resources (police stations, hospitals, shelters, etc.) across a neighborhood or city, giving residents and responders a geographic view of where issues are concentrated and where help is nearby.

## Tech Stack

- **SvelteKit** — application framework and routing
- **MapLibre GL** — interactive vector map rendering
- **WebGL** — GPU-accelerated map and data-layer rendering

## Features

- Interactive map with layered visualization of safety incidents by type, recency, and severity
- Geographic overlay of emergency resources (hospitals, police stations, shelters)
- Filterable views by incident category and time range
- Smooth pan/zoom performance via WebGL-accelerated rendering, even with dense data layers

## Getting Started

### Prerequisites

- Node.js 18+
- npm or pnpm

## Data Model

Incidents and resources are stored as geotagged records (latitude/longitude plus category, timestamp, and metadata) and rendered as MapLibre GL layers, allowing new incident types or resource categories to be added without changing the rendering pipeline.

## License

MIT
