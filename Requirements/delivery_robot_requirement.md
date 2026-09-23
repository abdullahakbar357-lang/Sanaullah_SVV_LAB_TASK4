# Autonomous Delivery Robot — Requirements

## Functional and Behavioral Requirements

| Req. ID | Requirement |
|---|---|
| R1 | The robot shall remain in the IDLE state when it is powered on and no delivery request has been received. |
| R2 | When a delivery request is received while the robot is IDLE, the robot shall transition to NAVIGATING. |
| R3 | When the robot is NAVIGATING and detects an obstacle, it shall transition to AVOIDING_OBSTACLE. |
| R4 | After successfully avoiding an obstacle, the robot shall transition from AVOIDING_OBSTACLE back to NAVIGATING. |
| R5 | When the robot reaches the destination while NAVIGATING, it shall transition to DELIVERING. |
| R6 | After successful package delivery, the robot shall transition from DELIVERING to RETURNING. |
| R7 | When the robot reaches the warehouse while RETURNING, it shall transition to IDLE. |
| R8 | If the battery becomes critically low while the robot is NAVIGATING, the robot shall stop the delivery journey and transition to RETURNING. |
| R9 | The robot shall not transition directly from IDLE to DELIVERING without first receiving a delivery request and navigating to the destination. |
| R10 | The robot shall not transition from AVOIDING_OBSTACLE directly to DELIVERING; it shall first return to NAVIGATING and reach the destination. | 
