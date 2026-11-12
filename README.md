# AL Observing Program Planner

A browser tool that helps Astronomical League members plan visual observing for the League's observing programs. Set your site, tonight's instrument and the programs you are working on. It then shows:

- **What's next** - from the star or target you are on now, the nearby targets that earn credit, ranked by credits, distance, how soon they set and difficulty
- **Tonight** - every target that earns credit in your observing window
- **My plan** - a list ordered west to east, with print and export to CSV, SkySafari and Stellarium observing lists
- **Progress** - a checklist for every program with progress toward each certificate level

Open `index.html`, or use the published page. Hover the small (i) marks for help.

## Your data stays with you
Site, equipment, plan and observed marks are stored in your own browser. On the Progress tab you can keep the marks in a file on your own computer (saved automatically in Chrome and Edge) or download a copy. Nothing is uploaded.

## Credit
The target lists and program requirements are the work of the [Astronomical League](https://www.astroleague.org/) and its observing program coordinators. This is an independent planning aid, not an official League tool. Always read each program's own page for its rules, required log details and how to submit.

Positions and some magnitudes for NGC, IC and Messier objects come from [OpenNGC](https://github.com/mattiaverga/OpenNGC) (CC-BY-SA 4.0). Magnitudes marked SIMBAD come from the SIMBAD database, operated at CDS, Strasbourg, France.

## Publishing on GitHub Pages
The page needs only two files: `index.html` and `al_data.js` (plus this README). They are collected in the `publish` folder.
1. Create a public repository on GitHub.
2. Upload the contents of `publish` (Add file > Upload files).
3. Settings > Pages > Build and deployment > Deploy from a branch > `main` / root > Save.
4. After a minute the page is live at `https://<your-user-name>.github.io/<repository-name>/`.

To update later, run `Make publish folder.bat` and upload the changed files.

## Rebuilding the data
1. `python al_fetch_lists.py` downloads the program lists from astroleague.org into `al_lists/`; `python tools/fetch_qv.py` adds the requirement grids.
2. `python tools/build_catalog.py` (or `Rebuild catalogue.bat`) writes `al_data.js` and `build_report.txt`. Needs `pip install pandas openpyxl xlrd beautifulsoup4`.
3. Optional: `python tools/fetch_magnitudes.py`, then step 2 again, to fill magnitudes from SIMBAD.

The lists published only as PDF are read from the text files in `al_lists/text/`.
