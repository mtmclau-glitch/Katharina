# Tune Changelog

## Future Work
- Copy values from camshaft timing (the Audi TT 225 map) KFNWSE
- Copy values for ignition timing Need to find this table again KFZW
- Do Linearization work one last time

## Unreleased

## 2026-02-09 - MLHFM Scaled down 2%

### Reason
- MAF scaling wasn't matching the model and was significantly higher than the model

### Change
- Decreased MAF table at the 140 g/s region and up by scaling the highest point by multiplying it by 0.98 and then interpolating starting at 140 g/s
- Note that this required the use of the MLHFM table that had g/s in it and not just raw values - this could be totally wrong, but it's a place to start
- Later, I scaled MAF down one more time by the same 0.98 using the same technique as above and called it Outing
- Notably, I chose to inflect a little earlier - Down around 120 g/s - But I did NOT keep this change (see next bullet)
-- What I did instead of keeping the change was to keep the same upper value (the very highest value was still, effectively 0.96 of its original value)
-- I restored the 120-130 g/s range to what it was before and choosing the ~130 or 140 point for the new deflection.

### Result
- msdk_w and mshfm_w diverged again
- fra_w is dead-on - Does this mean the MAF scaling is getting better?
- I still need to drive the car with the very latest changes where the MLHFM g/s graph was changed to restore 120-130 g/s behavior but that had the second drop in MLHFM at top

## 2026-02-08 - KFMIOP Load Axis Increased

### Reason
- Increasing load axis due to larger turbo

### Change
- Increased load axis for KFMIOP to match the previously good tune
- Increased Z axis values in KFMIOP to match that file too, which mostly matched the community tune v1 file

### Result
- The car appeared to run significantly better
- The throttle did close, but that was right at the end
- msdk_w and mshfm_w diverged again, but after the divergence, they tracked in the same direction -- this might be good

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
