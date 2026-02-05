# Tune Changelog

## Future Work
- Copy values from camshaft timing (the Audi TT 225 map) KFNWSE
- Copy values for ignition timing Need to find this table again KFZW
- Do Linearization work one last time

## Unreleased

## 2026-02-03 — MLHFM correction

### Reason
- Original MLHFM scaling was based on approximate housing measurements
- Housing diameters were re-measured more accurately
- Car was not idling correctly

### Change
- Updated MLHFM using corrected MAF housing dimensions by running MAFADJUST.exe
- I used 60 and 73 as my inputs. I believe I underestimated the inner diameter of the old housing. This yielded a larger initial MLHFM value.
- Also updated TVUB - Injector latency. Copied this from previous tunes.

### Result
- The car idles! I need to drive it. Log for this is Initial.csv.

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
- Copied LAMFA from previous file (this is driver requested LAMBDA)

### Result
- 108 -> 2474 MLHFM did not run the car at all. This was the original output of the calculator. I measured the pipes again, and I think I came up with a better measurement.
