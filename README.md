# Schema Description

The schema currently looks as follows:

High-Level Structure of the FitFile Schema

```text
FitFile
|- FitFile Version
|_ Workouts (Array of Workout)
   |- Workout_Name              ✅  (string)
   |- Workout_Priority          ✅  (string)
   |- Workout_Type              ✅  (enum)
   |- Workout_Category          ✅  (enum)
   |- Planned_Training_Load     ✅  (integer)
   |_ Tasks (Array of Tasks)    ✅
      ├─ Step                   ✅  (integer)           – sequence number
      ├─ Name                   ✅  (string)            – short label
      ├─ Segment_Type           ✅  (enum)              – segment type: Warmup, Interval, Ramp, SteadyState, Cooldown, Rest, FreeRide
      ├─ Duration               ✅  (integer, sec)      – length of segment
      ├─ Distance               ✅  (integer, Meter)    – optional, for running/swimming/cycling
      ├─ Target_Power           ✅  (integer, Watt)     – fixed power target
      ├─ Target_Power_Low       ✅  (integer, Watt)     – lower bound of power range
      ├─ Target_Power_High      ✅  (integer, Watt)     – upper bound of power range
      ├─ Target_Power_Zone      ✅  (integer)           – power zone number
      ├─ Target_Heartrate       ✅  (integer, BPM)      – fixed heart‐rate target
      ├─ Target_Heartrate_Zone  ✅  (integer)           – heart‐rate zone number
      ├─ Cadence                ✅  (integer, RPM)      – fixed cadence target
      ├─ Cadence_Low            ✅  (integer, RPM)      – lower cadence bound
      ├─ Cadence_High           ✅  (integer, RPM)      – upper cadence bound
      ├─ Repeat                (integer)                – number of intervals
      ├─ OnDuration            (integer, sec)           – “on” phase duration for intervals
      ├─ OffDuration           (integer, sec)           – “off” phase duration
      ├─ OnPower               (integer, Watt)          – target power during “on” phase
      ├─ OffPower              (integer, Watt)          – target power during “off” phase
      ├─ Ramp_Start            (integer, Watt)          – starting power for ramps
      ├─ Ramp_End              (integer, Watt)          – ending power for ramps
      ├─ Pace                  (integer, sec/km)        – target pace for runs
      ├─ Description            ✅  (string)            – detailed notes or instructions
      ├─ TextEvent              ✅  (array of TextEvent) – in‐workout message with timing
         |- Duration            ✅  (integer, sec)      - How long the message is displayed
         |- Message             ✅  (string)            - Message Text to display
         |- TimeOffset"         ✅  (integer, sec)      - Seconds from the start of this step when the text appears
      └─ Tags                  (array of string)        – freeform metadata labels

```

Some Fields are only valid if the right Sporttype is choosen. For example Cadance is valid for Running, Cycling, Rowing

✅ Are allready implemented in the schema file
