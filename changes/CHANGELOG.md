# Tune Changelog

## Future Work
- Copy values from camshaft timing (the Audi TT 225 map) KFNWSE
- Copy values for ignition timing Need to find this table again
- Do Linearization work one last time

## Unreleased

## 2026-02-03 — Initial Setup

### Changes
- Starting over from stock
- Copied the MLHFM output from MAFADJUST.exe
- Adjusted top speed limiter to 200 mph or higher (effectively disable it) VMAX[NB, PNG, and NIV set to 300]
- Adjusted rev limiter to 7,000 RPM NMAX (Was 6800, which was the limiter)
- Adjusted rev limiter warning to 7,300 RPM NMAXF (called Fault Detection - Was 7100, so I kept it 300 above NMAX)
- Disabled SAI (Step 1) MSLUB = 0
- Disabled SAI (Step 2) MSLBAS = 0
- Disabled Catalyst Heating FKHABMN = 0
- Copied values for fuel injector scaling KRKTE
- Set KFLDRL = 0 according to fknbrkn at nefmoto
- Set NDLDRAPU = 9999 according to fknbrkn at nefmoto (to avoid underboost issues)
- Disabled anti-judder KFDMDARO = 100 at highest axis load

### Result
- 
