# Lower Willapa River Measurement Campaign (2025–26)

This repository contains all data and documentation for the Lower Willapa River Measurement Campaign (2025–26) by the UW CoPes team, as well as some preliminary analysis. This dataset was supported by the Pacific Conservation District and Pacific County Emergency Management Agency, whose assistance with field deployment and connections to local community members were invaluable. The Willapa River, South Fork, and Skidmore Slough data will additionally be published using Dryad and can be accessed with the following link [to be inserted]

## Repository Contents

- `lowill_field_methods.pdf` — Field methods
- Sensor data files by location *(covers measurements up to the March retrieval; update as needed)*
- `lowill_totalwaterlevel_dataset.csv` — Datetimes [PST] and TWL NAVD88 [m] for all locations
- `lowill_complete_dataset.csv.zip` — Datetimes [PST], absolute pressure, atmospheric pressure, TWL [m], and TWL NAVD88 [m] for all locations *(update before further analysis on future data)*
- `lowill_deployment_tracking_sheet.pdf` - Deployment Tracking Sheet
- `lowill_polished_survey_data.csv` — Survey data
- `lowill_sensor_locations.kml` — Google Earth KML file *(see Figure 1 in Deployment Locations)*
- `lowill_totalwaterlevel_plotter.ipynb` (Jupyter Notebook) — Plots TWL NAVD88 per location from the polished dataframe
- `lowill_data_corrections.ipynb` (Jupyter Notebook) — Converts raw data to TWL NAVD88; documents trimming and conversion steps
- **Analysis** (Jupyter Notebook) — All analysis completed to date

---

## Locations

All sensors were deployed within or near South Bend and Raymond, Washington, organized into four regions:

1. Willapa River (prefix: `WR`)
2. Willapa River South Fork (prefix: `SF`)
3. Skidmore Slough (prefix: `SS`)
4. Floodplain (prefix: `FP`)

---

## Sensors

**Measurement frequency:** 5 minutes

