# RiverGuard
[RiverGuard](https://www.riverguard.earth) is a web map that shows where the Jamuna River in Bangladesh is eating its banks, and who lives behind them. It currently covers a 56 km stretch from Sirajganj to Chauhali, both banks.

## Key Features

* **History (2015–2021):** We turned yearly JRC Global Surface Water maps (Landsat, 30 m) into the outer edge of the river's permanent channels for each year. Every 2 km of bank gets a measured rate of land lost, a risk class (*Critical*, *High*, *Moderate*, or *Low*), and a confidence rating.

* **Radar (2026):** We processed two NASA-ISRO NISAR L-band images (June and November) from the same orbit. Water shows dark on radar, so we mapped it from the backscatter. Land that had vegetation or buildings in June and was open water by November is flagged as candidate bank loss.

* **Context:** One click on any spot shows its risk, land cover (ESA WorldCover), topsoil (ISRIC SoilGrids), and the people, schools, clinics, and roads within 2 km (WorldPop, OpenStreetMap).

* **Planning:** A filter shows only the stretches at a chosen risk level. A planner ranks stretches by `erosion rate × people exposed`, within a budget measured in kilometres of bank.

## Benefits

* **One clear view:** Brings scattered free satellite data together in a single map that non-experts can read.

* **Works when it matters:** Radar sees through monsoon cloud, exactly when banks fail.

* **Helps with priorities:** Shows planners where to send engineers first when budgets are limited.

* **Transparent:** Every number shows its source and confidence.

## Intended Impact

Riverbank erosion displaces thousands of families in Bangladesh every year, and the damage is usually mapped only after the land is gone. We want water agencies, local planners, and NGOs to spot fast-moving banks earlier, protect the most people for the resource available, and eventually monitor every monsoon routinely.

## Tools and Technologies

* **Languages:** Python, JavaScript, HTML, CSS

* **Data processing:** `rasterio`, `NumPy`, `SciPy`, `Shapely`, `h5py` (to read NISAR files), `pyproj`, `Pillow`

* **Web:** Leaflet maps with Esri satellite basemaps; hand-built HTML, CSS, and JavaScript; hosted on Vercel

* **Data access:** NASA Earthdata and ASF DAAC (NISAR GCOV, Sentinel-1 catalogue), EC JRC, ESA, ISRIC, WorldPop, OpenStreetMap (Overpass API)

* **Video:** Playwright for screen capture, DaVinci Resolve for editing

* **AI assistance:** ChatGPT and Gemini used for research, information formatting, logo creation, and satellite data navigation

* **Hardware:** A standard laptop, with no special equipment

## What's Creative About It

* **Radar and history together:** It combines a brand-new NISAR mission with seven years of history.

* **A careful signal:** It counts land as possibly lost only when it was vegetated in June and was water in November, after the floodwater had fallen, so ordinary flooding isn't mistaken for erosion.

* **Built around a click:** Each click turns raw data into a plain-language summary of that spot.

* **Honesty as a feature:** Confidence ratings and data sources are visible inside the app.

## Factors We Considered

* **Data limits:** NISAR data over the area starts only in June 2026, so the history comes from Landsat, and every layer says which satellite it came from.

* **Water level vs. erosion:** Monsoon flooding can look like bank loss. We used permanent water for history and labelled radar results as candidates.

* **No forecasts:** We had no way to test a forecast, so the risk index describes the past.

* **Missing data:** OpenStreetMap is thinly mapped on the river islands, and we found no verified cost data. We say so in the app, and the planner budgets in kilometres instead of money.

* **Responsible use:** Suggested actions are candidates for qualified engineers. The app flags that protecting one bank can shift erosion downstream.

* **Credits and licences:** Every data source and the drone footage is credited.

* **Usability:** The app works on laptops and phones, in dark theme, and loads fast enough for low bandwidth.
