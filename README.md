# BPMN-Assignment-3
ex3
# Student Project Approval & Allocation System

## 1. Project Overview

The Student Project Approval & Allocation System is a BPMN-based workflow designed to manage the final-year student project approval process. It covers proposal submission, validation, coordinator screening, committee evaluation, faculty guide allocation, and student notification.

The workflow is designed using **Camunda Modeler** and follows BPMN 2.0 notation.

## 2. Objectives

* To automate the student project approval workflow.
* To validate project proposals and team rules.
* To identify duplicate or similar project topics.
* To support committee approval, revision, and rejection decisions.
* To allocate suitable faculty guides based on availability and workload.
* To handle failures, delays, and withdrawal scenarios.
* To maintain a clear record of project allocation.

## 3. Participants and Lanes

The BPMN diagram contains the following five lanes:

1. **Student / Team** – Submits the project proposal and makes corrections when required.
2. **Project Coordinator** – Screens proposals and handles exceptions.
3. **Review Committee (including HoD)** – Evaluates proposals and decides whether to approve, request revision, or reject.
4. **Faculty Guide** – Receives and accepts the guide allocation request.
5. **Project Management System** – Validates proposals, checks duplicate topics, allocates guides, records results, and sends notifications.

## 4. Happy Path Workflow

The normal workflow consists of the following steps:

1. The student team decides to submit a project proposal.
2. The student submits the proposal.
3. The system validates the proposal and team rules.
4. The project coordinator screens the proposal.
5. The system checks for duplicate or similar project topics.
6. The review committee evaluates the proposal.
7. An exclusive gateway determines the decision: approved, revise, or rejected.
8. If approved, the system checks faculty guide availability and workload.
9. The system allocates a suitable faculty guide and sends an allocation request.
10. The faculty guide accepts the request.
11. The system notifies the student and records the allocation.
12. The process ends with the project successfully allocated.

## 5. Failure Paths and Solutions

| ID  | Failure Scenario                           | Solution                                                                                 |
| --- | ------------------------------------------ | ---------------------------------------------------------------------------------------- |
| F1  | Missing proposal information               | Return the proposal for correction, allow up to two attempts, and escalate if necessary. |
| F2  | Invalid team composition                   | Notify the student team and allow team reformation or close the case.                    |
| F3  | Duplicate or plagiarised topic             | Review the similarity report and request a topic modification or reject the proposal.    |
| F4  | Missed proposal deadline                   | Use a timer event and send the late-submission request to the coordinator.               |
| F5  | Committee requests revision                | Allow a revision loop with a seven-day deadline and a maximum of two cycles.             |
| F6  | Committee rejects the proposal             | Notify the student with reasons and allow one new topic submission.                      |
| F7  | Committee review delay                     | Send reminders and escalate the delay to the Head of Department (HoD).                   |
| F8  | No suitable faculty guide available        | Perform manual allocation, appoint a co-guide or external guide, or use a waiting list.  |
| F9  | Faculty guide declines or does not respond | Find another guide and use manual allocation after three unsuccessful attempts.          |
| F10 | System or notification failure             | Retry the operation up to three times, then use manual notification and recording.       |
| F11 | Withdrawal after approval                  | Release the guide's allocated slot and restart allocation if appropriate.                |

## 6. BPMN Elements Used

* **Start Event:** Indicates the beginning of the workflow.
* **User Task:** Represents activities performed by students, coordinators, committee members, or faculty guides.
* **Service Task:** Represents automated activities performed by the system.
* **Business Rule Task:** Checks guide availability and workload using decision rules.
* **Send Task:** Sends notifications or allocation requests.
* **Exclusive Gateway (XOR):** Routes the process based on a decision.
* **Timer Boundary Event:** Handles deadlines and delays.
* **Error Boundary Event:** Handles system or service errors.
* **Message Boundary Event:** Handles withdrawal or other incoming messages.
* **End Event:** Indicates successful completion, rejection, withdrawal, or closure.

## 7. Tools and Technologies

* Camunda Modeler
* BPMN 2.0
* DMN decision tables, where required for guide allocation
* GitHub for version control and project submission

## 8. Expected Outcome

The workflow provides a structured representation of the student project approval process. It makes responsibilities clear, supports approval and rejection decisions, and defines recovery procedures for common failures.

The successful outcome is reached when a suitable faculty guide accepts the allocation, the system records the allocation, and the student team is notified.

Other possible outcomes include proposal rejection, invalid team closure, missed deadlines, or withdrawal.

## 9. Conclusion

The Student Project Approval & Allocation System demonstrates how BPMN can represent a real-world academic workflow. It models the normal approval process as well as exceptions such as incomplete proposals, duplicate topics, committee delays, guide unavailability, system errors, and withdrawal.

By using appropriate tasks, gateways, timers, and boundary events, the model improves workflow clarity and provides a foundation for future automation using Camunda.

## 10. Project File

* `Student_Project_Approval.bpmn` – BPMN workflow diagram.
* `README.md` – Project description, workflow explanation, BPMN elements, and failure-path register.
