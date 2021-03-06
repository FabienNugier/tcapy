# tcapy change log

## Release Notes

* No official releases yet

## Coding log

* 06 May 2020
    * Change default Windows path to `e:\cuemacro\tcapy` from `e:\Remote\tcapy` to 
    make it more similar to Linux default
    * Now downloads tick data from New Change FX/NCFX using their updated API `DatabaseSourceNCFX`
    * Spun out some functionality for splitting up download dates from `DatabasePopulator` to `UtilFunc`
    * Added script to resample tick data and dump as Parquet eg. if we want to use tick data outside of tcapy
    * Fixed issue with `DatabasePopulator` ignoring downloading of points around end of periods if on weekend
    * Updated Dash/Plotly Python dependencies - appears to fix problems with non-updates of GUI so far
* 24 April 2020
    * Changed Redis repo, so installs latest version without compilation (given compilation very slow)
    * Added scripts for creating conda environment via YAML file (quicker installation)
    * Added links to view Jupyter notebooks by nbviewer
    * Bug fix on Excel implementation, now removes previously drawn charts
* 16 April 2020
    * Added Excel addin/spreadsheet to use tcapy (with xlwings)
    * Adding heatmaps (allowing for multiple metrics/breakdowns)
    * Updated Python dependencies
* 11 April 2020
    * Bug fixes for Influx download/upload (still need to speed up writing)
    * KDB fixes for download/upload (with new qPython version)
* 10 April 2020
    * Bug fixes for MySQL download/upload
    * Bug fixes for saving CacheHandle to VolatileCache
    * Bug fixes for periods without market data (including for cross rates)
    * Improved labelling for various charts with aggregation labels
    * Updated Jupyter notebook to reflect changes (eg. aggregation labels)
    * Added support for ChunkStore from Arctic, resulting in a very large speed improvement when fetching data from MongoDB
    * Added Jupyter notebook for populating database (MySQL, SQLite, Arctic and PyStore)
    * Added experimental support for using PyStore (partitioned Parquet files) to store market tick data
        * Having issues with append
    * Added support for SQLite to store trade/order data
    * Refactored ResultsForm init
    * Now uses Parquet as default binary format on disk
    * Updated dependencies (especially Python libraries)
* 02 April 2020
    * Added HTML versions of Jupyter notebooks
    * Added `DataNorm` as a parameter to `DataRequest`
    * Made chart titles neater for `TCAResults` with Jinja/WeasyPrint PDF creation and refactored report generator
    * Added scatter charts and associated methods/classes
* 27 March 2020
    * Various bug fixes 
        * In particular for `VolatileCache`
    * Updated Jupyter notebook - introducing_tcapy.ipynb
        * Note that Dukascopy downloader is not thread safe
        * Additional examples
    * Added Jupyter notebook - compliance_tca_calculations.ipynb
        * Show how to flag outlier trades and compute notional totals/slippage average per broker
    * Using pd.eval in BenchmarkSpreadToMid to speed up calculation
    * TCAResults can now parse the output from JoinTables
* 26 March 2020
    * Added Windows installation instructions for tcapy
* 24 March 2020
    * Fixed install link on README.md
* 20 March 2020
    * First public upload of tcapy
    
## Bugs/performance issues to be fixed (with date of addition)

* 30 Apr 2020
    * ISSUE: web GUI times out after a while, requiring user to refresh web page
* 24 Apr 2020
    * BUG: On the very first run of web GUI (after running restart_tcapy.sh), it doesn't display results (but computation 
    works in backend)
* 23 Apr 2020
    * PERFORMANCE: Speed up Dukascopy downloading, to reduce initialization time