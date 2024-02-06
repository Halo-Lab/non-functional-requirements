# Technical Stack

This chapter is dedicated to the technical stack of the Front-End part of web applications. We will review high-level problems such as choosing a programming language with static or dynamic typing, selecting Front-End frameworks and metaframeworks, and infrastructure. Low-level tools like state managers, form managing libraries, etc., are omitted because this document is designed to assist developers rather than restrict them.

Table of content:

1. [Factors to Consider When Choosing Tech Stack](#factors-to-consider-when-choosing-tech-stack)
2. [JavaScript vs. TypeScript](#javascript-vs-typescript)
3. [Front-End Frameworks and Metaframeworks](#front-end-frameworks-and-metaframeworks)
4. [Infrastructure](#infrastructure)

## Factors to Consider When Choosing Tech Stack

When selecting a project tech stack, it's crucial to consider the project's functional requirements, business area and goals, the current job market situation for developers, and the skills of available team members.

### Project's functional requirements, business area and goals

Software for spacecraft must prioritize maximal correctness, as even a small mistake could divert a very expensive spacecraft to Saturn instead of Jupiter. Software for heart rhythm devices must be robust to ensure patients that their hearts will beat reliably under any conditions. On the other hand, software for marketing websites should enable the use of visual effects such as animations and videos while preserving web page performance. This generalization illustrates how functional requirements and the specific business area can significantly influence the choice of tech stack.

For example, when developing a banking application, enterprise-level CRM, or any other project where correctness is crucial, you should consider using TypeScript in strict mode and incorporate both manual and automatic testing. On the other hand, if you're developing a content site that generates revenue from ad banner displays, you may be more tolerant of some mistakes but need to ensure your site remains responsive under high load. In this case, paying attention to infrastructure and being okay with dynamic typing may be more suitable.