# iGnite Release 3.1
## System Test Strategy and Plan

**Version:** Draft 0.2  
**Prepared:** 4 November 2026  
**Testing scope:** Event-trigger validation using Slack messages or AWS CloudWatch logs.

## 1. Project Purpose - Overall Project

The iGnite project introduces Twilio Segment as the Customer Data Platform to bring customer information and digital interactions together.

Release 3.1 includes changes to capture events from Vodafone websites, MyVodafone web and mobile applications, and supporting services.

**Pega interaction is not included in the current Release 3.1 scope.**

## 2. Purpose of System Testing - ST-related

System Testing will check that the correct event is triggered when a user performs an agreed action.

The ST team will perform the action in the test application and check the corresponding **Slack message or CloudWatch log**.

**ST confirms the event trigger only. It does not confirm that Segment received, processed or stored the event.**

## 3. Testing Scope - ST-related

### In Scope

| Area | What ST will check |
|---|---|
| Event triggers | The expected event is triggered after the relevant user action. |
| Event identification | The event name or identifier shown in Slack or CloudWatch matches the agreed requirement. |
| Successful actions | Events are triggered for successful actions where required. |
| Failed actions | Failure events are triggered where required, without an incorrect success event. |
| Actions that should not trigger an event | No event is observed where the agreed requirement says it should not be triggered. |
| Repeated actions | Repeated actions produce the expected number of triggers, according to the agreed requirement. |
| Application behaviour | The affected user journey continues to work after the event-handling changes. |
| Defect retesting | Fixed issues are checked again, including related event triggers. |

ST will use the Release 3.1 requirements workbook to identify the events to test. Only events confirmed for the delivered release will be included in execution.

### Out of Scope

The following activities are not part of the current ST scope:

- Segment integration, event receipt, processing or storage.
- Segment profile creation, identity merging or destination routing.
- Detailed payload or schema validation beyond the information needed to identify the event trigger.
- Pega interaction.
- Downstream database or data-storage validation.
- Performance, load and penetration testing.
- Unrelated application features or UI redesign.

### Possible Future Scope: Segment Integration

The client has requested Segment integration testing, but **it is not included in the current ST scope**.

It may be added later after agreement on access, environment readiness, responsibilities, test cases and timelines. Until then, an event observed in Slack or CloudWatch must not be reported as a successful Segment integration test.

## 4. Event Areas to Be Tested - ST-related

The following event areas will be covered where included in the approved Release 3.1 delivery:

| Event area | Examples |
|---|---|
| Login and session | Login success/failure, registration, logout and session refresh. |
| Shopping | Product selection, eligibility checks, basket actions, checkout and order completion. |
| Self-service | Account changes, preferences, payments, bills, recharge and service activation. |
| Website interactions | Page navigation, searches, promotions, forms and errors. |
| Mobile interactions | Screen navigation, application lifecycle and device-related events. |
| Notifications and links | Push-notification and deep-link actions, where supported and delivered. |

The expected event name, triggering action and log location must be agreed before testing.

## 5. Testing Approach - ST-related

For each event, the ST team will:

1. Select the test case and required test account.
2. Perform the action in the application.
3. Record the action time and an approved test reference.
4. Check the agreed Slack channel or CloudWatch log.
5. Match the observed event to the action using the event name, time and available reference.
6. Record the result and retain sanitised evidence.

### Example

| Item | Expected result |
|---|---|
| User action | Complete a successful login. |
| Expected trigger | The agreed login-success event. |
| Verification | Matching Slack message or CloudWatch log within the agreed observation period. |
| Evidence | Screenshot or log reference showing the event and time, with sensitive information removed. |

If no matching event is visible, ST will investigate with the development team. A missing Slack message or log could indicate either an event-trigger problem or a logging problem.

If the logging service is unavailable, the test will be recorded as **Blocked**, not Passed.

## 6. Test Environment, Tools and Data - ST-related

Testing will use an approved non-production environment.

