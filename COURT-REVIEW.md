# SPOTRECON — Court revision R2
Date: 21 October 2026 (UTC)

**Disposition:** continue as a pilot-supervised research concept for participating, mapped outdoor parking lots. Preserve the vehicle dock and occupancy map. No SPOTRECON prototype measurements have been supplied.

## What changes in R2

| Original poster | R2 decision |
| --- | --- |
| 150 m scan radius at 20–30 ft | Remove. Mission extent must follow camera visibility, a cleared flight route, energy and observation age. |
| >94% accuracy | Remove. No drone-specific held-out field evidence exists. |
| 8–12 min; 25 mph wind; light rain | Remove pending measured qualification of the complete configuration. |
| Universal magnetic/suction mount | Replace with a vehicle-specific mechanical attachment that still requires qualification. |
| Automatic return on any fault | Replace with a tested contingency policy based on available navigation, route and landing-area validity. |
| Green “open” spaces | Use observed empty / occupied / unknown, per-space capture age, and eligibility filtering. No reservation or arrival guarantee. |
| No people tracking | Design goal: no face recognition or plate identification; temporary obstacle detection may be needed for safety. |

The plausible first user is a lot operator surveying a participating site from a parked staff vehicle. This is a candidate use, not demonstrated demand or an economic advantage over fixed cameras.

## Checked math: illustrative optics, not performance

Assume an ideal rectilinear nadir camera, flat ground, square pixels, 3840 × 2160 image, 90° **horizontal** field of view, and camera height h = 20 m above ground.

- Ground width: W = 2h tan(FOV_H / 2) = 40 m.
- Ground height: H = W × 2160 / 3840 = 22.5 m.
- Single-frame footprint: 900 m².
- Nominal ground sample distance: GSD = W / 3840 = 0.0104167 m/pixel ≈ 10.4 mm/pixel.
- A 150 m-radius disk is π × 150² ≈ 70,686 m², about 78.5 frame areas before overlap and occlusion.

At the original 20–30 ft, these same assumed optics would cover only about 12.2–18.3 m in width. The 20 m example is a calculation assumption, not an approved operating altitude or a chosen mission specification.

GSD does not establish optical resolving power, stall-coordinate error or vacancy accuracy. Real calibration requires lens distortion, camera pose, timestamps, ground geometry and map registration.

Observation age: Δt = t_display − t_capture, using consistent clocks. Hidden, stale, ambiguous or ineligible spaces become unknown. Freshness limits require testing.

Conservative continuation requirement:
E_remaining,lower ≥ E_return,upper + E_approach/abort,upper + E_divert/land,upper + E_margin.

This funds the allowed failed-dock sequence, rather than whichever single landing option is cheapest. Every term and uncertainty bound needs measurements.

## Proposed operating architecture

- Pilot-authorized launch; host vehicle remains stationary. Initial testing uses a controlled, unoccupied flight corridor and a separately available contingency landing area.
- Qualify flight and docking on a fixed pad before qualifying a particular roof attachment.
- Enclosure clearance, transport retention, final approach and vehicle motion are separate checks. The transport latch is engaged for storage, then released and verified clear before launch.
- Reject a moving, obstructed, partly open or stale-state dock. Authenticate dock state and independently observe geometry; a status message alone does not prove a clear landing path.
- Bound approach retries by measured energy and safe landing options. No landing on a moving car.
- The phone and occupancy software remain advisory; flight safety must remain onboard if the phone disconnects.
- C2 loss plus degraded navigation requires a tested combined-fault response. Neither generic return-to-home nor translation toward an alternate area is universally safe. Hold/descent is also not a generic safe default.
- Mount, enclosure, propeller clearance, battery, charge interlocks, sensing and environmental envelope remain unqualified design elements.

## Four Court questions

1. **Exact claim:** a supervised, vehicle-docked scout could deliver recent occupancy observations for visible, eligible spaces within a participating lot.
2. **Evidence in hand:** checked ideal camera geometry, primary documentation for established camera/autopilot methods and current US operating constraints; no SPOTRECON physical evidence.
3. **Contribution:** the integration and validated operating workflow could be useful. Drone docks and parking vision are existing fields; no novelty or patent conclusion is made.
4. **Kill test:** in staged simulation, caged and controlled-site tests, invalidate the dock while injecting navigation/link faults and reducing available reserve. Any unsafe approach, unbounded retry, or inability to reach an available safe outcome fails the proposed envelope. Separately, blinded held-out flights must measure false-vacancy errors, useful coverage, map error and capture age together.

Measure vacant precision = true vacant reports / all vacant reports alongside usable coverage = fresh, visible, eligible reported spaces / mapped eligible spaces. Record failures and unknown states, not just successful demonstrations. Predetermine pass criteria and separate test data by lot and day.

## External AI review record

Grok, Claude and Gemini returned text-based engineering reviews of the concept. The table records accepted and rejected suggestions; no service endorsement is implied.

| Service | Role and result | Revision decision |
| --- | --- | --- |
| Grok | Adversarial coverage, energy and dock review returned. | Accepted the failure questions; rejected categorical endurance/safety conclusions unsupported by a configured system. |
| Claude | Systems architecture review and requested corrections returned. | Accepted separation of flight/map layers and worst-sequence reserve. Corrected latch logic and fault routing. Arbitrary retry/trial counts are not adopted as validated requirements. |
| Gemini | Optics review and correction returned. | Accepted ideal footprint arithmetic. Challenged its unjustified visibility-probability formula and universal VLOS-angle implication; Gemini withdrew both. Neither enters R2. |
| Meta AI | Returned an inability to help with this request “right now.” | No technical review or endorsement attributed. |

Three internal Court reviewers separately checked imaging, flight/docking failures and US operating constraints. AI agreement is not independent experimental evidence.

## Primary references

- [OpenCV camera calibration and projection](https://docs.opencv.org/4.12.0/d9/d0c/group__calib3d.html): camera intrinsics, extrinsics and lens distortion. Does not validate this hardware.
- [PX4 return-mode documentation](https://docs.px4.io/main/en/flight_modes/return): return behavior is configuration dependent; it does not establish obstacle-free roof docking.
- [14 CFR 107.31](https://www.ecfr.gov/current/title-14/chapter-I/subchapter-F/part-107/subpart-B/section-107.31): VLOS baseline, absent applicable relief.
- [FAA operations over people overview](https://www.faa.gov/uas/commercial_operators/operations_over_people): routine operations over people/moving vehicles are conditional. Parking-area access, airspace and aircraft eligibility require separate consideration.

R2 poster imagery is an illustrative concept. Runtime, mass, wind/rain envelope, occupancy performance, docking reliability, mounting retention and public-use readiness remain unmeasured.

