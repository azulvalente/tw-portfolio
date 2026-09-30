# Open-Meteo API: Endpoint Reference

Quick reference for two Open-Meteo endpoints: current weather and location search.

## Current Weather

Returns current weather conditions for a given coordinate pair.

**Base URL:** `https://api.open-meteo.com/v1/forecast`

### Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `latitude` | float | Yes | Latitude of the location |
| `longitude` | float | Yes | Longitude of the location |
| `current` | string | Yes | Comma-separated list of variables to return (e.g. `temperature_2m,wind_speed_10m`) |

### Example Request

```
GET https://api.open-meteo.com/v1/forecast?latitude=-34.6&longitude=-58.4&current=temperature_2m,wind_speed_10m
```

### Example Response

```json
{
  "latitude": -34.622143,
  "longitude": -58.40909,
  "timezone": "GMT",
  "elevation": 23.0,
  "current_units": {
    "temperature_2m": "°C",
    "wind_speed_10m": "km/h"
  },
  "current": {
    "time": "2026-09-22T22:45",
    "temperature_2m": 10.2,
    "wind_speed_10m": 6.4
  }
}
```

!!! note
    - `elevation` is returned in meters and reflects the terrain elevation at the given coordinates, not the request altitude.
    - Values inside `current` depend entirely on what was listed in the `current` parameter — omitted variables won't appear in the response.

---

## Location Search (Geocoding)

Searches for locations by name and returns matching coordinates, useful for resolving a city name before calling the weather endpoint above.

**Base URL:** `https://geocoding-api.open-meteo.com/v1/search`

### Parameters

| Parameter | Type | Required | Default | Description |
|---|---|---|---|---|
| `name` | string | Yes | — | Location name or postal code. Minimum 2 characters. |
| `count` | integer | No | 10 | Number of results to return (max 100) |
| `format` | string | No | `json` | Response format (`json` or `protobuf`) |

### Example Request

```
GET https://geocoding-api.open-meteo.com/v1/search?name=Berlin
```

### Example Response

```json
{
  "results": [
    {
      "id": 2950159,
      "name": "Berlin",
      "latitude": 52.52437,
      "longitude": 13.41053,
      "country": "Germany",
      "timezone": "Europe/Berlin",
      "population": 3426354
    },
    {
      "id": 5083330,
      "name": "Berlin",
      "latitude": 44.46867,
      "longitude": -71.18508,
      "country": "United States",
      "timezone": "America/New_York",
      "population": 9367
    }
  ]
}
```

!!! note
    - The search is name-based, not location-based. Searching "Berlin" returns every place named Berlin worldwide, not just the German capital. Sort or filter results by `population` or `country` if you need the most prominent match.
    - A two-character search matches exact names only; three or more characters use prefix matching.
    - Narrow results by appending a country or region to the `name` parameter, e.g. `name=Berlin, Germany`.