Required access includes the application, relevant Slack channels or CloudWatch logs, and the agreed test-management and defect-tracking tools.

Test data will include suitable accounts for the agreed journeys, such as:

- New and existing users.
- Prepaid and postpaid customers, where applicable.
- Successful and unsuccessful actions.
- Different preference settings.
- Relevant shopping and self-service scenarios.

Use synthetic or approved masked data. Passwords, OTP values, payment details and other sensitive information must not be included in test evidence.

Web, iOS and Android testing will be performed where the delivered events apply. Device and browser versions will be agreed before execution.

## 7. Entry Criteria - ST-related

ST can begin when:

- The Release 3.1 event list and expected triggers are agreed.
- A stable application build is available.
- Test accounts and data are ready.
- Slack or CloudWatch access is available and working.
- The development team has confirmed where to find each event.
- The expected time for an event to appear has been agreed.

## 8. Execution Plan - ST-related

| Stage | Activity |
|---|---|
| Preparation | Review event requirements and prepare test cases. |
| Readiness check | Confirm build, accounts, data and logging access. |
| Initial check | Trigger a sample event and confirm it is visible. |
| Test execution | Execute the agreed event-trigger scenarios. |
| Retesting | Check fixes and repeat affected scenarios. |
| Completion | Prepare the ST summary and record outstanding issues. |

Dates and effort will be agreed once the release build and event list are confirmed.

## 9. Defect Management and Reporting - ST-related

When an event does not behave as expected, ST will record:

- The test case and expected event.
- The action performed.
- The application build and environment.
- The time and test reference.
- Expected and actual results.
- Sanitised Slack or CloudWatch evidence.

The development team will investigate and fix the issue. ST will then retest it.

Daily reporting will show tests passed, failed, blocked and not yet run, together with open defects and any access or environment issues.

## 10. Roles and Responsibilities - ST-related

| Team or role | Responsibility |
|---|---|
| ST Lead | Plan coverage, coordinate execution and report results. |
| ST Team | Perform actions, verify triggers, retain evidence and retest defects. |
| Development Team | Explain expected triggers and log locations, investigate issues and provide fixes. |
| Environment/Support Team | Maintain the test environment and logging access. |
| Project/Test Manager | Approve scope, schedule and any later addition of Segment integration testing. |

## 11. Exit Criteria - ST-related

ST can be completed when:

- All agreed event-trigger tests have been executed.
- Expected triggers have been confirmed in Slack or CloudWatch.
- No Critical or High defects remain open.
- Remaining defects and untested items have been reviewed and accepted by the responsible owners.
- The ST summary and supporting evidence are available.

These are proposed completion criteria and require project approval.

## 12. Risks and Dependencies - ST-related

| Risk or dependency | Action |
|---|---|
| Slack or CloudWatch is unavailable. | Restore access; mark affected tests as Blocked. |
| Events cannot be matched to the test action. | Agree useful timestamps and test references with developers. |
| Event names or triggers are unclear. | Confirm expected behaviour before execution. |
| Logs appear late. | Agree an observation period before testing. |
| Required accounts or journeys are unavailable. | Arrange data and support before execution. |
| Segment testing is added later. | Review scope, access, effort and schedule before accepting it. |

## 13. Deliverables and Sign-off - ST-related

ST will provide the test cases, execution results, event-trigger evidence, defect records and final ST summary.

**ST sign-off confirms only that the agreed event triggers were verified through Slack or CloudWatch. It does not confirm Segment integration or downstream processing.**

## Reference Documents

- IACC-SAD - #901_ iGnite Segment CDP Release 3.1-291026-092530.pdf - project background and solution context.
- R3.1_Digital_to_CDP_Data_Requirements_V2.xlsx - event requirements, subject to the approved Release 3.1 delivery.
- st dfa STRATEGY DOC.docx - sample structure only.

The current ST boundaries and absence of Pega interaction reflect the project clarifications supplied for this revision.
