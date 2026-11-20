# Interactive map: measles-susceptible children, Greenville and Spartanburg Counties, SC

Companion to the paper (add citation and DOI). The map shows results from a synthetic population
built with the UrbanPop method (ACS 2019-2023), not observed cases or real people.

## Files

| File | Contents |
| --- | --- |
| `index.html` | The map (Leaflet). Opens directly in a browser; no server needed |
| `data/blockgroups.js` / `.geojson` | 517 block groups: children and susceptible counts (one realization), LISA quadrant and scan cluster, stability across realizations and window sizes, demographic hot spot and bivariate stability |
| `data/schools.js` / `.geojson` | 222 schools: reported enrollment and MMR coverage (SC DPH 2024-25), LISA and scan results, DPH exposure sites |
| `data/counties.js` / `.geojson` | SC counties: outbreak cases and cases per 100,000 (SC DPH) |
| `data/meta.js` | Settings the page reads (realizations, windows, traits, export date) |

The `.geojson` files open in QGIS, kepler.gl or ArcGIS Online.

## Publish on GitHub Pages

1. Create a public repository (for example `sc-measles-map`) and upload `index.html`, `README.md`
   and the `data/` folder, keeping the folder structure.
2. In the repository: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   branch `main`, folder `/ (root)`, **Save**.
3. After a minute the map is at `https://<your-username>.github.io/sc-measles-map/`.
4. Edit `PAPER_URL` near the top of the script in `index.html` to link the paper.

To show it on your profile, add the link to your profile README (the repository named after your
username) or pin the repository.

## Column guide (block groups)

`B`, `C`, `D` = enrolled students, all children 1-17, children not in school data (all at home).

| Column | Meaning |
| --- | --- |
| `{k}_n`, `{k}_susceptible`, `{k}_rate` | Children and susceptible children in realization 0, and the share |
| `{k}_lisa_sim0` | Local Moran's I quadrant in realization 0 (HH, LL, HL, LH, ns) |
| `{k}_scan_sim0`, `{k}_scan_rr` | Scan cluster number (main window; -1 = none) and its relative risk |
| `{k}_LISA_freq`, `{k}_scan{10..50}_freq` | Share of realizations in which the block group was flagged |
| `{k}_scan_windows_stable`, `{k}_scan_core` | Number of window sizes at which it is stable; stable at all five |
| `zone` | Stable susceptibility cluster (by county) or outside |
| `{trait}_hot_freq`, `{trait}_bv_freq` | Share of realizations in a demographic hot spot / a bivariate High-High cluster |
