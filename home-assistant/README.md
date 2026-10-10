# Home Assistant: wall panel Travel tab live flight map

Drop-in configuration that adds a live flight map to the wall panel's
**Travel** tab. The map is shown only while the tracked flight is in the air;
otherwise the tab shows the flight status and a box to enter a flight number.

| File | Purpose |
| --- | --- |
| `packages/flight_tracking.yaml` | Template sensors (`sensor.tracked_flight`, `binary_sensor.flight_in_air`), the `input_text` helper and an automation that starts FlightRadar24 tracking. |
| `dashboards/wall-panel-travel-view.yaml` | The Travel view: conditional map + details card while airborne, status card otherwise. |

## Setup

1. Install the **Flightradar24** integration from HACS and configure it.
2. Enable packages in `configuration.yaml` and copy `flight_tracking.yaml` into `<config>/packages/`.
3. Restart Home Assistant.
4. Open the wall panel dashboard, edit it, open the raw configuration editor and
   paste the Travel view from `wall-panel-travel-view.yaml` (or just its two
   conditional cards into your existing Travel view).
5. On the panel, type a flight number (for example `DL1234`) into
   *Flight number to track*. Once the aircraft is airborne the map pops up.

If your FlightRadar24 tracked sensor is not `sensor.flightradar24_tracked`,
change the `SOURCE` entity id in `flight_tracking.yaml`.