| Sensor | Measures |
|--------|----------|
| TD-Diver | Pressure, temperature |
| HOBO Water Level Logger U20-001-01-TI | Pressure, temperature |
| In-Situ Rugged Troll 100 | Pressure, temperature |
| Tolthawk | Water level (real-time: [WR01](https://sensors.tolthawk.com/Home/Index?regionId=69&locationId=800&chartType=5&from=-20&to=0&weatherIds=&tidalId=null), [WR02](https://sensors.tolthawk.com/Home/Index?regionId=69&locationId=797&chartType=5&from=-20&to=0&weatherIds=&tidalId=null)) |
| YSI CTD 600LS | Pressure, temperature, salinity |
| AQUAlogger 210TY (OBS) | Pressure, temperature, turbidity |
| UW RAPID Feather Wave Gauge | Pressure |

---

## Measurements and Datasets

Most data collected are absolute pressure measurements, with some locations also measuring temperature and salinity. Temperature, salinity, and atmospheric pressure from the NOAA Toke Point gauge were used to convert absolute pressure to Total Water Level (TWL). Survey data was used to convert TWL to TWL relative to the NAVD88 vertical datum.

The repository includes a complete dataset (all conversion steps) and a polished dataset (TWL adjusted to NAVD88 where applicable).

---

## Installation Techniques

### Subtidal sensors (WR, SF, SS)

Sensors were attached primarily to historic pilings along the river and sloughs. To capture the full tidal range, sensors were fastened to the bottom of mounts and deployed at the lowest tide of the day. Mounts progressed from 8-foot PVC and slotted zinc-coated steel angles to 8-foot aluminum tubing. Sensors were secured with stainless steel hose clamps, zip ties, and electrical tape. Nails were hammered 1 ft and 2 ft above the top of each mount to track movement from initial deployment position. Significant movement instances are discussed in the [Uncertainty](#uncertainty) section.

### Floodplain sensors (FP)

Sensors were attached to nearby structures (street signs, fence posts) using stainless steel hose clamps, zip ties, and electrical tape. Where no nearby structures existed (e.g., Central Avenue culvert), sensors were fastened to steel gardening stakes driven into the ground.

### Radar sensors

Radar sensors were installed at two locations:
- **WR01 (Bendiksen's Landing)** — attached to the dock
- **WR02 (Raymond's Landing)** — attached to the top of a dock piling

As these sensors cannot become submerged, they were mounted at high elevations.

---

## Trip Summaries

> Full deployment and retrieval details are in the `lowill_deployment_tracking_sheet.pdf`. "Serviced" = sensor retrieved, downloaded, and redeployed. "Retrieved" = sensor removed with no redeployment. Some locations have multiple sensors; this summary does not distinguish between them.

| Trip | Dates | Activity |
|------|-------|----------|
| Recon | 10/21–10/22 | Deployed: WR03 |
| D1 | 11/6–11/8 | Serviced: WR03. Deployed: WR01, WR02, WR04–06, SF01–02, SS01–03, WATERSTREET, VET, RIVERDALE, ABBYROAD, BARGE, EYECLINIC |
| D2 | 11/25 | Deployed: WR07, WR08, SF03, CENTRAL |
| D3 | 12/14–16 | Retrieved: WR05. Serviced: WR01, WR03, WR06, BALLPARK, VET, ABBYROAD, WATERSTREET, BARGE, RIVERDALE, CENTRAL, EYECLINIC, HECKARD. Deployed: WR07 |
| D4 | 1/11–12 | Serviced: WR03, WR04, WR06, WR07, SF01–03 |
| D4.5 | 1/28 | Serviced: WR08 |
| D5 | 3/8–9 | Retrieved: WR01, BALLPARK, VET, WATERSTREET, ABBYROAD, BARGE, RIVERDALE, EYECLINIC, HECKARD. Serviced: WR03, WR04, WR06, WR07, SF01, SF03, SS01–03 |
| D6 | 6/7–6/8 | TBD |

---

## Survey

Surveys were completed using an Emlid RS3 (on a 1.8 m collapsible pole) and an Emlid RX (on a 1.99 m pole), connected to the Washington State Virtual Reference Network. Coordinates reported in Washington State Plane Zone South (NAD83) horizontal and NAVD88 (Geoid18) vertical. Each survey used 30-second averaging.

**Equipment:**
- Emlid RS3 S/N: `8243CA3BAAD4E443`
- Emlid RX S/N: `8243fa6e4a7a666e`

**Pole length corrections (RS3):**

| Configuration | Length | Elevation adjustment |
|---------------|--------|----------------------|
| Fully extended | 1.80 m | — |
| Bottom collapsed | 1.24 m | +0.56 m |
| Fully collapsed | 0.73 m | +1.07 m |

All survey data is in `lowill_polished_survey_data.csv`. Sensor coordinates are in the [Deployment Locations](#deployment-locations) section.

---

## Software

| Software | Used for |
|----------|----------|
| HOBOware | HOBO sensors |
| Win-Situ 5 | In-Situ sensors |
| Diver Office | Diver sensors |
| Ecowatch Lite | CTD sensors |
| Arduino IDE | RAPID sensors |

---

## Uncertainty

### Universal

- **Survey subnet variation:** PACWAVRSRTCM3 was the primary subnet; RYMD3 and RYMD_MSM were used where needed. Subnet used is recorded per point in `lowill_polished_survey_data.csv`.
- **Single 30-second averages** used for all survey points.
- **Indirect surveys:** Most surveys were measured at a distance from the sensor head; offsets were recorded in field notebooks and corrected in post-processing via the Deployment Tracking Sheet.
- **Collapsible pole:** Corrections for collapsed-pole surveys are recorded and accounted for in the Deployment Tracking Sheet.
- **FLOAT vs. FIX:** A few locations could only be surveyed with FLOAT status, which is unreliable for elevations.

### Site-Specific

- **WR08 / SF03:** Survey not possible due to poor coverage. WR08 elevation was estimated for timestack visualization purposes.
- **WR03 (pressure/OBS):** Observed downslide of 3" (D1→D3) and ¾" (D3→D4); redeployed at original position after D4.
- **WR08 (pressure):** PVC-mounted to a tree with significant scour observed at the base.
- **SF03 (pressure):** Attached to a concrete block wedged between rocks; block rotated from horizontal to vertical by D5 retrieval. Redeployed in original position.
- **SS03 (pressure):** Mount moved to a nearby piling deeper in the channel at D4; surveyed in both positions.

---

## Reference Data

Two external datasets are included as river-dominated and tidally-dominated end conditions, and MET data from Toke Point was used for pressure-to-TWL conversions.

| Source | Label in datasets | Link |
|--------|-------------------|------|
| USGS-12013500 — Willapa River Near Willapa, WA | `USGS` | [USGS](https://waterdata.usgs.gov/monitoring-location/USGS-12013500/) |
| NOAA-9440910 — Toke Point, WA | `TP` | [NOAA](https://tidesandcurrents.noaa.gov/stationhome.html?id=9440910) |
