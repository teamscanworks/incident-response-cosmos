# Incident Response for Cosmos networks

_**Disclaimer:** This guidance is highly opinionated and currently a best-effort approach to help Cosmos teams with their incident response processes. The current document is expected to be modified and improved in the future with the help and feedback of other Cosmos teams and community members_


## Introduction

> **Confidential.** Do not share your incident response plan with anyone outside of your circle of trust

This document offers recommendations and guidance for core teams to help them deal with security incidents and control their damage.

### Definitions

- **Incident response plan (IR):** TODO
- **Playbook:** TODO
- **War room:** TODO
- **Circle of trust:** TODO

### Roles

> It's recommended to define substitutes in case the primary team members are not available at the moment of the incident. Having team member substitutes spread on different timezones increases the availabily guarantees. 

- Lead Core Dev
  - TODO
- Secondary Core Dev
  - TODO
- Web UI Lead
  - Update and disable website/app
- Facilitator
	- Multi-sig herder if applicable
- Ops
	- Communications (internal and external)
	- War room set up
	- Record minutes and timeline
- External
	- Validators
	- Auditors
  
 ### Contact details record
 
 #### Internal contacts

| Name    |    Function        | Phones       | signal    | telegram  | other     |
|---------|--------------------|--------------|-----------|-----------|-----------|
| Alice   |   Lead Core Dev    | xxx-xxx-xxxx | something | something | something |
| Bob     |   Facilitator      | yyy-yyy-yyyy | something | something | something |


#### External contacts

| Name                | Function              | Email              | Other         |   Security page   |
|---------------------|-----------------------|--------------------|---------------|-------------------|
| Super Security      | Audit Firm            | name@email.com     | something     |       something   |
| Mallory             | Trusted Validator     | name@email.com     | something     |       n/a         |
| Protocol X          | Protocol dependency   | security@email.com | something     |       something   |
| Infra Partner Z     | Protocol infra        | security@email.com | something     |       something   |

 
 
## Preparation

- [ ] Define internal communication toolkit
  - Example: Signal/Zoom (primary), Slack/Meet (backup)
- [ ] Define external communication toolkit
  - Example: Discord (primary), Telegram (backup)
- [ ] Assign roles in your team
- [ ] Define your circle of trust (internal roles + selected external participants e.g. past auditors)
- [ ] Document and keep updated contact details of internal roles and external participants
- [ ] Consider what circumstances would require emergency actions in your protocol
- [ ] Create potential hack scenarios
  - Example: [How to Hack the Yield Protocol](https://docs.yieldprotocol.com/#/operations/how_to_hack)
- [ ] Define sensitive logic and behaviour that would be considered an anomaly an integrate with an off-chain monitoring solution
  - Consider integration with a monitoring solution e.g [Range](https://www.range.org/)
- [ ] Prepare mitigation scripts
- [ ] Implement circuit breakers for critical functionality
  - Example: Use [x/circuit](https://github.com/cosmos/cosmos-sdk/tree/main/x/circuit) module
- [ ] Understand how long it would take to patch a vulnerability in a given component
- [ ] Describe critical dependencies of your system and define how you will keep track on vulnerabilities and disclosure of those systems
  - Inventory of critical dependencies
  - Consider assigning one team member to be fully responsible of this task
- [ ] Drill. Employee training and practice of mock incidents
- [ ] Keep the Incident Response plan private exclusively to assigned roles

## Playbook

> This is a playbook for chain-related incidents. Even if there may be overlaps, other security issues like social media account take-overs or phishing attacks should have their own specific playbooks.

## Actions

### Immediately After

- [ ] Identify vulnerability
- [ ] Escalate and set up the war room with internal members
	- [ ] Contact security partners and other assigned external roles (e.g. trusted validators/contributors)
  - [ ] Add trusted external partners within your circle of trust to the war room
- [ ] Determine the full extent of the compromise
	- How the system was compromised
	- What is the breach timeline of the attack or bug
  - Initial root cause analysis
- [ ] Emergency mitigations. Pause contracts or module functionality when relevant
- [ ] Execute an immediate patch or emergency action if relevant
	- e.g. frontrun attacker
	- e.g. drain a compromised pool before the attacker
- [ ] Monitor the effectiveness of the emergency remediation action
- [ ] Review related application logic to identify knock-on vulnerabilities
- [ ] Update UI e.g. disable withdrawals via the UI
- [ ] Contact other protocols and projects that may be affected by the same vulnerability
- [ ] Contact upstream maintainers if the vulnerability is at a lower level of the stack
	- Cosmos SDK
	- CometBFT
  - IBC
  - etc

### After

- [ ] Post message Discord, Twitter and other social media channels
- [ ] Prepare long-term remediation actions (e.g. patches)
	- Reviewed by validators and past auditors in your circle of trust
	- Consider Code4rena contest (optional)
- [ ] Deploy long-term mitigation e.g. patches
- [ ] Monitor the correct functioning of the patches
- [ ] Draft Post mortem 
  - To be performed by Ops member
- [ ] Review Post mortem
  - To be perfomed by lead and secondary devs, past auditors
- [ ] Publish post mortem in social media channels
  - Medium, Discord, Twitter, etc
- [ ] Retrospective
	- What we did well, what not
	- How did we handle the incident?
  - What can we improve?


## Additional Resources
- [Emergency Procedures for Yearn Finance](https://github.com/yearn/yearn-devdocs/blob/master/docs/developers/v2/EMERGENCY.md)
- [Nascent Incident Response Plan](https://github.com/nascentxyz/simple-security-toolkit/blob/main/incident-response-plan-template.md)
- [Incident Response Recommendations](https://github.com/crytic/building-secure-contracts/blob/master/development-guidelines/incident_response.md)
- [Startup Boilerplate Incident Response Plan](https://github.com/magoo/Incident-Response-Plan)
- [Yield Post Mortem](https://medium.com/yield-protocol/post-mortem-of-incident-on-august-5th-2022-7bb70dbb9ada)
- [Juno Incident Response)(https://github.com/CosmosContracts/incident-response)
