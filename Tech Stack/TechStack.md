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

### Client's Team Preferences and Knowledge

For example, if your client's team is experienced with WordPress and the client asks you to create a headless blog with WordPress, you need to consider this solution even if you prefer another headless CMS. Your approach should be to inform the client about alternatives, but ultimately, if they believe their business needs WordPress, you are to work with it.

### Technology Landscape and Perspectives

This point can also be illustrated with an example. At the beginning of 2024, jQuery v.4 was released. However, does this mean that jQuery is a modern technology that adequately meets current business and development needs? This question is rhetorical.

When choosing a tech stack, you need to consider tools that incorporate modern approaches to development. Additionally, these tools should be popular enough, as every project requires support, and neither you nor your client should encounter difficulties in hiring developers with the appropriate skills.

## JavaScript vs. TypeScript: A Practical Perspective

The age-old debate of "egg vs. chicken" or "dynamic vs. static typing" might be fun for philosophical thought experiments, but when it comes to practical software development, choosing between JavaScript and TypeScript often boils down to **context and preferences**.

For our team, TypeScript is the default choice because it offers:

* Improved Documentation: Type annotations act as developer-facing documentation, enhancing code clarity and maintainability, especially for large projects.
* Reduced Errors: Static typing catches many potential errors at compile time, leading to a more robust and user-friendly experience.
* Enhanced Developer Tools: Better autocompletion and tooling support streamline the development process for TypeScript users.

However, JavaScript remains a valid option in certain scenarios:

* Strong Preference for Dynamic Typing: Some developers firmly favor the flexibility of dynamic typing and are adept at managing it responsibly.
* Rapid Prototyping: When speed is paramount, JavaScript's looser structure can be advantageous for quick mockups or proof-of-concepts.

Even if you primarily use JavaScript, consider leveraging tools like:

* Prop Types: Provide optional type checking for React components, offering some static typing benefits.
* JSDoc annotations: [Allow for documentation and basic type hints within JavaScript code](https://ricostacruz.com/posts/typescript-jsdoc).

Ultimately, the choice between JavaScript and TypeScript depends on your specific project needs, team preferences, and the trade-offs you're willing to make.

## Front-End Frameworks and Metaframeworks

Our team's standard de facto choice is React. This library is robust, suitable for projects of any scale, and benefits from a large infrastructure and a thriving community. Another advantage of React is its popularity among developers: finding a developer with expertise in React is generally easier compared to finding one proficient in Vue or Svelte.

Vue and Svelte are also viable options, each offering distinct advantages over React. They are often perceived as more developer-friendly based on various polls and surveys, although opinions on this matter can be subjective.

However, a significant objective consideration is that Vue and Svelte are more prescriptive in terms of architectural solutions and tooling compared to React. This can be advantageous for teams as it simplifies the implementation of standards and ensures better quality control, especially for developers with limited experience.

So why do we typically lean towards React over Vue or Svelte? The primary reason is the availability of developers, as mentioned earlier. Opting for a less popular tool may pose challenges in terms of development and support for the project in the future.

Therefore, the choice between Vue and React for a new project depends on the specific requirements of the project. If the project is complex and involves multiple developers or teams, React may be the preferable option. However, for smaller projects requiring minimal support, Vue or another alternative solution may suffice.

It's essential to avoid selecting esoteric or lesser-known frameworks.

Using metaframeworks like Next.js, Gatsby, Remix, etc., is recommended. These frameworks offer additional tools and optimizations, including built-in image optimization and SEO features, while also handling various low-level tasks such as bundling.

Please refrain from using Create React App in production settings. While it's a useful tool for bootstrapping projects, it's not suitable for commercial projects.
