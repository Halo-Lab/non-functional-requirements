# Performance

## Frontend

Some formal metrics for reference:

- [First Contentful Paint](https://web.dev/articles/fcp)
- [Largest Contentful Paint](https://web.dev/articles/lcp)
- [First Input Delay](https://web.dev/articles/fid)
- [Interaction to Next Paint](https://web.dev/articles/inp)
- [Total Blocking Time](https://web.dev/articles/tbt)
- [Cumulative Layout Shift](https://web.dev/articles/cls)
- [Time to First Byte](https://web.dev/articles/ttfb)

Some informal metrics, quoting [this article](https://web.dev/articles/user-centric-performance-metrics):

- **Perceived load speed**: how quickly a page can load and render all of its visual elements to the screen.
- **Load responsiveness**: how quickly a page can load and execute any required JavaScript code in order for components to respond quickly to user interaction
- **Runtime responsiveness**: after page load, how quickly can the page respond to user interaction.
- **Visual stability**: do elements on the page shift in ways that users don't expect and potentially interfere with their interactions?
- **Smoothness**: do transitions and animations render at a consistent frame rate and flow fluidly from one state to the next?

It is very important to keep at least a mental checklist (ideally – a documented checklist) with these questions for every page of a website.

Now, for a more formal approach. You should strive to achieve `100` points in [Lighthouse](https://developers.google.com/web/tools/lighthouse/)'s `Performance` metric (ideally, you want `100` in other categories as well, but it is out of scope of this particular topic). Minimal acceptable score: `95`. Use an automated tool (_TBD_) to run it for every page of the site. Lighthouse alone will cover the following performance concerns (list is not exhaustive):

- how much page load time affected by JS (yours and 3rd party's)
- image optimization
- large network payloads
- proper caching of static assets

_TBD: Running performance analysis on internal pages_

For a non-trivial projects, which needs to be supported after release, you want to monitor site performance continuously and receive alerts upon performance degradation. Suggested tool for that is [New Relic](https://docs.newrelic.com/).

_TBD: Requirements for a dynamic interaction_

### Performance: frontend deployment

It is extremely important to understand that there are two completely different approaches to frontend deployment.

The first one is to deploy the frontend as **pre-built static files**.

Pros:
- simple deployment and caching (example: S3 + CloudFront)
- very fast page initial loading speed

Cons (for highly dynamic and complex pages):
- user will need to wait for dynamic content to load after the page initial loading
- SEO is problematic (no content on initial page load)

The second one is to deploy the frontend as a **web-server** (usually backed by Node.js), which will serve pages dynamically. Next.js server actions require such deployment, for example.

Pros:
- complex pages could be generated on a backend and served "as one" without extra requests
- SEO works out-of-the-box due to server-side rendering

Cons:
- requires a server, which leads to increased infra costs and more complex deployment
- scaling with the number of website users could be much more complicated and will require more computing power (i.e. infra costs)
- initial page load might be very slow without an extra caching layer (which is another complexity level)

**Important**: never, under any circumstances, you should be running the website on a production infrastructure using the development server with hot reload (usually `npm start dev`). Ideally, you want to only use such development server mode on a local machine.

There is also a hybrid approach, which could be optimal for complex websites with tight SEO requirements under a high load. It is to dynamically pre-build complex static pages each time the content changes. Note that this can be done only for pages where content is not dependant on dynamic user data. In Next.js this could be achieved by using [Static Site Generation](https://nextjs.org/docs/pages/building-your-application/rendering/static-site-generation). This approach have all the pros of both approaches mentioned above, but can be difficult to implement (depending on the type of the website) and raises deployment complexity.

To choose the approach for a particular project it is important to consider the following questions:
- Is it important to have a very fast initial page load?
- Is it important to have SEO working out-of-the-box?
- Is it possible that the website will be under heavy load?

**Important**: it is highly recommended to have at least one non-production environment with the same type of deployment as in production.

## Backend

Our primary tech stack for backend is Node.js (logic) + PostgreSQL (data storage).

A list of important metrics to monitor in a Node.js web server application:
- response times
- request rates
- error rates
- content size
- database query times
- [event loop lag](https://davidhettler.net/blog/event-loop-lag/)
- memory consumption

It is important to use an instrument which allows to monitor all of these metrics in real time, to analyze the metrics values, and to setup alerts (email/messengers) on abnormal metric values for production deployments. Currently suggested instrument is [New Relic](https://docs.newrelic.com/docs/apm/agents/nodejs-agent/getting-started/monitor-your-nodejs-app/). New Relic also allows to monitor PostgreSQL instance performance, even when deployed within [AWS RDS](https://docs.newrelic.com/docs/infrastructure/amazon-integrations/aws-integrations-list/aws-rds-monitoring-integration/).

There are no hard guidelines on web-server response times: it might greatly depend on a particular product and even on a particular endpoint. It is completely OK for the authentication endpoint to have ~1s response time (given that the server stays responsible to other requests). It might be desired to have a very fast response time (~10ms) for, let's say, search result, which is used in popup. I suggest to use a combination of UI responsiveness requirements and common sense to determine the acceptable response times for different API endpoints. It might be a good idea to determine these values in advance and use them as a reference when implementing the API.

### Profiling

Before fixing the performance issue (let's say, the high response time of a particular API endpoint) it is crucial to determine, what particular operation causes the delay. That's where the extended logging (with unique request IDs) might help. First, create a breakdown of different request processing stages (parsing / DB querying / external API calls / etc.) with exact timings, and after that look into the possible optimizations.

### Database query optimization

Consider using indexes for the data you're searching on, but only after [analyzing](https://www.postgresql.org/docs/current/sql-explain.html) the particular slow query. You might also sometimes significantly improve performance by rewriting particular set of queries into the single, more complex one.

### Stress-testing

_TBD_