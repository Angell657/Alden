# Alden 🏠

**Local-first household operations intelligence.**

Alden keeps the household running, monitors approved devices, handles routine issues where authorized, and escalates important decisions. **Concept stage:** no live device integrations or autonomous behavior exist yet.

## Responsibilities
- Coordinate vacuum/maid robot schedules, docking, maintenance, errors and consumables, subject to actual accessible APIs.
- Monitor supported appliances, equipment health, household inventory, maintenance and supplies.
- Coordinate with the food-planning app for groceries, freezer stock, meal schedules and reminders, when explicitly linked.
- Deliver quiet, useful briefings about completed work, exceptions and approvals.
- Later: coordinate additional robotics, but never circumvent independent device safety systems.

## Operating principles
1. **Local first:** no mandatory cloud service, subscription, telemetry or internet connection to run Alden.
2. **Privacy by design:** opt-in sensing, physical microphone/camera shutoffs where possible, minimal local storage, clear consent and retention rules.
3. **Bounded autonomy:** read/report by default; execute preapproved low-risk routines; request permission for purchases, deployments, new devices, invasive monitoring or risky operations.
4. **Safety outside the LLM:** deterministic rules, hardware interlocks, emergency stops and fail-safe behavior for anything that moves, heats, locks or uses power.
5. **Auditable:** log who/what triggered actions, outcomes, uncertainty and recovery steps. Never silently repeat failing device commands forever.

## Team boundaries
| Entity | Function | Relationship |
| --- | --- | --- |
| **Alden** | Household operations and connected appliances | Owns household workflows |
| **Mercer** | Engineering and development | Can investigate problems at Alden's request; deployments require approval |
| **Wobble** | Independent companion robot | A household resident, not an employee or household actuator |
| **Owner** | Final authority | Grants permissions and approves consequential actions |

Alden can report a recurring vacuum navigation failure to Mercer. Mercer can prepare a proposed fix. Neither should deploy a physical modification without approval.

## Concept architecture
```text
Voice / Dashboard / Notifications
               |
   Alden coordinator + scheduler
               |
 Policy / approval / audit gateway
               |
 Local state + event bus + inventory
               |
   Device-specific local adapters
               |
Independent device safety controllers
```

Deterministic scheduling and sensors handle routine work. LLM reasoning may interpret events, prioritize tasks, propose solutions and draft briefings, **not** directly drive hazardous equipment.

## Early milestones
- [ ] Inventory actual household devices, their APIs, floors, connectivity and failure modes.
- [ ] Define access policies, exception categories, approvals and audit event schema.
- [ ] Build a mock home simulation with robots, maintenance schedules and a local dashboard.
- [ ] Integrate one device **status-only**, validate disconnection recovery.
- [ ] Enable one owner-approved low-risk routine with logging and limits.
- [ ] Connect food planning and inventory through explicit shared interfaces.
- [ ] Define secure, asynchronous Alden ↔ Mercer requests.

## Proposed structure
```text
docs/         Requirements, decisions, security and protocol design
integrations/ Device adapters
services/     Event, scheduler and coordinator services
policies/     Capabilities and approvals
ui/           Dashboard and notifications
tests/        Simulated devices and failure injection
deploy/       Owner-controlled local installation
```

## Future scenario
> Alden: “The upstairs vacuum has stalled repeatedly. I've stopped retries and filed a diagnostic request with Mercer. The kitchen and other cleaning schedules are unaffected.”

*No cloud-bound robot army. No unapproved chef-bot flamethrower.*
