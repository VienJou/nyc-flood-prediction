# NYC Flood Prediction

Real-time flood depth and category predictions for New York City, updated 4× daily.

**Model**: MMBTWithTabPFNLegacy (DEM + AlphaEarth + 3-tier weather features)  
**Weather**: GFS via Open-Meteo API  
**Resolution**: 300 m spatial sampling, 6-hour update cycle

## How it works

1. GFS weather model updates at 00z, 06z, 12z, 18z UTC
2. Open-Meteo publishes processed GFS data ~15–30 min later
3. SLURM job fetches weather, runs GPU inference over NYC, exports web artifacts
4. This repo is updated automatically

## Data files

| File | Description |
|------|-------------|
| `data/latest.json` | Metadata, borough stats, weather summary |
| `data/flood_prediction.png` | Colorized flood depth + category map |
| `data/weather_latest.json` | Current weather at 4 key locations |
