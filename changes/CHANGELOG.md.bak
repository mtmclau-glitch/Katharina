# Tune Changelog

## Future Work
- Copy values from camshaft timing (the Audi TT 225 map) KFNWSE
- Copy values for ignition timing Need to find this table again KFZW
- Do Linearization work one last time

## Unreleased

## 2026-02-07

### Reason
- I forgot to enable left-foot braking
- Rev limiter was still 6800 - needed to increase NMAXOG

### Change
- NWPMBBR - set to max (minimum RPM - for left-foot braking)
- VWPMBBR - set to max (minimum speed - for left-foot braking)
- NMAXOG - set to 7000

### Result
- Rev limiter seems higher, but Engine Torque follows rlmax_w until 5,300 (good behavior) before switching to follow rlsol_w (meh behavior)
- This may be due to KFMIOP limitations - I may need to increase the load axis

## 2026-02-05 - KFLDRL BACK to 0 again and raised torque limiters

### Reason
- KFLDRL should stay at zero for baselining--it was a mistake to change it so soon
- LDRXN and KFLDHBN were probably limiting throttle plate angle due to higher boost

### Change
- Reset KFLDRL back to zero again
- Raised LDRXN to keep it from limiting throttle (outside of reach of the turbo for now)
- Raised KFLDHBN to keep it from limiting throttle (outside of reach of the turbo for now)

### Result
- Great success!
- msdk_w and mshfm_w divergence happened at a higher RPM (around 5,500) (I'm not sure why it was different.)
- Throttle plate did not close on me
- fra_w was better today (.912) than yesterday (.873), but still not great.

## 2026-02-04 - KFLDRL back to stock

### Reason
- KFLDRL had been zero for baselining. Set to stock for further characterization.

### Change
- Reset KFLDRL back to stock (guidance from nefmoto)

### Result
- Did not Run this yet
- Advice from nefmoto superceded this change

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
- The car runs OK, too. Not fast, and the throttle closes at higher RPM, but it's soft and reasonable. First_Drive.csv is the log.

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
