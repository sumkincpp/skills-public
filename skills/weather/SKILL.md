
---
name: weather
description: Get current weather conditions for any city using Open-Meteo. Use when asked about temperature, wind, or precipitation at a location.
compatibility: Requires internet access and an HTTP GET tool.
---

# Weather

Use the free Open-Meteo APIs to retrieve current weather.

## Step 1: Geocode the location

If coordinates are not provided, request:

https://geocoding-api.open-meteo.com/v1/search?name={city}&count=5

URL-encode the city name. Use `countryCode` if the
user specified a country.

Select the matching result and extract:
- latitude
- longitude
- name
- country

Ask for clarification if the location is ambiguous.

## Step 2: Fetch current weather

Request:

https://api.open-meteo.com/v1/forecast?latitude={latitude}&longitude={longitude}&current=temperature_2m,wind_speed_10m,precipitation&timezone=auto

## Step 3: Respond

Read the `current` object and `current_units`.

Report the location, observation time, temperature,
wind speed, and precipitation.

## Rules

- Never fabricate weather data or coordinates.
- Handle missing results and API errors.
- Report when HTTP access is unavailable.
