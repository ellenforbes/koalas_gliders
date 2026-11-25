# Olive Downs - Koala & Glider Monitoring

Static site published from collar GPS data and vet records. Open `index.html`
in a browser (or publish to GitHub Pages from the root of this folder).

## Files

- `index.html` - Exploratory Data Analysis report (the entry page)
- `map.html` - Interactive Folium map (species-aware, all layers toggleable)
- `dashboard.html` - Plotly dashboard with sortable summary table
- `figures/` - Static PNG charts referenced from index.html
- `brand/` - Pembroke Resources brandmark + Olive Downs Complex sub-brand SVGs
- `tables/` - CSV summary tables (per-koala movement, home ranges, daily distance)

## Publishing on GitHub Pages

1. `git init && git add . && git commit -m "Initial publish"`
2. Push to a repo on GitHub
3. Repo Settings -> Pages -> deploy from branch -> root (`/`)
4. The site lives at `https://<user>.github.io/<repo>/`

## Refreshing

The Python pipeline that builds this site lives in `../analysis/`. To refresh
after new collar data arrives:

```
rm ../outputs/_cache/gps_all.parquet ../outputs/_cache/home_ranges*.pkl
python ../analysis/run_eda.py
python ../analysis/run_home_ranges.py
python ../analysis/run_gis_export.py
python ../analysis/run_dashboard.py
python ../analysis/build_web.py    # regenerates this folder
```
