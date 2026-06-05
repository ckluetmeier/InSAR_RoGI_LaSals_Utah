# InSAR Rock Glacier Inventory — La Sal Mountains, Utah, USA

This repository contains the active and transitional rock glacier inventory (RoGI) for the La Sal Mountains, Utah, compiled using satellite-based InSAR and associated geomorphic and climate data.

**Associated publication:**
Kluetmeier, C. L., Handwerger, A. L., and Munroe, J. S. (2026). Active and transitional rock glaciers above the 0°C mean annual air temperature isotherm in the La Sal Mountains, Utah, USA. *Arctic, Antarctic, and Alpine Research*. https://doi.org/10.1080/15230430.2026.2680743

---

## Dataset

`LaSal_UT_active_RoGI.csv`

A CSV inventory of 41 active and transitional rock glaciers in the La Sal Mountains identified from Copernicus Sentinel-1 InSAR data (2016–2024). The inventory was compiled following the IPA Action Group *Rock Glacier Inventories and Kinematics* (RGIK) standard guidelines.

---

## Column Descriptions

### Identification and location

| Column | Description |
|---|---|
| `IPA_id` | Standard 18-character IPA primary ID. Format: `RGU` (unit) or `RGS` (system) + WGS84 centroid coordinates in decimal degrees (e.g., `RGU384455N1092526W` = rock glacier unit at 38.4455°N, 109.2526°W) |
| `lon` | Centroid longitude (decimal degrees, WGS84) |
| `lat` | Centroid latitude (decimal degrees, WGS84) |
| `geometry` | Centroid coordinates as a vector string `c(lon, lat)` |

### Morphology

| Column | Description |
|---|---|
| `Morphology` | Shape classification: `Tongue` (length > width) or `Lobate` (width > length) |
| `Up_connect` | Upslope unit connection: `TC` = talus-connected; `DC` = debris-mantled slope-connected |

### Physical characteristics (full rock glacier polygon)

| Column | Units | Description |
|---|---|---|
| `aspect_med_cardinal` | Median aspect of the full rock glacier polygon, cardinal direction (N, NE, E, SE, S, SW, W, NW) |
| `area_m2` | m² | Total area of the rock glacier polygon |
| `mean_slope_deg` | degrees | Mean slope across the rock glacier polygon (Copernicus 30-m DEM) |
| `mean_elevation_m` | m | Mean elevation of the rock glacier polygon (Copernicus 30-m DEM) |
| `mean_temp_C` | °C | Mean annual air temperature (MAAT) from PRISM 30-year normals (1991–2020), 800-m grid, averaged over the rock glacier polygon |
| `mean_precip_mm` | mm | Mean annual precipitation (MAP) from PRISM 30-year normals (1991–2020), 800-m grid, averaged over the rock glacier polygon |

### InSAR velocity — full rock glacier polygon

Velocities are line-of-sight (LOS) or downslope-projected means averaged over the full rock glacier polygon. Suffix `D` = descending track (T129); suffix `A` = ascending track (T49). The characteristic velocity used in the paper is the **moving area** downslope velocity (see next section). All velocity units are **m yr⁻¹**.

| Column | Description |
|---|---|
| `mean_velD` | Mean LOS velocity, descending track, full polygon |
| `mean_velA` | Mean LOS velocity, ascending track, full polygon |
| `LOS_vel_mean` | Mean LOS velocity (larger of ascending/descending), full polygon |
| `mean_dwslp_scalarD` | Mean downslope scalar velocity, descending track, full polygon |
| `mean_dwslp_scalarA` | Mean downslope scalar velocity, ascending track, full polygon |
| `mean_dwslp_velD` | Mean downslope velocity, descending track, full polygon |
| `mean_dwslp_velA` | Mean downslope velocity, ascending track, full polygon |
| `dwslp_vel_mean` | Mean downslope velocity (larger of ascending/descending), full polygon |

### Moving area (MA) characteristics

The moving area is the subset of the rock glacier surface showing a coherent InSAR deformation signal, delineated strictly from InSAR velocities without geomorphological constraints (per RGIK, 2023). Moving areas cover approximately 32.9% of total rock glacier area on average.

| Column | Units | Description |
|---|---|---|
| `MA_area_m2` | m² | Area of the rock glacier moving area |
| `MA_mean_slope_deg` | degrees | Mean slope of the moving area |
| `MA_aspect_med_cardinal` | — | Median aspect of the moving area, cardinal direction |
| `MA_mean_elevation_m` | m | Mean elevation of the moving area |
| `MA_mean_temp_C` | °C | PRISM MAAT averaged over the moving area |
| `MA_mean_ppt_mm` | mm | PRISM MAP averaged over the moving area |

### InSAR velocity — moving area

Velocity statistics computed over the moving area only. Units are **m yr⁻¹**.

| Column | Description |
|---|---|
| `mean_velD_MA` | Mean LOS velocity, descending track, moving area |
| `mean_velA_MA` | Mean LOS velocity, ascending track, moving area |
| `LOS_vel_mean_MA` | Mean LOS velocity (larger of ascending/descending), moving area |
| `mean_dwslp_scalarD_MA` | Mean downslope scalar velocity, descending track, moving area |
| `mean_dwslp_scalarA_MA` | Mean downslope scalar velocity, ascending track, moving area |
| `mean_dwslp_velD_MA` | Mean downslope velocity, descending track, moving area |
| `mean_dwslp_velA_MA` | Mean downslope velocity, ascending track, moving area |
| `dwslp_vel_mean_MA` | Mean downslope velocity (larger of ascending/descending), moving area — **this is the characteristic velocity reported in the paper** |
| `dwslp_velA_MA_fullScalar` | Full scalar downslope velocity, ascending track, moving area |
| `dwslp_velD_MA_fullScalar` | Full scalar downslope velocity, descending track, moving area |
| `dwslp_vel_MA_fullScalar` | Full scalar downslope velocity (larger of ascending/descending), moving area |

---

## Methods summary

Sentinel-1 SAR data (2016–2024, snow-free periods July–October) were processed using ISCE v2.5.1 and MintPy. Interferograms from ascending track T49 and descending track T129 were unwrapped with SNAPHU and inverted to produce average annual velocity maps and displacement time series. LOS velocities were projected onto the downslope direction following Liu et al. (2013), assuming uniform flow along mean azimuth and slope. Climate data are from the PRISM 800-m 30-year normals (1991–2020). Topographic attributes are derived from the Copernicus GLO-30 DEM. See the associated paper for full methodological details.

---

## Coordinate reference system

WGS84 geographic coordinates (EPSG:4326).

---

## Citation

If you use this dataset, please cite the associated paper:

> Kluetmeier, C. L., Handwerger, A. L., and Munroe, J. S. (2026). Active and transitional rock glaciers above the 0°C mean annual air temperature isotherm in the La Sal Mountains, Utah, USA. *Arctic, Antarctic, and Alpine Research*. https://doi.org/10.1080/15230430.2026.2680743

---

## Related resources

- Portland State University Active Rock Glacier Inventory (PSUARGI), contiguous US: https://doi.pangaea.de/10.1594/PANGAEA.918585
- Sentinel-1 data: Alaska Satellite Facility (https://search.asf.alaska.edu/)
- PRISM climate data: https://prism.oregonstate.edu/
- SNOTEL data: https://www.wcc.nrcs.usda.gov/snow/

