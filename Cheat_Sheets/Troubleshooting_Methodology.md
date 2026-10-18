# Cheat Sheet: CompTIA Troubleshooting Methodology

> A professional framework for diagnosing and documenting faults. CompTIA explicitly excludes the methodology itself from the V15 exam; practical troubleshooting skills remain in scope.

Source: [CompTIA Core 1 objectives, document version 4.0, page 3](https://lecbyo.files.cmp.optimizely.com/download/34be017cb73211ef8985a6f347fbf652).

## Six Steps in Practice

| Step | Action | Useful record |
| --- | --- | --- |
| 1 | Identify the problem | User report, symptoms, scope, recent changes and baseline |
| 2 | Develop a likely explanation | Plausible causes, starting with simple ones; research when needed |
| 3 | Test the explanation | One controlled test at a time; results that support or rule out the cause |
| 4 | Plan the repair and implement it | Risk, approval, backup/rollback, communication and the applied change |
| 5 | Verify full operation and prevent recurrence | Original symptom resolved; related functions checked; preventive action |
| 6 | Document findings and outcome | Evidence, cause, actions, results and follow-up |

The implementation belongs with step 4; verification and prevention belong in step 5.

## Applying the Framework

1. Ask clarifying questions and reproduce the fault when safe. Protect data and preserve evidence where incident procedures require it.
2. Check obvious causes before replacing components. A cable or configuration error can resemble hardware failure.
3. Change one variable at a time. If a theory fails, revise it or escalate when the next test exceeds your access, tools or responsibility.
4. Obtain required approval before the repair. Confirm the target, create a recovery point where appropriate and communicate downtime.
5. Repeat the original failing task and check related functionality. A successful command alone does not prove the user's workflow works.
6. Record what was observed and verified. Keep a suspected cause labelled as suspected rather than presenting it as proven.

## Example: Client Cannot Reach a Remote Service

| Step | Example |
| --- | --- |
| Identify | Record the IP/mask/gateway; other clients work; local peer is reachable but remote service is not |
| Theory | The default gateway may be incorrect |
| Test | Compare the client settings with the approved address plan; ping local and remote targets |
| Plan and implement | With authorization, restore the documented gateway and keep the previous setting for rollback |
| Verify and prevent | Repeat remote IP, DNS and application tests; check the deployment template for the incorrect value |
| Document | Record the wrong value, corrected value, tests and user confirmation |

An APIPA address points to an incomplete DHCP exchange; it does not prove that the DHCP server itself is broken. Check link, VLAN, scope, DHCP service and client settings as appropriate. Do not restart shared services without authorization and impact assessment.

See [hardware/network troubleshooting](../Core_1/1.5_Hardware_and_Network_Troubleshooting.md), [software troubleshooting](../Core_2/2.3_Software_Troubleshooting.md), and [Lab 02](../Labs/Lab_02_Network_Simulation.md).
