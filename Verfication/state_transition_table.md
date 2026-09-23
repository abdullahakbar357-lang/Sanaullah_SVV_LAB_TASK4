# Autonomous Delivery Robot — State Transition Table

## State Transition Table

| Current State | Event / Condition | Next State | Requirement |
|---|---|---|---|
| IDLE | Delivery Request Received | NAVIGATING | R2 |
| NAVIGATING | Obstacle Detected | AVOIDING_OBSTACLE | R3 |
| AVOIDING_OBSTACLE | Obstacle Avoided | NAVIGATING | R4 |
| NAVIGATING | Destination Reached | DELIVERING | R5 |
| DELIVERING | Delivery Successful | RETURNING | R6 |
| RETURNING | Warehouse Reached | IDLE | R7 |
| NAVIGATING | Critical Battery | RETURNING | R8 |

## Invalid Transitions

| Current State | Invalid Next State | Reason |
|---|---|---|
| IDLE | DELIVERING | Violates R9 |
| AVOIDING_OBSTACLE | DELIVERING | Violates R10 |

# Verification Activity

## Check 1 — Invalid Transition

### IDLE → DELIVERING

This transition is invalid.

The robot must first receive a delivery request and then navigate to the destination before entering the DELIVERING state.

Requirement violated: R9.

Correct sequence:

IDLE → NAVIGATING → DELIVERING

---

## Check 2 — Missing Transition

### NAVIGATING → AVOIDING_OBSTACLE

If there is no transition from AVOIDING_OBSTACLE back to NAVIGATING, the robot cannot continue its delivery journey.

Therefore, the following transition is required:

AVOIDING_OBSTACLE → NAVIGATING

Requirement: R4.

---

## Check 3 — Obstacle During Delivery

### AVOIDING_OBSTACLE → DELIVERING

This transition is invalid.

The robot must first return to NAVIGATING after avoiding the obstacle and then reach the destination before entering DELIVERING.

Requirement violated: R10.

Correct sequence:

AVOIDING_OBSTACLE → NAVIGATING → DELIVERING

# Verification Summary

| Check | Result |
|---|---|
| IDLE → DELIVERING | Invalid |
| NAVIGATING → AVOIDING_OBSTACLE | Valid |
| AVOIDING_OBSTACLE → NAVIGATING | Required |
| AVOIDING_OBSTACLE → DELIVERING | Invalid |
| NAVIGATING → DELIVERING | Valid |
| DELIVERING → RETURNING | Valid |
| RETURNING → IDLE | Valid |
| NAVIGATING → RETURNING | Valid |
