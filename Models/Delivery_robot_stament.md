# Autonomous Delivery Robot — State Model

## States

### S1 — IDLE
The robot is waiting for a delivery request.

### S2 — NAVIGATING
The robot is travelling toward the delivery destination.

### S3 — AVOIDING_OBSTACLE
The robot is handling an obstacle detected during navigation.

### S4 — DELIVERING
The robot has reached the destination and is performing the package delivery.

### S5 — RETURNING
The robot is travelling back to the warehouse.

## Events and Conditions

| Event ID | Event / Condition |
|---|---|
| E1 | Delivery Request Received |
| E2 | Destination Reached |
| E3 | Delivery Successful |
| E4 | Warehouse Reached |
| E5 | Obstacle Detected |
| E6 | Obstacle Avoided |
| E7 | Critical Battery |

## State Flow

IDLE → NAVIGATING

NAVIGATING → AVOIDING_OBSTACLE

AVOIDING_OBSTACLE → NAVIGATING

NAVIGATING → DELIVERING

DELIVERING → RETURNING

RETURNING → IDLE

NAVIGATING → RETURNING
