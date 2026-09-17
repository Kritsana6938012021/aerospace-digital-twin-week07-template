# Week 07 Controls Lab — Responses

Answers and recorded model results from `submission.json`. This document does not recompute or independently validate the results.

## Submission status

- Schema: week07.submission/v1

- Record ID: e5a1fee8-c467-49a2-b756-5621b5d12a93

- Record revision: 806

- Model hash: fnv1a-39de33c2

- Readiness: Marked incomplete or not ready; missing: verification, claim, reflection, aiUse, execution

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
For planar motion ,assumes motion is strictly 2D (pitching about the body Y-axis only)and what could invalidates is are Roll or yaw inputs.
```

### model
**Prompt:** Write your demand, dynamic-pressure, coefficient and moment equations. Identify which quantities are supplied and which are unknown.

**Student response:**
```
Demand: Iy*target - competing
q : 0.5*density*v^2
Cm : M / q*s*c
Moment equation: M=Cm*q*s*c

```

### prediction
**Prompt:** Before running your own implementation, predict the sign of its elevator moment and the effect of halving airspeed. Explain the competing moment.

**Student response:**
```
Elevator moment : positive because it nose-up.Effect  of having airspeed : Moment generate from the elevator is proportional to v^2.
```

### verification
**Prompt:** Show one independent hand calculation with units. Compare it with your model, and explain a sign, unit, or limiting-case check.

**Student response:**
_Missing — no response supplied._

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
ENGINEERING IMPLEMENTATION BRIEF — Week07
Implement only student-owned JSON; do not edit platform code. Do not fill missing decisions.
question: Calculate required control moment, elevator moment, and the change with airspeed. Explain whether the nominal response meets +0.12 rad/s².
system: Illustrative planar pitch model. Aircraft geometry, integration, force conversion and constraints are supplied.
representation: Body axes forward/right/down. Positive pitch moment nose-up. Positive Fz downward. Positive elevator trailing edge down. Reference/CG X=0 m; tail X=-3 m.
physics: Due to Moment=I*a , there is a force downward at the back of cg , which gives us counterclockwise rotation for the moment to make a positive nose-up  moment in front of the cg 
assumptions: For planar motion ,assumes motion is strictly 2D (pitching about the body Y-axis only)and what could invalidates is are Roll or yaw inputs.
inputs: Iy=5000 kg·m²; target=+0.12 rad/s²; competing=-750 N-m; density=1.225 kg/m³; V=40 m/s; S=16 m²; chord=1.5 m; Cmδ=-0.8/rad; elevator=-5°. Inputs are illustrative, not calibrated.
model: Demand: Iy*target - competing
q : 0.5*density*v^2
Cm : M / q*s*c
Moment equation: M=Cm*q*s*c

prediction: Elevator moment : positive because it nose-up.Effect  of having airspeed : Moment generate from the elevator is proportional to v^2.
verification: 
claim: 
reflection: 
aiUse: 
Return {schemaVersion:"week07.student-model/v1",id,version,slots:[{id:"controls.demand",expressions:[{name:"requiredMoment",expression:"...",unit:"N*m"}]},{id:"controls.effectiveness",expressions:[{name:"dynamicPressure",expression:"...",unit:"Pa"},{name:"deltaCm",expression:"...",unit:"1"},{name:"deltaMoment",expression:"...",unit:"N*m"}]}]}.
Approved inputs: pitchInertia (kg*m^2), requestedAcceleration (rad/s^2), competingMoment (N*m), density (kg/m^3), airspeed (m/s), referenceArea (m^2), referenceChord (m), elevatorDerivative (1/rad), elevatorAngle (rad).
Use + - * / parentheses, constants, inputs and named intermediates only. No JavaScript. Angles arrive in radians. Check baseline, zero target, half speed, zero elevator and signs.

```

## Recorded verification status

No verification record was supplied.

## Recorded model runs

_Missing — no model runs supplied._

## Submission instructions

Use Save to GitHub in the app to save both files, commit, and push. Submit your fork URL and the saved commit SHA. Manual fallback: save this file beside `student/submission.json`, run `npm run student:prepare` and `npm run student:validate`, then commit and push student/.
