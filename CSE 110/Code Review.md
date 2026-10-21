Testing has its limitations:
- we can't get all the possible errors, and it's costly to verify.
- we don't know code structure and design
- Does UI look like how it's supposed to look?

That's why we need to review code itself, systemic reading or examination
- focus on what can't be tested
- at least in pairs, often asynchronous
- at least one is non-author
- promotes learning and knowledge transfer
- bus factor - number of people who knows the code, needs to be >= 2, so that if one gets hit by a bus, the others can still know the code
- good for new devs

Used to do a checklist, too expensive

Nowadays do change-based code review, every change gets reviewed

Google Process
1. create a change
2. authors preview results of static analyzers
3. reviews write comments, unresolved comments must be addressed
4. author addresses feedback
5. reviewer approves with LGTM

Median Google developer makes 3 commits each week, 4 reviews per week, around 4 hours per change

Recommendation: <=200 lines of code / hour when reviewing code, which is 1 line per 18 seconds, or 3 lines per minute.

Be nice/patient to errors other people makes, use we not you, avoid blaming specific people

