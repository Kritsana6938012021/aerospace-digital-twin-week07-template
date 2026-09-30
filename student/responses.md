# Week 07 Controls Lab — Responses

Answers and recorded model results from `submission.json`. This document does not recompute or independently validate the results.

## Submission status

- Schema: week07.submission/v1

- Record ID: 93efd672-de68-47f3-85da-61eda1384058

- Record revision: 50

- Model hash: fnv1a-76d8587a

- Readiness: Marked incomplete or not ready; missing: claim, reflection, aiUse

## Supplied setup (instructor supplied)

### question — instructor supplied
Calculate required control moment, elevator moment, and the change with airspeed. Explain whether the nominal response meets +0.12 rad/s².

### system — instructor supplied
Illustrative planar pitch model. Aircraft geometry, integration, force conversion and constraints are supplied.

### representation — instructor supplied
Body axes forward/right/down. Positive pitch moment nose-up. Positive Fz downward. Positive elevator trailing edge down. Reference/CG X=0 m; tail X=-3 m.

### inputs — instructor supplied
Iy=5000 kg·m²; target=+0.12 rad/s²; competing=-750 N-m; density=1.225 kg/m³; V=40 m/s; S=16 m²; chord=1.5 m; Cmδ=-0.8/rad; elevator=-5°. Inputs are illustrative, not calibrated.

## Student responses

### physics
**Prompt:** Explain why a downward force aft of the CG gives a positive nose-up moment.

**Student response:**
```
Due to Moment=I*a , there is a force downward at the back of cg , which gives us counterclockwise rotation for the moment to make a positive nose-up  moment in front of the cg 
```

### assumptions
**Prompt:** Explain one supplied assumption and what could invalidate it: planar motion, fixed reference, local linear effectiveness, no trim or damping.

**Student response:**
```
The local linear effectiveness assumption states that elevator deflection produces a proportional pitching moment based on a constant effectiveness coefficient. This assumption is invalidated at large control surface angles where flow separation or stall occurs.
```

### model
**Prompt:** Write your demand, dynamic-pressure, coefficient and moment equations. Identify which quantities are supplied and which are unknown.

**Student response:**
```
Demand: control moment plus competing moment equals inertia times target acceleration.The dynamic pressure is defined as q=0.5 pV^2 .Coefficient  is ΔCm = Cmδ × δe.The instructor supplies the aircraft geometry, flight airspeed, air density, pitch inertia, control derivative, nominal elevator deflection, target pitch acceleration, and competing moments.The dynamic pressure, total required control moment demand, actual elevator moment produced, moment variation with airspeed, and confirmation of whether the target acceleration is met remain unknown and must be calculated.
```

### prediction
**Prompt:** Before running your own implementation, predict the sign of its elevator moment and the effect of halving airspeed. Explain the competing moment.

**Student response:**
```
The elevator moment will have a positive sign because multiplying a negative control effectiveness coefficient by a negative elevator deflection   creating a nose-up rotation. Halving the airspeed reduces dynamic pressure  one-quarter of its original value , which quarters the elevator control moment  and severely degrades control effectiveness. The competing moment represents an external constant disturbance that acts on the aircraft, which the elevator control moment must overcome to achieve the desired pitch acceleration.
```

### verification
**Prompt:** Show one independent hand calculation with units. Compare it with your model, and explain a sign, unit, or limiting-case check.

**Student response:**
```
The elevator moment is M = 980 Pa *16m^2 * 1.5 m *0.069813=+1642.01N, which matches the model's output of 1642.01N. As a sign check, a negative elevator angle produces a positive nose-up pitching moment
```

### claim
**Prompt:** What do your computed results support at the stated condition? Include a limitation.

**Student response:**
_Missing — no response supplied._

### reflection
**Prompt:** What additional evidence or missing physics would you investigate next?

**Student response:**
_Missing — no response supplied._

### AI use
**Prompt:** Identify the AI tool and how you used it, what you changed, and how you independently checked the result. State “No AI used” if applicable.

**Student response:**
_Missing — no response supplied._

## Equations and model source

The recorded model JSON/expression source follows exactly as supplied. It is not interpreted or recomputed here.

```
{
  "schemaVersion": "week07.student-model/v1",
  "id": "week07-student-model",
  "version": "1.0.0",
  "slots": [
    {
      "id": "controls.demand",
      "expressions": [
        {
          "name": "requiredMoment",
          "expression": "pitchInertia * requestedAcceleration - competingMoment",
          "unit": "N*m"
        }
      ]
    },
    {
      "id": "controls.effectiveness",
      "expressions": [
        {
          "name": "dynamicPressure",
          "expression": "0.5 * density * airspeed * airspeed",
          "unit": "Pa"
        },
        {
          "name": "deltaCm",
          "expression": "elevatorDerivative * elevatorAngle",
          "unit": "1"
        },
        {
          "name": "deltaMoment",
          "expression": "0.5 * density * airspeed * airspeed * referenceArea * referenceChord * elevatorDerivative * elevatorAngle",
          "unit": "N*m"
        }
      ]
    }
  ]
}
```

## Recorded verification status

Recorded as passed for the submitted model hash.

- Checked at: 2026-09-30T15:22:09.473Z
- Detail: Student artifact passed demand, baseline elevator, quadratic speed, and neutral-deflection checks.

## Recorded model runs

### Run 1
- Recorded: 2026-09-30T15:22:12.717Z
- Run ID: 26bea85a-5a2d-490a-bc46-9f39812c580a
- Record revision: 49
- Model hash recorded with run: fnv1a-76d8587a
- Prediction recorded with run:

```
The elevator moment will have a positive sign because multiplying a negative control effectiveness coefficient by a negative elevator deflection   creating a nose-up rotation. Halving the airspeed reduces dynamic pressure  one-quarter of its original value , which quarters the elevator control moment  and severely degrades control effectiveness. The competing moment represents an external constant disturbance that acts on the aircraft, which the elevator control moment must overcome to achieve the desired pitch acceleration.
```
- Result status: recorded values shown below
- Values: `requiredMoment=1350 N*m`; `dynamicPressure=980 Pa`; `deltaCm=0.06981317007977318 1`; `deltaMoment=1642.0057602762652 N*m`

## Submission instructions

Use Save to GitHub in the app to save both files, commit, and push. Submit your fork URL and the saved commit SHA. Manual fallback: save this file beside `student/submission.json`, run `npm run student:prepare` and `npm run student:validate`, then commit and push student/.
