### Understanding Note-Taking

During a penetration test, some activities may not be permitted. We have to be very clear about the _Rules of Engagement_ (RoE)[3](https://portal.offsec.com/courses/pen-200-44065/learning/report-writing-for-penetration-testers-38648/understanding-note-taking-38712/penetration-testing-deliverables-38667#fn-local_id_1588-3) under which the testing is done. When conducting red team testing, a person will often be assigned the role of "referee" to ensure that the rules of engagement are observed.

We need to take a structured approach to note-taking that is both concise and precise. There are an uncountable number of ways in which we might organize our notes, and it would be futile to attempt to provide a one-size-fits all set of recommendations. Nevertheless, here are some principles that often useful to consider:

- Rather than taking a few general notes assuming that we'll remember how to perform certain actions next time, we should record exactly what we did.
- This means that every command that we type, every line of code that we modify, and even anywhere we click in the GUI should be recorded so that we can reproduce our actions.
- Even if we've taken a lot of notes, if looking at them later doesn't help us remember exactly what happened during the assessment, then they won't be particularly useful to us.
- The notes need to be structured and sufficiently detailed to remove any ambiguity.
- To write a convincing and substantiated technical report later, we need to provide sufficient technical details within our notes.
- If the notes are not written coherently, it will be difficult for someone else to repeat the test and get the same results.

- **Application Name**: This is important in a multi-application test, and a good habit to get into. The application names also lends itself to building a natural folder and file structure quite nicely.
- **URL**: This is the exact URL that would be used to locate the vulnerability that we've detected.
- **Request Type**: This represents both the type of request (i.e: GET, POST, OPTIONS, etc) that was made, as well as any manual changes we made to it. For example, we might intercept a POST request message and change the username or password before forwarding it on.
- **Issue Detail**: This is the overview of the vulnerability that will be triggered by our actions. For example, we may point to a CVE describing the vulnerability if one exists, and/or explain the impact we observe. We may categorize the impact as denial of service, remote code execution, privilege escalation, and so on.
- **Proof of Concept Payload**: This is a string or code block that will trigger the vulnerability. This is the most important part of the note, as it is what will drive the issue home and allow it to be replicated. It should list all of the necessary preconditions, and provide the exact code or commands that would need to be used to trigger the vulnerability again.
### Writing Effective Technical Reports
To properly prepare a report for the client, we must understand two things:
1. The purpose of the report.
2. How we can deliver the information we've collected in a way that the audience can understand.
#### Tailor the Content
We must deliver skill-appropriate content for all the readers of our report. It may be read by executives, the heads of security, and by technical members of the security team. This means we want to not only provide a simple overview of the issues for the executives, but we will also want to provide sufficient technical detail for the more technical readers.
#### Executive Summary
The first section of the report should be an Executive Summary. This enables senior management to understand the scope and outcomes of the testing at a sufficient level to understand the value of the test, and to approve remediation. We start with the quick bite-sized pieces of information that provide the big picture, and follow that up with the full Executive Summary.

```
Executive Summary:

- Scope: https://kali.org/login.php
- Timeframe: Jan 3 - 5, 2022
- OWASP/PCI Testing methodology was used
- Social engineering and DoS testing were not in scope
- No testing accounts were given; testing was black box from an external IP address
- All tests were run from 192.168.1.2
```


We'll consider three potential states with regard to extenuating circumstances:
- **Positive Outcome**: "There were no limitations or extenuating circumstances in the engagement. The time allocated was sufficient to thoroughly test the environment."
- **Neutral Outcome**: "There were no credentials allocated to the tester in the first two days of the test. However, the attack surface was much smaller than anticipated. Therefore, this did not have an impact on the overall test. OffSec recommends that communication of credentials occurs immediately before the engagement begins for future contracts, so that we can provide as much testing as possible within the allotted time."
- **Negative Outcome**: "There was not enough time allocated to this engagement to conduct a thorough review of the application, and the scope became much larger than expected. It is recommended that more time is allocated to future engagements to provide more comprehensive coverage."