# studyspace-jira
StudySpace Jira-GitHub integration demo
StudySpace seat reservation feature integration test.

## Reservation Lifecycle Test Cases

| ID | Scenario | Preconditions | Steps | Expected Result |
| --- | --- | --- | --- | --- |
| RL-01 | Create reservation | Seat is available for selected time slot | 1) Open reservation flow 2) Select seat and time slot 3) Submit reservation | Reservation is created with `PENDING` status and reservation details are saved |
| RL-02 | Confirm reservation | Existing reservation in `PENDING` status | 1) Open reservation details 2) Confirm reservation | Reservation status changes to `CONFIRMED` and confirmation timestamp is recorded |
| RL-03 | Check in to reservation | Existing reservation in `CONFIRMED` status and check-in window is open | 1) Open active reservation 2) Select check in | Reservation status changes to `IN_USE` and seat is marked occupied |
| RL-04 | Complete reservation | Existing reservation in `IN_USE` status | 1) End reservation/session | Reservation status changes to `COMPLETED` and seat is released |
| RL-05 | Cancel reservation before use | Existing reservation in `PENDING` or `CONFIRMED` status | 1) Open reservation 2) Cancel reservation | Reservation status changes to `CANCELLED` and seat becomes available again |
| RL-06 | Auto-expire no-show reservation | Existing reservation in `CONFIRMED` status and check-in deadline has passed | 1) Trigger no-show scheduler/job | Reservation status changes to `EXPIRED` and seat is released |
| RL-07 | Reject invalid transition from completed reservation | Existing reservation in `COMPLETED` status | 1) Attempt to check in or cancel completed reservation | Operation is rejected and status remains `COMPLETED` |
