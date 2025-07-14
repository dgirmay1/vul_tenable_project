# Official [Cyber Range](http://joshmadakor.tech/cyber-range) Project

# Vulnerability Management Program Implementation

In this project, I simulate the implementation of a comprehensive vulnerability management program, from inception to completion.

_**Inception State:**_ the organization has no existing policy or vulnerability management practices in place.

_**Completion State:**_ a formal policy is enacted, stakeholder buy-in is secured, and a full cycle of organization-wide vulnerability remediation is successfully completed.

---

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/cfc5dbcf-3fcb-4a71-9c13-2a49f8bab3e6">

# Technology Utilized
- Tenable (enterprise vulnerability management platform)
- Azure Virtual Machines (Nessus scan engine + scan targets)
- PowerShell & BASH (remediation scripts)

---


# Table of Contents

- [Vulnerability Management Policy Draft Creation](#vulnerability-management-policy-draft-creation)
- [Mock Meeting: Policy Buy-In (Stakeholders)](#step-2-mock-meeting-policy-buy-in-stakeholders)
- [Policy Finalization and Senior Leadership Sign-Off](#step-3-policy-finalization-and-senior-leadership-sign-off)
- [Mock Meeting: Initial Scan Permission (Server Team)](#step-4-mock-meeting-initial-scan-permission-server-team)
- [Initial Scan of Server Team Assets](#step-5-initial-scan-of-server-team-assets)
- [Vulnerability Assessment and Prioritization](#step-6-vulnerability-assessment-and-prioritization)
- [Distributing Remediations to Remediation Teams](#step-7-distributing-remediations-to-remediation-teams)
- [Mock Meeting: Post-Initial Discovery Scan (Server Team)](#step-8-mock-meeting-post-initial-discovery-scan-server-team)
- [Mock CAB Meeting: Implementing Remediations](#step-9-mock-cab-meeting-implementing-remediations)
- [Remediation Round 1: Outdated Wireshark Removal](#remediation-round-1-outdated-wireshark-removal)
- [Remediation Round 2: Insecure Protocols & Ciphers](#remediation-round-2-insecure-protocols--ciphers)
- [Remediation Round 3: Guest Account Group Membership](#remediation-round-3-guest-account-group-membership)
- [Remediation Round 4: Windows OS Updates](#remediation-round-4-windows-os-updates)
- [First Cycle Remediation Effort Summary](#first-cycle-remediation-effort-summary)

---

### Vulnerability Management Policy Draft Creation

This phase focuses on drafting a Vulnerability Management Policy as a starting point for stakeholder engagement. The initial draft outlines scope, responsibilities, and remediation timelines, and may be adjusted based on feedback from relevant departments to ensure practical implementation before final approval by upper management.  
[Draft Policy](https://docs.google.com/document/d/1dC01jKli9VEP_hpOa5Q0KwV9FP9t056P-utvP_RyD98/edit?usp=sharing) 

---

### Step 2) Mock Meeting: Policy Buy-In (Stakeholders)

Context: This fictional conversation demonstrates how a vulnerability management professional collaborates with the server team to present the draft Vulnerability Management Policy and adjust initial remediation timelines based on real-world capacity and feedback.

Participants:

Priya Sharma — Vulnerability Management Lead

Alex Chen — Server Team Lead

Transcript
Priya: Good morning, Alex. Thanks for making time to discuss the draft Vulnerability Management Policy.

Alex: Good morning, Priya. No problem always glad to help shape this from the start.

Priya: I wanted to walk through the proposed remediation timelines. For now, the draft sets a 48-hour window for addressing critical vulnerabilities. Does that feel achievable for your team?

Alex: Honestly, with our current staffing and workload, that’s going to be challenging. Some of our systems are quite complex, and urgent patches often require thorough testing to avoid downtime.

Priya: That makes sense we definitely don’t want to rush changes that could impact availability. Would extending the critical window to one week be more realistic for now?

Alex: I think a one-week timeline for criticals would be manageable to start with. We’d still prioritize the most severe issues, but it gives us enough time for proper testing and deployment.

Priya: Perfect. For any zero-day vulnerabilities that pose an immediate risk, we’d still aim to patch those within 48 hours or sooner if possible.

Alex: That’s reasonable. Having that flexibility helps the team plan better.

Priya: Great. We’ll also include an adjustment period for everyone to get familiar with the new policy. I’m proposing a six-month transition window where we monitor how teams are meeting the timelines and make any needed tweaks.

Alex: That’s appreciated. It gives us time to build out our patching workflows and allocate resources where needed.

Priya: Absolutely. We’re all on the same page the goal is to improve security without putting too much strain on operations.

Alex: Agreed. Thanks for including us early in the process. It makes a big difference when we feel like we have input.

Priya: Of course collaboration is key. I’ll incorporate your feedback and share the revised draft later this week.

Alex: Sounds good. Thanks again, Priya. Looking forward to working together on this.

Priya: Likewise, Alex. Have a great rest of your day!

---

### Step 3) Policy Finalization and Senior Leadership Sign-Off

After gathering feedback from the server team, the policy is revised, addressing aggressive remediation timelines. With final approval from upper management, the policy now guides the program, ensuring compliance and reference for pushback resolution.  
[Finalized Policy](https://docs.google.com/document/d/1OhpHJYpMJHIrTf64UKz6qsTzpTWhPauQJU-IpSzWfCI/edit?usp=sharing)

---

### Step 4) Mock Meeting: Initial Scan Permission (Server Team)

Context: This fictional scenario demonstrates how a vulnerability management team works collaboratively with the server team to initiate scheduled, credentialed scans. The conversation covers addressing security concerns, minimizing operational impact, and agreeing on secure access methods.

Participants:

Priya Sharma — Vulnerability Management Lead

Alex Chen — Server Team Lead

Transcript
Priya: Good morning, Alex. I appreciate you meeting today to go over our initial scanning plan.

Alex: Good morning, Priya. No problem I heard you’re ready to get started?

Priya: Yes now that our Vulnerability Management Policy is approved, we’re ready to begin scheduled credentialed scans of the server environment.

Alex: Sounds good. What’s involved, and how can we help?

Priya: We’re planning to run weekly scans across the server infrastructure. We estimate it will take about 4 to 6 hours to cover all 200 assets. To get the most accurate results, we’ll need administrative credentials so the scan engine can log into each target and perform a deeper assessment.

Alex: Hold on can you clarify what scanning actually entails? I’m a bit concerned about the impact on server performance. Also, you’re asking for admin credentials to all 200 machines that feels risky.

Priya: Those are completely valid concerns. The scan engine will send controlled traffic to the servers to check for vulnerabilities for example, it will verify registry keys, check for outdated software, and flag any insecure protocols or cipher suites. The scans won’t take systems offline, but we can monitor performance to be sure.

Alex: Okay, that makes sense. As long as we’re sure the scans won’t disrupt services.

Priya: To be extra cautious, let’s start by scanning a single server first and monitor the resource utilization closely. If everything looks good, we can expand gradually.

Alex: I like that approach. And about the credentials is there a way to keep that secure?

Priya: Definitely. Would you be able to set up an account in Active Directory specifically for this? You can keep it disabled until the scan window, then enable it while we scan, and disable it again afterward. It’s a just-in-time access approach to minimize risk.

Alex: That works. I’ll ask Susan to get started on automating the account provisioning so it’s easy to manage.

Priya: Perfect. Once the test scan is done, we can review the results together and confirm the broader schedule.

Alex: Sounds good. I’ll get back to you once the AD credentials are ready. Thanks for working with us on this.

Priya: Absolutely appreciate the collaboration. Talk soon!

Alex: See you later, Priya.

---

### Step 5) Initial Scan of Server Team Assets

In this phase, an insecure Windows Server is provisioned to simulate the server team's environment. After creating vulnerabilities, an authenticated scan is performed, and the results are exported for future remediation steps.  

[Scan 1 - Initial Scan](https://drive.google.com/file/d/1oub7ffdHydHge33j301xF_MZahzgGp5i/view?usp=sharing)




---

### Step 6) Vulnerability Assessment and Prioritization

I assessed vulnerabilities and established a remediation prioritization strategy based on ease of remediation and impact. The following priorities were set:

1. Third Party Software Removal (Wireshark)
2. Windows OS Secure Configuration (Protocols & Ciphers)
3. Windows OS Secure Configuration (Guest Account Group Membership)
4. Windows OS Updates

---

### Step 7) Distributing Remediations to Remediation Teams

The server team received remediation scripts and scan reports to address key vulnerabilities. This streamlined their efforts and prepared them for a follow-up review.  

S**Subject:** Vulnerability Remediation Scripts for Testing and Deployment

**Hi [Team],**

Based on our initial vulnerability scan and assessment, I have created a set of scripts to help you tackle the initial remediation efforts. These scripts target key vulnerabilities and can be easily integrated into your deployment platform (e.g., SCCM). Please test them before deploying to production.

### Vulnerabilities and Remediations:
1. [**Third-Party Software Removal (Wireshark)**](https://github.com/dgirmay1/remediation-/blob/main/remediation-wireshark-uninstall.ps1)
2. [**Windows OS Secure Configuration (Insecure Protocols)**](https://github.com/dgirmay1/remediation-/blob/main/toggle-protocols.ps1)
3. [**Windows OS Secure Configuration (Insecure Ciphersuites)**](https://github.com/dgirmay1/remediation-/blob/main/toggle-cipher-suites.ps1)
4. [**Windows OS Secure Configuration (Guest Account Group Membership)**](https://github.com/dgirmay1/remediation-/blob/main/toggle-guest-local-administrators.ps1)

Let me know if you have any questions or need any adjustments!

Best regards,

**Dogol Girmay, Security Analyst**<br/>
**Governance, Risk, and Compliance**

---

### Step 8) Mock Meeting: Post-Initial Discovery Scan (Server Team)

The server team reviewed vulnerability scan results, identifying outdated software, insecure accounts, and deprecated protocols. The remediation packages were prepared for submission to the Change Control Board (CAB). 

Context:
This fictional scenario shows how the vulnerability management team reviews initial scan results with the server team, discusses key findings like outdated software, insecure accounts, and deprecated protocols, and agrees on next steps for remediation and Change Control Board (CAB) submission.

Participants:

Priya Sharma — Vulnerability Management Lead

Alex Chen — Server Team Lead

Transcript
Priya: Good morning, Alex. How’s your Monday going so far?

Alex: Not bad for a Monday — and you?

Priya: Still alive, so I can’t complain! Before we dive into the vulnerabilities, how did the scan go on your end? Any outages or resource spikes?

Alex: The scan went smoothly. We were monitoring everything, and aside from seeing a lot of open connections, you’d barely know it was happening.

Priya: That’s great news. I expected as much, but we’ll keep an eye on it for future scans. Now, do you mind if I walk you through the vulnerability findings?

Alex: Absolutely — go ahead.

Priya: Perfect. I’ll share my screen. The majority of these findings relate to Wireshark being installed — it’s significantly outdated. You can see all these detections are basically old Wireshark versions that need to go.

Alex: Makes sense.

Priya: Another interesting one: the local guest account on several servers is actually part of the local Administrators group. That’s a pretty big risk — I’m not sure why that is, but we’ll want to fix it.

Alex: Agreed — that shouldn’t be the case.

Priya: A few other findings, like the Microsoft Edge Chromium version, may resolve automatically with Windows Updates. Same for some self-signed certificates — those aren’t really a concern in this context.

Alex: Got it.

Priya: The other piece we should address are the medium-strength cipher suites and the use of deprecated TLS 1.0 and 1.1 protocols. These should be disabled as they’re no longer secure.

Alex: Understood. Do you foresee any issues removing those cipher suites and protocols?

Priya: I don’t expect any major issues, but we’ll definitely run it through the next Change Control Board to be safe. Uninstalling Wireshark and removing the guest account should also be straightforward — they really shouldn’t be on these servers in the first place.

Alex: Agreed — I’ll check with our CIS admins about the guest account permissions.

Priya: Great. I’ll go ahead and build out remediation packages for these issues to make things easier for your team.

Alex: Perfect. And as for Windows Updates, we already have our patch management in place, so I’m not worried about those items — they should be handled automatically this week.

Priya: Excellent. I’ll finalize the remediation plan and send it over before the next CAB meeting so we’re all prepared.

Alex: Sounds good. Appreciate you pulling this together.

Priya: Anytime. Talk to you soon, Alex.

Alex: Talk to you soon, Priya. Thanks again.

---

### Step 9) Mock CAB Meeting: Implementing Remediations

The Change Control Board (CAB) reviewed and approved the plan to remove insecure protocols and cipher suites. The plan included a rollback script and a tiered deployment approach.  

Context:
In this fictional scenario, the Change Control Board (CAB) reviews and approves a remediation plan to remove insecure protocols and cipher suites. The plan outlines the technical solution, includes a tiered deployment approach, and incorporates a rollback plan to minimize risk.

Participants:

Josh Patel — Risk Management Team

Jimmy Lee — Infrastructure Team

CAB Members

Transcript
CAB Chair: Next on the agenda are a couple of vulnerability remediations for the server team — specifically, the removal of insecure protocols and insecure cipher suites. It looks like Josh from Risk is working with Jimmy from Infrastructure on this. Jimmy, could you walk us through the technical side of the change?

Jimmy: Normally I would, but do you mind if Josh explains? He actually built the solution for us, and we’re still getting familiar with the process.

Josh: Sure, happy to. So, the issue is that having insecure cipher suites and protocols on our servers means the systems are technically capable of negotiating outdated, deprecated algorithms. If a server tries to connect and only supports those insecure methods, there’s a risk the system will accept them.

These settings are managed through the Windows Registry. Our fix is simple: we developed a PowerShell script that disables all insecure protocols and cipher suites, and enables only secure, up-to-date ones that align with current standards.

CAB Member: That sounds straightforward. What happens if something breaks — do we have a rollback plan?

Josh: Absolutely. We have a tiered deployment plan — starting with a small pilot group, then moving to pre-production, and finally rolling out to production. On top of that, we’ve built automated rollback scripts for each remediation. So if any unexpected issue arises, the original registry settings can be restored quickly.

CAB Member: Great. So it’s just registry updates — I don’t see that causing major issues, but it’s good to have a safety net.

Josh: Exactly. It’s a simple change, but we’re taking every precaution.

CAB Chair: Any other questions from the team?

CAB Members: (No further questions.)

CAB Chair: Perfect. That wraps up this item for this week’s CAB meeting. Thanks, everyone — see you next week.

Josh: Thanks, everyone.

Jimmy: See you all next week.

---
### Step 10 ) Remediation Effort

#### Remediation Round 1: Outdated Wireshark Removal

The server team used a PowerShell script to remove outdated Wireshark. A follow-up scan confirmed successful remediation.  
[Wireshark Removal Script](https://github.com/dgirmay1/remediation-/blob/main/remediation-wireshark-uninstall.ps1)  

<img width="634" alt="image" src="https://github.com/user-attachments/assets/7b4f9ab2-d230-4458-ac0f-c0ff070ae79a">

[Scan 2 - Third Party Software Removal](https://drive.google.com/file/d/1sPxqr4qjbzI3A00--axgGueiot97BxLI/view?usp=sharing)


#### Remediation Round 2: Insecure Protocols & Ciphers

The server team used PowerShell scripts to remediate insecure protocols and cipher suites. A follow-up scan verified successful remediation, and the results were saved for reference.  
[PowerShell: Insecure Protocols Remediation](https://github.com/dgirmay1/remediation-/blob/main/toggle-protocols.ps1) and
[PowerShell: Insecure Ciphers Remediation](https://github.com/dgirmay1/remediation-/blob/main/toggle-cipher-suites.ps1)

<img width="630" alt="image" src="https://github.com/user-attachments/assets/0e96120d-8ec9-4f76-8e42-79c752200010">

[Scan 3 - Ciphersuites and Protocols](https://drive.google.com/file/d/1tPpdydOqS-w9X57IHAaWZJx-lg9l3Ai5/view?usp=sharing)


#### Remediation Round 3: Guest Account Group Membership

The server team removed the guest account from the administrator group. A new scan confirmed remediation, and the results were exported for comparison.  
[PowerShell: Guest Account Group Membership Remediation](https://github.com/dgirmay1/remediation-/blob/main/toggle-guest-local-administrators.ps1)  

<img width="627" alt="image" src="https://github.com/user-attachments/assets/870a3eac-3398-44fe-91c0-96f3c2578df4">

[Scan 4 - Guest Account Group Removal](https://drive.google.com/file/d/1u4tq9ULQgIOUpuA0nlyvbZRdWF04YaWj/view?usp=sharing)


#### Remediation Round 4: Windows OS Updates

Windows updates were re-enabled and applied until the system was fully up to date. A final scan verified the changes  

<img width="627" alt="image" src="https://github.com/user-attachments/assets/870a3eac-3398-44fe-91c0-96f3c2578df4">

[Scan 5 - Post Windows Updates](https://drive.google.com/file/d/1hdoNuj7kDC3RJonDDmjw0fPb0vJVj2Sy/view?usp=sharing)

---

### First Cycle Remediation Effort Summary

The remediation process reduced total vulnerabilities by 80%, from 30 to 6. Critical vulnerabilities were resolved by the second scan (100%), and high vulnerabilities dropped by 90%. Mediums were reduced by 76%. In an actual production environment, asset criticality would further guide future remediation efforts.  

<img width="1920" alt="image" src="https://github.com/user-attachments/assets/51f0aae8-7f36-4d90-b29f-5257e57155f9">

[Remediation Data](https://docs.google.com/spreadsheets/d/1FTtFfZYmFsNLU6pm8nTzsKyKE-d2ftXzX_DPwcnFNfA/edit?gid=0#gid=0)

---

### On-going Vulnerability Management (Maintenance Mode)

After completing the initial remediation cycle, the vulnerability management program transitions into **Maintenance Mode**. This phase ensures that vulnerabilities continue to be managed proactively, keeping systems secure over time. Regular scans, continuous monitoring, and timely remediation are crucial components of this phase. (See [Finalized Policy](https://docs.google.com/document/d/1OhpHJYpMJHIrTf64UKz6qsTzpTWhPauQJU-IpSzWfCI/edit?usp=sharing) for scanning and remediation cadence requirements.)

Key activities in Maintenance Mode include:
- **Scheduled Vulnerability Scans**: Perform regular scans (e.g., weekly or monthly) to detect new vulnerabilities as systems evolve.
- **Patch Management**: Continuously apply security patches and updates, ensuring no critical vulnerabilities remain unpatched.
- **Remediation Follow-ups**: Address newly identified vulnerabilities promptly, prioritizing based on risk and impact.
- **Policy Review and Updates**: Periodically review the Vulnerability Management Policy to ensure it aligns with the latest security best practices and organizational needs.
- **Audit and Compliance**: Conduct internal audits to ensure compliance with the vulnerability management policy and external regulations.
- **Ongoing Communication with Stakeholders**: Maintain open communication with teams responsible for remediation, ensuring efficient coordination.

By maintaining an active vulnerability management process, organizations can stay ahead of emerging threats and ensure long-term security resilience.
