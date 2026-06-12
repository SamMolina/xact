# X-Act Framework — Maturity Scores

X-Act is a TW framework to help point client implementation. It is organized in **categories**, **modules**, **sub-modules**, **parameters**, and **questions**.

| Level | Element | Description |
|-------|---------|-------------|
| 1st | Category | Top-level domain (e.g., Software Engineering) |
| 2nd | Module | Area within a category |
| 3rd | Sub-module | Grouping within a module; maturity criteria may be defined here |
| 4th | Parameter | Dimensions within a sub-module; maturity criteria may also be defined here |
| 5th | Question | Focused on parameters *(not contemplated yet)* |

**Maturity criteria** can be defined at the **sub-module** level (e.g., `1.1.1`) or at the **parameter** level (e.g., `1.6.3.1`), depending on the granularity needed. A sub-module may have its own scores, parameter-level scores, or both. When maturity is defined at the sub-module level, child parameters without their own scores should read *Using maturity from sub-module*.

> **Note:** Missing maturity scores at any level are expected — this document is a work in progress.

---

## 1. Software Engineering

### 1.1 Architecture Quality

#### 1.1.1 Architectural Style

*   **Score 1:** Big ball of mud monolith. Dependencies are Ad-hoc, with little to no separation between core and third-party application logic. Changes in third-party integration logic usually require major changes in a majority of systems, including user interfaces. [1]
*   **Score 2:** Structured Monolith. The separation between core and third-party components exists. However, changes to third-party components usually result in major changes to service components directly interfacing with these third-party components. [1]
*   **Score 3:** Service Oriented Microservices. The separation between core and third-party components exists. Logic is cleanly veiled off in third-party components. However, there is little clarity on non-functional resilience characteristics. [1]
*   **Score 4:** Event-Driven Microservices and service-oriented microservices are used as applicable. The separation between core and third-party components exists. Logic and non-functional requirements are cleanly veiled off in third-party components. However, each team uses its own set of implementations when integrating with third parties. [2]
*   **Score 5:** Serverless Functions, Event-Driven Microservices and service-oriented microservices are used as applicable. Standardized integration templates exist and are actively used. These standardized templates are designed with specific care being taken to isolate third-party logic and resilience expectations. [2]

##### 1.1.1.1 Components
_Using maturity from sub-module_

##### 1.1.1.2 Dependencies
_Using maturity from sub-module_

##### 1.1.1.3 Data model
_Using maturity from sub-module_

#### 1.1.2 API Strategy

*   **Score 1:** API gateway is not used as an explicit pattern. No explicit strategy is used for API versioning. API Consumers are notified if backwards incompatible changes are made and are expected. API documentation is largely missing or ignored. API clients are required to consult producers' source code to look for usage patterns.
*   **Score 2:** The use of API gateway is explicitly discouraged to avoid it becoming a home of excessive business logic. API versioning is used very sparingly. In most cases, changes are made in a backwards-compatible manner. When backwards incompatible changes are required to be made, new APIs are created. API documentation is produced at the start of a project but is not maintained up to date. Hence is used sparingly by consuming teams.
*   **Score 3:** API Gateway is used as a single entry point for all consumers. It acts as a simple proxy for all downstream services and as a switch to enable zero downtime deployments. URL-based API versioning is used at all times. Consumers are expected to include a version identifier in the request at all times. API documentation is produced and all efforts are made to keep it up-to-date with implementation changes. However, the documentation does experience drift from implementation because it is maintained separately from the implementation.
*   **Score 4:** API Gateway is used as a single entry point for all consumers. It is used to expose different variations of the same API to different consumers and as a switch to enable zero downtime deployments. Header-based API versioning is used at all times. Consumers are expected to include a version identifier in the request at all times. API documentation is produced and kept in sync with implementation at all times. Documentation and implementation are produced from the same source repository.
*   **Score 5:** API Gateway is used as a single entry point for all consumers for value-added services such as authentication, authorization and resilience patterns such as circuit breaker, rate limiting, throttling etc. Header-based API versioning is used when multiple versions of an API need to co-exist. Consumers not including an explicit version identifier are returned responses from the latest version. API documentation and examples are produced and kept in sync with implementation at all times. Documentation is generated from tests and published as an artifact of the build. All documentation is published on a central API management portal for easy discoverability and access.

##### 1.1.2.1 Standards
_Using maturity from sub-module_

##### 1.1.2.2 API basic hygiene
_Using maturity from sub-module_

##### 1.1.2.3 API best practices
_Using maturity from sub-module_

#### 1.1.3 Technology Stack

*   **Score 1:** Architecture predominantly uses a technology stack that is unsupported, extremely difficult to extend or out-of-date.
*   **Score 2:** The technology stack has less support, either needs the goodwill of the open source community or involves expensive licenses. It is possible to extend the architecture but at the expense of business priorities and downtime
*   **Score 3:** The technology stack is not proprietary but deprecated or around 5 years out-of-date with the current way of doing things.
*   **Score 4:** The technology stack is current, but not quite the best fit for the problem domain. For eg; data stores use data models that have been force-fitted to capture the domain model
*   **Score 5:** The technology stack is state-of-the-art and the architecture is open to extension. The problem domain nicely fits in with the tech stack being used.

##### 1.1.3.1 Technology Stack
_Using maturity from sub-module_

#### 1.1.4 Performance

*   **Score 1:** Resilience patterns like circuit breakers, timeouts, service discovery, rate limiting, throttling and caching are not used. Performance and scale testing are not practiced.
*   **Score 2:** Resilience patterns like circuit breakers, timeouts, service discovery, rate limiting, throttling and caching are used sporadically by individual teams. Performance and scale testing are not practiced, but only on an ad-hoc basis.
*   **Score 3:** Resilience patterns like circuit breakers, timeouts, service discovery, rate limiting, throttling and caching are documented, with varying implementation styles. Performance and scale testing are not practiced, but only before significant milestones (like a large cross-functional release)
*   **Score 4:** There is standardized implementation across teams on Resilience patterns like circuit breakers, timeouts, service discovery, rate limiting, throttling and caching. Performance and scale testing are practiced periodically but are not part of the pipeline
*   **Score 5:** Implementation of resilience patterns like circuit breakers, timeouts, service discovery, rate limiting, throttling and caching are standardized and tested to meet SLAs. Performance and scale testing are practiced consistently and automated as part of the pipeline

##### 1.1.4.1 Resilience
_Using maturity from sub-module_

##### 1.1.4.2 Scalability
_Using maturity from sub-module_

##### 1.1.4.3 Availability
_Using maturity from sub-module_

#### 1.1.5 Governance

*   **Score 1:** Architecture decisions are made on an ad-hoc basis with individual teams responsible for all major decisions. There is little to no record maintained for decisions made. The primary means to enforce architecture decisions is through documents and accompanying literature.
*   **Score 2:** Architecture decisions are made by a central committee outside of the team and pushed to teams for adoption. The primary means to enforce architecture decisions is through architecture and code reviews.
*   **Score 3:** Architecture decisions are initiated by teams working on a problem. These decisions are reviewed with a central committee to ensure standards are adhered to. Architecture decisions are enforced through a combination of documentation, reviews static analysis observations.
*   **Score 4:** Architecture decisions are initiated by teams working on a problem. These decisions are reviewed with a central committee to ensure standards are adhered to. Decisions made are captured and persisted in a lightweight manner. Architecture decisions are enforced through a combination of documentation, reviews static analysis observations. In addition, some architecture decisions are enforced using a set of fitness functions that are integrated as part of the build.
*   **Score 5:** A pattern catalog of historic architecture decisions is consulted prior to large projects/undertakings. Teams work with an embedded representative from an architecture forum to expedite decisions from both a domain and technology perspective. These decisions are reviewed with a central committee to ensure standards are adhered to. Decisions made are captured and persisted in a lightweight manner. Architecture decisions are enforced through a combination of documentation, reviews static analysis observations. In addition, a majority of architecture decisions are enforced using a set of fitness functions that are integrated as part of the build.

##### 1.1.5.1 Architecture decisions
_Using maturity from sub-module_

##### 1.1.5.2 Conformance
_Using maturity from sub-module_

---

### 1.2 DevOps

#### 1.2.1 Continuous Integration and Deployment

##### 1.2.1.1 Build

*   **Score 1:** Check-ins happen on a long running private branch and remain there until story/feature completion. Integration to the mainline usually takes several weeks or months. The build process does not include adequate testing. Builds are stable, but usually require a significant amount of manual testing to certify quality. Failed builds remain red for prolonged periods of time. Check-ins on top of failed builds are fairly common. There is no clear ownership assignment for failed builds.
*   **Score 2:** Check-ins initially happen on a private branch and remain there for the duration of a development sprint/iteration. Integration to the mainline happens every 2 to 4 weeks. The build process does include various types of automated testing. But these tests are time-consuming and flaky. Hence they require a significant amount of manual testing to certify quality. Failed builds remain red for prolonged periods. Usually, someone takes ownership, but fixing red builds takes a long time.
*   **Score 3:** Check-ins and builds happen on a private branch. Features are usually fine-grained to finish within a few days. Integration happens every few days. The build process includes a good mix of unit, integration, functional and acceptance tests, and these tests are mostly green. However, a significant amount of manual testing is still needed to certify quality - primarily because of poor visibility into the quality of the tests that run as part of the build. Failed builds for prolonged periods are inevitable. Developers are unable to run stages in the pipeline locally and there isn"'t enough debugging information readily available.
*   **Score 4:** Check-ins and CI happen on a short-lived private branch to satisfy a pull-request workflow. A branch-by-abstraction style is used to turn off incomplete work. Integration is truly continuous. The build process includes a good mix of unit, integration, functional and acceptance tests, and these tests are mostly green. Additional manual testing is required for scenarios not covered through automated testing. Failed builds are not that common. But when failures do happen, other team members wait for the build to be fixed. Team members avoid checking in on top of a red build.
*   **Score 5:** Check-ins and CI happen on the mainline. A branch-by-abstraction style is used to turn off incomplete work. Integration is truly continuous. The build process includes a good mix of unit, integration, contract, functional and acceptance tests, and these tests are mostly green. Manual testing only used for exploratory testing. Failed builds are not that common. When they do occur, team members are empowered to rollback the cause of the build failure if they are not fixed by the owner.

##### 1.2.1.2 Deployment

*   **Score 1:** EAR, WAR style into a shared application container with multiple applications/services running in the same process space. Manual with downtime and outage window. Monthly or even less frequently. Deployments can only happen during low traffic "windows" because there is downtime when switching to the new version. There is always an extended, pre-emptive deployment freeze during peak periods (e.g. Thanksgiving, Christmas etc.) - no negotiations - except in case of critical bug fixes or
*   **Score 2:** Mutable deployment target with configuration management software e.g. puppet, chef, etc. Automated with downtime with outage window Frequency - Weekly or more. Deployments can only happen during low traffic "windows", because of a poor track record with failed (customer impacting) deployments. There is always an extended, pre-emptive deployment freeze during peak periods, but deployments are possible with proper justifications.
*   **Score 3:** Immutable, versioned virtual machine(VM) image e.g. VMDK, AMI etc. Automated with zero downtime, blue-green. Frequency - Almost Daily. Deployments can happen anytime during the day, but continue to happen only during low traffic "windows" due to inertia. There is a short deployment freeze during peak periods, but these are merely a formality. Deployments usually are done as and when necessary.
*   **Score 4:** Immutable, versioned container image e.g. docker, rocket etc. Automated with zero downtime - rolling or canary. Frequency - Daily. Deployments can happen anytime during the day, but continue to happen only during specific times of the day due to a lack of approvers, deployment operations personnel etc. There are no deployment freezes at any time of the year. However, deployment frequency slows during peak periods due to a lack of availability of key personnel (business and operations).
*   **Score 5:** Versioned compound container image groups e.g. helm, docker-compose etc. Automated with zero downtime - combination of blue-green and rolling. Frequency - On-demand, several times a day. Any time functionality is ready and the business wants to release it. Deployments can and happen anytime during the day. The business/product stakeholder is in complete control of when deployments should happen. Teams are free to deploy whenever they wish as long as the product/business team members are comfortable. Deployment is not a function of IT constraints, simply a business decision.

#### 1.2.2 Production Operations

##### 1.2.2.1 Observability

*   **Score 1:** Observability patterns such as log aggregation, distributed tracing, health checks, alerting, APM, etc. are not used
*   **Score 2:** Observability patterns such as log aggregation, distributed tracing, health checks, alerting, APM, etc. are used sporadically by individual teams
*   **Score 3:** Observability patterns such as log aggregation, distributed tracing, health checks, alerting, APM, etc. are documented, with varying implementations
*   **Score 4:** Implementation of Observability patterns such as log aggregation, distributed tracing, health checks, alerting, APM, etc. are standardized.
*   **Score 5:** Observability patterns such as log aggregation, distributed tracing, health checks, alerting, APM, etc. are tested to meet SLAs

##### 1.2.2.2 Business Continuity

*   **Score 1:** Active passive with MTTR of 24 hours or more
*   **Score 2:** Active passive with MTTR between 12 and 24 hours
*   **Score 3:** Active passive with MTTR between 6 and 12 hours
*   **Score 4:** Active passive with MTTR between 2 to 6 hours
*   **Score 5:** Active active with zero downtime

#### 1.2.3 Environments

##### 1.2.3.1 Provisioning and use

*   **Score 1:** Manually provisioned, long-running bare metal servers.
*   **Score 2:** Manually provisioned, long-running virtual machine servers.
*   **Score 3:** Programmatically provisioned, long-running, mutable virtual machine servers.
*   **Score 4:** Programmatically provisioned, ephemeral, immutable virtual machine servers.
*   **Score 5:** Programmatically provisioned, ephemeral, immutable containers or serverless functions.

##### 1.2.3.2 Best Practices

*   **Score 1:** Application configuration is embedded within application deployment artifacts for a fixed set of environments. New environment(s) or changes to application configuration require an application rebuild. Feature toggles are not used to turn on/off application functionality dynamically. Secrets are embedded within application deployment artifacts and are managed manually.
*   **Score 2:** Application configuration is embedded within application artifacts. Environment-specific configuration parameters can be overridden without requiring an application rebuild. However, overrides are not audited. Configuration changes require application redeployment. Feature toggles are embedded within application deployment artifacts. Changes to toggles require an application rebuild. Secrets are externalized from application deployment artifacts, but are managed manually.
*   **Score 3:** Application configuration is externalizable from application artifacts. But there is no operationalized mechanism to do so. Teams continue to require rebuilds when a change to application configuration is required. Feature toggles are externalized from application deployment artifacts. Individual teams use custom methods to implement toggle functionality. Turning off functionality reliably requires intimate knowledge of application internals. Secrets are externalized from application deployment artifacts, with encrypted secrets being stored in source control.
*   **Score 4:** Application configuration is externalized from the deployable application artifact. Teams making use of externalized configuration use custom (including homegrown) methods to do so. Feature toggles are externalized from application deployment artifacts. Teams use a consistent approach to toggles, but toggling off functionality still requires knowledge of application internals. Secrets are externalized from application deployment artifacts, with encrypted secrets being stored in a configuration management system.
*   **Score 5:** Application configuration is externalized from the deployable application artifact. All teams use a consistent method to make changes to application configuration. All changes are traceable to a source code check-in. Feature toggles are externalized from application deployment artifacts. Toggles are defined at a business feature level. Secrets are externalized from application deployment artifacts, with encrypted secrets being stored in a secrets management server.

---

### 1.3 Quality Assurance

#### 1.3.1 Build In Quality Mindset

##### 1.3.1.1 Business Goal Comprehension

*   **Score 1:** The awareness within the team is minimal or nil.
*   **Score 2:** The team has minimal understanding of the functionality. The team understands isolated functional areas, but not how those are aligned with the overall business/product vision. There is minimal understanding of the users and their needs.
*   **Score 3:** The team has a good understanding of the overall business/product vision, understand the functional areas, and how they are aligned with the overall business goals.
*   **Score 4:** In addition, the team fully understands the NFRs (security, accessibility, performance requirements.) The team has access to the stakeholders to understand the product goals and functionality.
*   **Score 5:** In addition, the team fully understands the various types of users and their goals with the product/platform. The team understands the competitor products in this space. They are in a position to collaborate with the product team and share feedback on product features.

##### 1.3.1.2 Project Technical Comprehension

*   **Score 1:** The QAs (QA team) aren't aware of the technical details and architecture of the product/platform
*   **Score 2:** The QAs (QA team) understand the tech stack used, but aren't aware of the architecture or design
*   **Score 3:** The team understands architecture and incorporates some validation based on architecture
*   **Score 4:** The team understands architecture well and testing driven by known strengths/weaknesses.
*   **Score 5:** Team fully understands the architecture design, and provides feedback to improve/optimise architecture

#### 1.3.2 Test Strategy

##### 1.3.2.1 Test Preparedness

*   **Score 1:** No test strategy exists
*   **Score 2:** Test strategy document exists, but is not implemented or updated regularly. The understanding is fragmented across the various team members.
*   **Score 3:** The test strategy document is understood fairly among the various members of the QA team and is followed for most of the execution. Updates to the testing strategy based on implementation feedback are minimal and take longer time.
*   **Score 4:** Test strategy is a living document, and is updated quite regularly based on implementation feedback. The team is well versed with the latest version, and the implementation seldom deviates from the strategy.
*   **Score 5:** The entire development team understands the testing strategy and contributes to updating based on the implementation experience. The strategy is exhaustive and covers the breadth, but at the same time simple to understand, implement and update.

##### 1.3.2.2 Sensible Defaults

*   **Score 1:** There are no sensible defaults defined or implemented in the team
*   **Score 2:** Only a few sensible defaults are listed, and followed inconsistently
*   **Score 3:** Key sensible defaults are listed and implemented.
*   **Score 4:** Sensible defaults are listed comprehensively and followed regularly. Updates are done in a timely manner, based on the alignment to product/platform and technical requirements.
*   **Score 5:** Best of industry and pioneering approaches used across the team

#### 1.3.3 Testing Organization Setup

##### 1.3.3.1 Test Process

*   **Score 1:** The testing process isn't defined, and testing flow across stories/epics is inconsistent
*   **Score 2:** The testing process is partly defined. The team is not fully onboard with the process, and intermittently follows the defined process.
*   **Score 3:** The testing process is defined and documented. The majority of the team understands the testing process, and the team follows the defined process for a majority of the stories/epics.
*   **Score 4:** The testing process is defined, and well-understood across the team. The process is followed for all testing and modified where and when necessary.
*   **Score 5:** Additionally, the team is in a position to take decisions on expectations for the process where needed.

##### 1.3.3.2 Metrics

*   **Score 1:** The team doesn't use any metrics to drive the testing.
*   **Score 2:** The team tracks a few activity metrics. The metrics are sometimes dysfunctional and aren't a true reflection of the team's performance or testing quality.
*   **Score 3:** The team has some useful metrics and they track them regularly. Metrics are an afterthought.
*   **Score 4:** The team tracks key metrics that inform the quality of testing implemented. The metric values are a good indication of how the testing is performed, and quality of the software.
*   **Score 5:** Metrics tracked truly indicate the quality of the testing and software. Trends in metrics are tracked regularly, and inform the key decisions the team needs to take to improve the software and testing.

##### 1.3.3.3 Test Management

*   **Score 1:** There is no test management software or practice in place. The knowledge of tests, automation, and defects isn't maintained in a commonplace.
*   **Score 2:** Test management software is in place but not used by the team for test efforts consistently. The tests and other documentation are out of date.
*   **Score 3:** Test management tools are used by the team regularly. There are some gaps in the overall tests, automation and documentation.
*   **Score 4:** All tests are run through test management, and the tests are up to date with minor exceptions.
*   **Score 5:** Test management is completely up to date, and all tests are run through the test management tools. There is a good record of all the tests run, and the corresponding results. Tracing older results is easy and common.

#### 1.3.4 Test Pyramid

##### 1.3.4.1 Unit Testing

*   **Score 1:** The team doesn't have any of these practices in place.
*   **Score 2:** The team performs dev box testing only for a few stories, and inconsistently. No code coverage tools in place, and no code reviews.
*   **Score 3:** The team has regular dev box testing, the code coverage tools are in place, and unit test code reviews are done
*   **Score 4:** Dev box testing is an essential part of the testing process. Code coverage tools are implemented, and code coverage is actively looked at, and improved. Code reviews are a regular practice in the team.
*   **Score 5:** Additionally, the test automation strategy is devised based on the unit test coverage. QAs share feedback on the unit tests with the developers. The team collectively adheres to the test pyramid.

##### 1.3.4.2 Functional Testing

*   **Score 1:** All the testing is manual and unstructured. Test cases are not documented and mapped to functional areas. Many defects escape the testing cycle. Regression tests are incomplete, and the cycle is long and ineffective.
*   **Score 2:** Most of the testing is manual, and tests are documented against the functionality. However, tests are not updated regularly with changes in functionality. Some defects escape the testing cycle and make it to production. There are gaps in regression testing cycles.
*   **Score 3:** Regression tests are well documented, and cover the key functionality of the product/platform. Testing is a combination of manual and automated scripts. Automation tests need maintaince and upgrades. There are few defect leakages to the production environment.
*   **Score 4:** Regression tests are mapped to current functionality and are constantly upgraded based on the change in functionality. The majority of the tests are automated, and the team performs exploratory testing. Some of the automation tests are unreliable and need maintenance. These areas are known and covered using manual testing. The defect leakages to production are very rare.
*   **Score 5:** Regression tests are constantly upgraded, most times along side or before the product functionality is developed. Automated regression is exhaustive and robust. Team depends on the automated suite for regression cycles. Team spends quality time on exploratory, NFR testing. Defect leakage to production is very rare.

##### 1.3.4.3 Automation

*   **Score 1:** There are no automated tests in place.
*   **Score 2:** Automated tests are minimal and the team depends on manual testing for regression. Automated tests are flaky and need maintenance. There is no CI in place.
*   **Score 3:** Key test cases are automated and run on CI. The tests can be made more robust and build times can be optimized. The team fixes the key tests in a timely manner, and the results are analysed for every failure of build and fixed.
*   **Score 4:** Exhaustive automation test coverage is present for most of the regression suite. The test suite is robust and trustworthy. Build times are optimized, and the team depends on the results for build verification. The team spends most of the time on exploratory testing. There is good adherence to the test pyramid.
*   **Score 5:** Additionally, the team has automated security checks and performance testing. The tests are constantly upgraded and optimized.

---

### 1.4 Code Quality

#### 1.4.1 Readability

*   **Score 1:** No coding standard followed, Code is difficult to convey functional meaning.
*   **Score 2:** _WIP — maturity scores to be defined_
*   **Score 3:** Partly following coding standards, code is modular but all other standards are not in place.
*   **Score 4:** _WIP — maturity scores to be defined_
*   **Score 5:** following almost all coding standards, code is modular and follow strict style guide and naming conventions. methods/classes represent function/responsibility efficiently.

#### 1.4.2 Maintainability

*   **Score 1:** No clear separation of responsibility and naming does not reflect the responsibility, No linting and no code quality measures exist
*   **Score 2:** Very little code follows SRP but naming convention does not reflect the responsibility, Code quality is measured manually sometimes
*   **Score 3:** Portion of the code base follow SRP but naming does not allow easy identification of the responsibility, Code quality is analysed and measured manually.
*   **Score 4:** Code follows SRP and most of the code easily understandable, Automated ways to analyse and measure code quality.
*   **Score 5:** Single Responsibility Principle has been followed and naming allows for easy identification of responsibility, Automated analysis of code quality in place, prerequisite measures like linting,static scan etc.

#### 1.4.3 Re-usability

*   **Score 1:** Components are tightly coupled, Support only specific formats. Very difficult to onboard new integration/consumer.
*   **Score 2:** _WIP — maturity scores to be defined_
*   **Score 3:** Components are coupled, Support some formats and integration protocols. Fairly difficult to onboard new integration/consumer.
*   **Score 4:** _WIP — maturity scores to be defined_
*   **Score 5:** Components are loosely coupled, Support most of formats and integration protocols. Fairly easy to onboard new integration/consumer.

#### 1.4.4 Evolvability

*   **Score 1:** No Design Patterns being used. Design does not reflect domain. Functional changes spill over to unrelated areas of code.
*   **Score 2:** Very few design patterns being used. Design does not reflect domain. Functional changes may spill to unrelated areas of code.
*   **Score 3:** Design patterns are being followed in some part of the code but design is not driven by domain
*   **Score 4:** Design patterns are being followed in most of the code. Some part of design also reflects domain. But for other parts functional changes may spill in unrelated areas
*   **Score 5:** Most of the code uses Design Patterns and design is driven by domain. Functional changes are easy and limited to related classes/files

#### 1.4.5 Complexity

*   **Score 1:** Code is difficult to understand, difficult to change. Changes carry high risk of breaking something
*   **Score 2:** Very little code is easy to understand or change. Changes carry significant risk of breaking something
*   **Score 3:** Some part of the code is easy to understand and change without breaking elsewhere. But there are other parts that are neither easy to understand nor easy to change without breaking something
*   **Score 4:** Most of the code is self-explanatory, easy to change. Changes sometimes break unrelated parts of other code
*   **Score 5:** Self-explanatory code, easy to change. Changes do not carry risk of breaking unrelated code

#### 1.4.6 Testability

*   **Score 1:** No automated tests and automating tests are not possible
*   **Score 2:** Most of the code is not testable and there are very few tests
*   **Score 3:** There are some tests and some of the code can be inherently testable
*   **Score 4:** Most of the code is testable but there are few tests
*   **Score 5:** There is healthy automated tests and code inherently testable

#### 1.4.7 Tech Debt

*   **Score 1:** Tech debt is not tracked at all
*   **Score 2:** Tech debt is not tracked but arbitrarily some tech debt is paid down
*   **Score 3:** Only some part of known Tech debt is tracked and prioritised but not regularly
*   **Score 4:** All tech debt is tracked. But not prioritised and worked upon regularly
*   **Score 5:** All known tech debt is tracked and prioritised regularly based on value/effort, with equal priority as other functional features

#### 1.4.8 Logging

*   **Score 1:** Logs are not available at all. Any tracing is almost impossible.
*   **Score 2:** A logging framework is in place but logs are not consistent in application. Format and log levels are also not consistent. Tracing is very difficult.
*   **Score 3:** A logging framework is in place but logs are not consistent in application. The format is defined but log levels are also not consistent. Some times log is overused and creates large log files. Tracing is fairly complex.
*   **Score 4:** The logging framework is in place and logs are consistent in application. The format is defined and log levels are also consistent. Sometimes PII gets logged in, sometimes logs are overused, End to end tracing is also not possible.
*   **Score 5:** The logging framework is in place and logs are consistent in application. The format is defined and log levels are also consistent. End-to-end tracing is easily available and can be easily understandable.

#### 1.4.9 Exception Handling

*   **Score 1:** No exception handling.
*   **Score 2:** _WIP — maturity scores to be defined_
*   **Score 3:** Some of the exceptions are handled but the application still can raise and propagate exception which goes back to consumer/logs without handing.
*   **Score 4:** _WIP — maturity scores to be defined_
*   **Score 5:** Exception handling is implemented, checked exceptions are propagated and handled via throw early catch late principle, and unchecked exceptions are handled at the top level layer to avoid unintentionally revelation of code/logic/stack trace.

---

### 1.5 Agile Project Management
_WIP — sub-modules to be defined_

---

### 1.6 Engineering Excellence

#### 1.6.1 Requirement Analysis

##### 1.6.1.1 Requirement Analysis

*   **Score 1:** Requirements have not been defined in detail. All possible ways to arrive at a solution have not been thought about. NFS is not captured
*   **Score 2:** _WIP — maturity scores to be defined_
*   **Score 3:** _WIP — maturity scores to be defined_
*   **Score 4:** Requirements have been detailed, not consistent and of high quality. NFS  are incomplete. Business value is not assessed completely with the potential solution
*   **Score 5:** Requirements have been detailed, consistent and of high quality. NFS has been detailed and frequently updated. Alternative solutions to the potential solution have been compared and evaluated. Business value is always assessed with the potential solution

##### 1.6.1.2 Requirement Design

*   **Score 1:** No detailed design and approach to describe the future state and user journey and process flows are not available
*   **Score 2:** _WIP — maturity scores to be defined_
*   **Score 3:** Detailed design and approach to describe the future state is and user journey and process flows are redundant and not updated frequently
*   **Score 4:** _WIP — maturity scores to be defined_
*   **Score 5:** Detailed design and approach to describe the future state and user journey and process flows are updated regularly and used for all discussions

#### 1.6.2 Architecture and Design

##### 1.6.2.1 Architecture Engagement

*   **Score 1:** No architecture runway is available. CFRs are not defined.
*   **Score 2:** _WIP — maturity scores to be defined_
*   **Score 3:** Architecture diagrams and models (ie. C4) are created but it is difficult to find. architecture tech debt is identified and prioritized regularly. There are not enough documentation or sessions available and teams are working silos.
*   **Score 4:** _WIP — maturity scores to be defined_
*   **Score 5:** Architecture diagrams and models (ie. C4) are created and available to everyone to be consumed. architecture tech debt is identified and prioritized regularly. There is enough documentation or sessions available to make everyone understand the big picture.

##### 1.6.2.2 Documentation

*   **Score 1:** Decisions are taken in a silo, and no record is captured. No documentation is available.
*   **Score 2:** Some of the important decisions are captured but they get outdated with time,  Functional documents are manually created.
*   **Score 3:** All important decisions are captured and maintained in form of ADRs,  Functional documents are manually created so they get outdated easily. docs are not standardized and scattered, so it's difficult to find stuff.
*   **Score 4:** All important decisions are captured and maintained in form of ADRs, System generates capabilities and functional documents in form of live specifications through well-described tests. docs are not standardized and scattered, so it's difficult to find stuff.
*   **Score 5:** All important decisions are captured and maintained in form of ADRs, System generates capabilities and functional documents in form of live specifications through well-described tests. docs are standardized and well placed centrally to be consumed by teams.

#### 1.6.3 Development

##### 1.6.3.1 Development Discipline
*   **Score 1:** No local checks on code for linting or secret scanning, Tests are missing or poorly written. The team is missing XP practices and tech debt identification understanding. Development gets delayed because of external dependencies.
*   **Score 2:** The team follows some of the XP practices but still misses effective tests and fail-early setup, most of the linting or scanning happens over pipeline only. A team missing tech debt awareness. External dependencies slow down development.
*   **Score 3:** Team follows XP practices and have fail-early setup where most of unit tests, linting or scanning happen in local machine via pre-commit hook, Tests are not effective and just provide code coverage sense, Tech debts are identified but not picked up. Team doesn't do refactoring. External dependencies are sometimes mocked to speed up development.
*   **Score 4:** The team follows XP practices and has a fail-early setup where most of the unit tests, linting or scanning happen in a local machine via a pre-commit hook, Tests are written effectively with the right data set, and Tech debts are identified but not picked up. The team doesn't do refactoring. External dependencies are sometimes mocked to speed up development.
*   **Score 5:** The team follows XP practices and has a fail-early setup where most unit tests, linting or scanning happen in a local machine via a pre-commit hook, Tests are written effectively with the right data set, and Tech debts are identified and picked up in each iteration. The team does refactoring as and when they work on any task. External dependencies are mocked to speed up development.

##### 1.6.3.2 Developer Onboarding & Cultivation
*   **Score 1:** The team has a different-2 local setup and there is no standardised way to onboard a new dev, It takes a large re-effort every time. The team missed domain knowledge and security awareness overall.
*   **Score 3:** Dev onboarding is standardized, There are documents available for set-up to follow, It takes a few hours for complete setup but there can be different-2 setups within a team. Also, we have pre-recorded sessions/documents on the domain of work, larger picture and security and keep the team informed.
*   **Score 5:** Dev onboarding is standardized and checklist-driven, Everyone in the team follows the same setup and there are automated scripts available wherever possible, it takes just a few min to a few hours for a complete setup. Also, we have pre-recorded sessions/documents on the domain of work, larger picture and security and keep the team informed.

##### 1.6.3.3 Source Control Practices
*   **Score 1:** Developers don't follow any standards for commits and ad-hoc branches for features and difficult to manage.
*   **Score 2:** Team creating multiple branches. Lots of merging effort. The commits are not atomic and difficult to port to other branches.
*   **Score 3:** The team has definite branches for development/staging/releases. The commits are not atomic. The commits are not traceable from the story card and merging commits between branches is difficult.
*   **Score 4:** The team follows trunk-based development and uses feature toggles. The commits are atomic and traceable from the story card. Easy to merge / cherry-pick to other branches.
*   **Score 5:** The team follows trunk-based development and uses feature toggles. All commits are atomic and follow org standards in messages.

##### 1.6.3.4 Data Management Practices
*   **Score 1:** Adhoc Database changes happen directly through the GUI interface, No DB change versioning exists, Backups are not taken and no monitoring is in place.
*   **Score 2:** Database migration changes are neither captured as code nor version controlled. Backups are not taken and tested periodically. Basic monitoring is there but we look and react manually.
*   **Score 3:** Database migration changes are captured as code and version control. Backups are not taken and tested periodically. Monitoring is there but we look and react manually.
*   **Score 4:** Database migration changes are captured as code and version control. Backups are taken and tested periodically. Monitoring is there but we look and react manually.
*   **Score 5:** Database migration changes are captured as code and version control. Backups are taken and tested periodically. Monitoring and alerts are enabled as applicable.

#### 1.6.4 Deployment

##### 1.6.4.1 Pipeline
*   **Score 1:** No build pipeline or build tool. No deployment pipeline. The team manually creates deployment artefacts and deployed manually.
*   **Score 2:** No automated build and deployment. Some tests exist. They are neither automated and repeatable on every build nor comprehensive coverage. Some security scanning tools exist.
*   **Score 3:** No automated deployment. An automated build (CI) pipeline is in place BUT WITHOUT - various levels of test suites, - monitoring and alerts set up to detect build/deploy failures early - security scanners.
*   **Score 4:** Automated build (CI) and one-click deployment pipeline is in place with - monitoring and alert setup to detect build/deploy failures early - security scanners - only selected commits are deployed to production.
*   **Score 5:** An automated build and deployment (CI/CD) pipeline is in place. - Every commit goes to production - monitoring and alert set up to detect build/deploy failures early - security scanners.

##### 1.6.4.2 Cloud Practices
*   **Score 1:** Components are not containerized and are tightly coupled in nature. Infrastructure is manually handled.
*   **Score 2:** Components are containerized and tightly coupled in nature. components can not scale horizontally. Infrastructure is created manually once with some configs and policies (scaling, logs etc) which are never corrected back. Resources are over-provisioned or under-provisioned.
*   **Score 3:** Components are containerized and loosely coupled in nature. components might not scale horizontally easily. Infrastructure is created manually once with some configs and policies (scaling, logs etc) which are never corrected back.
*   **Score 4:** Components are containerized and loosely coupled in nature. components can scale horizontally easily. Infrastructure is created manually once with some configs and policies (scaling, logs etc) which is partly optimized.
*   **Score 5:** Components are containerized and loosely coupled in nature. components can scale horizontally easily. Infrastructure as code exists with optimal configs and policies (scaling, logs etc).

#### 1.6.5 Quality Assurance

##### 1.6.5.1 Shift-Left Testing/Quality
*   **Score 1:** Poorly written tests here and there without any strategy in place, There is no automation exist. External dependencies make the system non-testable.
*   **Score 2:** Following the test pyramid approach partially with some test layers, Tests are not written with the right dataset. The test environment is not available and automation does not exist. Mocks are not used in the lower environment to cover all scenarios depending on external services.
*   **Score 3:** Following test pyramid approach partially with some test layers, Tests are written with right datset on each layer. Test environment is not available and automation exist partially. Mocks are not used on lower environment to cover all scenario depending on external services.
*   **Score 4:** Following the test pyramid approach optimally with all layers, effective tests are written with the right dataset on each layer. The test environment is available and automation exists partially. Mocks are not used in lower environments to cover all scenarios depending on external services.
*   **Score 5:** Following the test pyramid approach optimally with all layers, effective tests are written with the right dataset on each layer. Test environment available and automation exist. Mocks are used in the lower environment to cover all scenarios depending on external services.

#### 1.6.6 CFRs

##### 1.6.6.1 Accessibility
*   **Score 1:** No accessibility guidelines are available and the team does implementation without considering the accessibility aspect.
*   **Score 3:** Standard accessibility guide available and followed by team in implementation some times. Some of developed solutions support defined accessibility requirements to some extent.
*   **Score 5:** Standard accessibility guide available and followed by the team in implementation. All developed solutions support defined accessibility requirements.

##### 1.6.6.2 Logging
*   **Score 1:** Log levels and patterns are used randomly, and request or actions are not traceable.
*   **Score 3:** Log levels and pattern are standardize, Each request or action can be traced to some extent only.
*   **Score 5:** Log levels and patterns are standardised, logs are combined and each request or action can be traced across systems using co-relation ids.

---

### 1.7 DevSecOps

#### 1.7.1 DevSecOps Pipeline

##### 1.7.1.1 Planning & Tracking

*   **Score 1:** _WIP — maturity scores to be defined_
*   **Score 2:** Manual practices are used, with possible use of some rudimentary tools, that collect and store information used to track and report status and outputs from planning and tracking activities.
*   **Score 3:**
    • Planning and tracking tools are used to define tasks and activities, along with the resources needed to perform them and achieve an objective or commitment, and track progress, or lack thereof, towards achieving the given objective.
    • The tools provide the ability to capture and associate planning and tracking metadata, such as estimates, assumptions, prioritization, assignment, status, commitments, assets, association to implementation elements and supporting artifacts, and agreements. Metadata may consist of mostly manually collected information, with minimal automation.
    • Automated visualization techniques are used to organize activities, understand dependencies, coordinate multiteam efforts, and road map future commitments. The automated system is used to share project plans and status of current activities with relevant stakeholders.
*   **Score 4:**
    • The planning and tracking tools are able to coordinate multiple value streams at the organizational level. Planning and tracking activities are integrated to include both technical and non-technical activities, such as quality assurance, documentation, testing, and configuration management. Dependencies between technical and non-technical activities can be visualized in order to coordinate efforts and identify issues.
    • Metadata is used to support estimation, projections and what-if scenarios simulations. Organizations, projects, and teams are able to customize metadata, and associated use, in order to meet relevant stakeholder needs.
    • The planning and tracking tools are integrated with other tools in order to automatically collect metadata associated with various value stream activities. This includes defect, issues, and noncompliance efforts as they are automatically discovered and subsequently addressed and tracked to closure and asset management.
    • Automated stakeholder notification and status reporting, and associated visualizations, are used to notify relevant stakeholders of changes to plans or commitments, status of current activities, deviations from defined thresholds, and asset renewals and maintenance.
*   **Score 5:** Data is used to
    • apply statistical analytical methods to planning and tracking practices in order to improve and optimize the team's, project's, and organization's ability to meet objectives and commitments
    • provide objective quantitative status to relevant stakeholders
    • automatically generate tasking and execute processes based on plan

##### 1.7.1.2 Configuration Management

*   **Score 1:**
    • All supporting artifacts and implementation elements that require configuration control are identified and documented.
    • The level of configuration control for each supporting artifact and implementation element is defined.
    • While the configuration management of supporting artifacts may be a fully manual process, an automated version control system, or set of systems, must be in place to track current and historical versions of files used to create implementation elements.
*   **Score 2:**
    • Automated configuration management system(s) are in place for all identified supporting artifacts and implementation elements.
    • Immutable logging is in place for all changes to configuration items and associated metadata, such as who made the change, when the change occurred, and what was changed.
    • Changes to the system and product under development are associated with an approved requirement or change request.
    • All relevant stakeholders are notified when changes to configuration items are requested.
    • Some integration between the automated version control system used for file tracking and other aspects of the DevSecOps pipeline has occurred in order to enable the automatic triggering of other activities.
    • The automated version control system traces relationships between test artifacts and requirements, and test results and associated artifacts, to a specific instance of the system or product under development in use at a given time, past or present.
*   **Score 3:**
    • Manage and control the volatility of change. Be able to identify impacted supporting artifacts and implementation elements a given change request will impact.
    • Use automatic discovery tools to scan current instance of system and product under development, and associated configurations, to identify mismatches between current instance and approved versions under configuration management in order to ensure integrity of the instantiated instances. Automatically report all mismatches to relevant stakeholders.
    • The system shall automatically maintain an audit trail of all system configuration changes to include what was changed, who/what changed it, and when the change occurred.
    • System only allows authorized individuals, or entities, to make specific types of changes to the product under development based on the individual's role, or entity's purpose, and where they are in the DevSecOps pipeline.
*   **Score 4:**
    • Automatically correct any misconfiguration of the currently instantiated system and product under development based on approved supporting artifacts and implementation elements under configuration control.
    • The system shall monitor user activities and actively identify security-related actions and system configuration changes that are uncharacteristic of the given user and notify relevant stakeholders of the uncharacteristic behavior to validate the change was appropriate and to avoid insider threats.
    • A fully automated change proposal process is in place, where changes are proposed and automatically routed to relevant stakeholders for approval and implemented by the system.
*   **Score 5:** _WIP — maturity scores to be defined_

##### 1.7.1.3 Solution Development

*   **Score 1:**
    • All development activities and tools have been identified and documented.
    • Tools are provided to enable users to edit, compile, and review source code.
    • The ability for developers to trace links between requirements, architectural elements, and implementation elements is provided.
    • A repository for all requirements and associated metadata is provided.
    • Manual processes for assuring security and privacy compliance are defined and used.
    • Processes for transitioning between development components are defined and used.
    • Individual processes are scripted and repeatable.
    • Processes may require manual intervention between phases and/or to coordinate steps.
    • Process initiation may be manual or automated.
*   **Score 2:**
    • Transitions between implementation elements, and supporting artifacts, are automated, possibly manually triggered.
    • Secure coding practices and development coding standards are identified and documented.
    • Traceability of software code origins is provided to provide a SBOM and verify use of most recent third-party components.
*   **Score 3:**
    • Transitions between development components are fully automated, either triggered on a periodic schedule or automatically triggered based upon completion of another component's activity.
    • Determination of requirement feasibility and validation analysis is supported.
    • Model-based software engineering in order to provide continuous, iterative, and traceable requirements model is supported.
    • Policy as code (e.g., Security Technical Implementation Guide (STIG) enforcement) is supported.
*   **Score 4:**
    • Transitions between development components is performed continuously without human intervention.
    • Code commits are continuously audited, with alerts to relevant stakeholders.
    • "Digital twin" modeling of the production system is enabled.
    • Advanced analysis to ensure compliance is supported.
*   **Score 5:** _WIP — maturity scores to be defined_

##### 1.7.1.4 Integration

*   **Score 1:**
    • Documented, repeatable, processes exist that may be manual, automated, or some combination of the two.
    • Some individual processes (e.g., merging changes) may require expert subjective judgement.
    • Processes may require manual intervention between phases and/or to coordinate steps between disparate systems
    • Some human-human and human-process contact occurs outside the orchestration pipeline.
    • Process initiation is manual and irregular.
*   **Score 2:**
    • Most individual processes are scripted and repeatable.
    • Expert subjectivity has been removed from all processes by adopting processes with objective criteria for success.
    • An orchestrated integration pipeline exists; however, it may not be fully automated.
    • Some human-human and human-process contact occurs outside the orchestration pipeline.
    • Integration process initiation is regular whether manual or automated.
*   **Score 3:**
    • All individual processes are scripted and fully automated.
    • An orchestrated integration pipeline controls all processes from start to finish.
    • All human-process contact occurs from within the context of the orchestration pipeline (e.g., approvals captured in ticketing system, SCM, etc., and orchestration continues).
*   **Score 4:**
    • The entire integration pipeline is fully automated, requiring no manual intervention.
    • The entire integration pipeline runs in near real time as changes are committed to the code base.
    • Alerts, notifications and results of integration are sent to relevant engineers automatically.
    • A successfully integrated product is ready for delivery with no additional manual processes required.
*   **Score 5:** _WIP — maturity scores to be defined_

##### 1.7.1.5 Verification & Validation

*   **Score 1:**
    • All relevant stakeholders, with regards to the products and services associated with the product under development and the system that supports it, have been identified.
    • All testing cases, procedures, and their artifacts are configured, stored, and maintained for a given instance of a product under development.
    • The system and product under development support the necessary technologies to execute tests.
*   **Score 2:**
    • Automated tools are used to trace tests to requirements.
    • Automated tools are used to trace tests cases and artifacts to specific versions of a product under development.
    • Automated tools are used to configure, store, and execute tests.
    • Test coverage reports are generated and captured for a specific instance of the system or product under development.
    • Tests are performed across multiple phases of the software lifecycle, such as development, test, and operations, providing feedback continuously.
    • Security patching is automatically tested, resulting in automated report generation and delivery.
    • Both functional and nonfunction tests are manually or automatically executed.
*   **Score 3:**
    • Tests are executed automatically using a continuous integration technique.
    • An MBSE approach is used to plan and execute testing of the system and product under development.
    • The system and product under development automatically execute quality tests that either passes or fails the appropriate component under test based on quality metrics for any change being made. Appropriate monitoring of the system and product under development enforces the quality metrics.
    • The system provides the necessary environment to perform advanced security testing such as fuzz and penetration testing activities.
*   **Score 4:** _WIP — maturity scores to be defined_
*   **Score 5:** _WIP — maturity scores to be defined_

##### 1.7.1.6 Deployment

*   **Score 1:** The system can manually recover if a failure occurs in a deployed product, deploying the product at the last known acceptable state.
*   **Score 2:**
    • A quality criterion for the deployment of the system and product under development is defined.
    • While monitoring for failures can be a combination of manual and automated detection processes:
    • The system can automatically recover if a failure occurs in a deployed product, deploying the product at the last known acceptable state.
    • The system can automatically recover the product to a previously working state in the event of system failure.
    • The system can track the changes between deployed products and the personnel and reasoning involved in the change.
*   **Score 3:**
    • Both the system and product under development are fully automated in terms of orchestration and deployment into target environments
    • Various release strategies are supported to include canary, Blue-Green, multiple service, batch, rolling, and A/B testing.
    • The product under development is deployed continuously, supported by sufficient automation in which no human intervention is required to release the product to its users.
    • The system shall automatically collect the necessary data to monitor the system and product under development for failures and quality issues and alert relevant stakeholders when corrective actions are required.
    • In the event that a failure or cancellation occurs during deployment of the product or system, the system will automatically restore a the most recent working version.
    • Automated updating or patching of software used by the system. Patches are rolled out automatically to the various parts of the system.
*   **Score 4:**
    • Continuous improvement of the testing procedures is performed based on the data collected from the system and product under development tests.
    • The system shall automatically identify and track when the defined quality criteria have not been met and the automated quality controls have been bypassed. All relevant stakeholders will be automatically notified, and the noncompliance issue will be tracked to closure.
*   **Score 5:** _WIP — maturity scores to be defined_

##### 1.7.1.7 Monitor & Control

*   **Score 1:**
    • All supporting artifacts and implementation elements that require monitoring and control are identified and documented.
    • The level of monitoring and control for each supporting artifact and implementation element is defined.
    • A policy and plan for planning and performing the monitor and control capability is established and maintained.
    • The work products of the monitor and control capability are placed under appropriate levels of control.
*   **Score 2:**
    • The people performing or supporting the monitor and control capability are trained as needed.
    • Automated monitor and control system(s) are in place for all identified supporting artifacts and implementation elements.
    • Automated collection of work products, measures, and measurement results are in place.
    • Automated comparison of actual measurements to expected measurements is performed, and deviations are quantified.
    • Automated alerting when significant deviations occur.
*   **Score 3:**
    • The relevant stakeholders of the monitor and control capability are identified, involved, and are obtaining the information they need to make decisions.
    • Sharing of monitor and control information to relevant stakeholders is automated.
    • Stakeholders can tailor the visualizations of the information provided to meet their needs.
*   **Score 4:**
    • The monitor and control capability is itself subject to being monitored and controlled and corrective action is taken when necessary.
    • Automated collection of monitor and control capability work products, measures, measurement results, and improvement information, including records of significant deviation, criteria for significant deviation, and corrective action results, are in place.
    • Root causes of defects and other problems in the monitor and control capability are identified and corrected.
    • Monitor and control capability is itself subject to continuous improvement.
*   **Score 5:** _WIP — maturity scores to be defined_

##### 1.7.1.8 Hosting Services

*   **Score 1:**
    • The hosting services adequately support the scalability, reliability, regulatory, and security requirements to operate, maintain, and build an organization's product.
    • The hosting services provide compatibility with the testing frameworks and tools utilized throughout system and product development lifecycles.
*   **Score 2:**
    • Logs from hosting services are aggregated, auditable, and analyzable.
    • System transaction logs are available and immutable.
    • Performance metrics can be visualized and analyzed for hardware, software, database, and network components.
    • Role-based access control is utilized throughout.
    • All information collected uses proper techniques to mitigate privacy and sensitivity concerns, and can be properly disposed of when necessary.
    • All configuration items are identified and resources are planned and executed in order to maintain configuration integrity of the given item.
    • Disaster recovery processes are documented and supported.
*   **Score 3:**
    • The system infrastructure is provisioned using IaC and is automated.
    • Captured metrics can generate alerts based off of defined values.
    • The system is able to automatically alert and communicate metrics associated with security risks of the underlying infrastructure to stakeholders so they can manage risk and make decisions regarding risk and impact to software applications.
    • Automatic upgrading of operating system software and supporting services is in place.
*   **Score 4:**
    • Qualities such as performance, capacity, security, compliance, and risk tolerance are continuously being monitored using automated tools. Results from the automated tools are automatically reported to all relevant stakeholders to ensure the quality of the automated process and to identify and track improvements to quality attributes.
    • System configuration and performance are continuously being monitored using automated tools to identify and report all anomalies. Results from the automated tools are automatically reported to all relevant stakeholders so they can manage risk and make decisions.
    • Infrastructure is immutable and can be automatically replaced versus update in place.
*   **Score 5:** _WIP — maturity scores to be defined_

##### 1.7.1.9 Software Assurance

*   **Score 1:**
    • All relevant stakeholders and expectations with regards to the products and services associated with the product under development and the system that supports it have been identified.
    • System functional and nonfunctional requirements are documented.
    • A comprehensive software bill of materials (SBOM) is compiled detailing all components that make up the DevSecOps system.
    • All relevant system constraints and regulatory requirements are documented.
    • Software assurance processes and tools are inventoried, and policies and procedures are written setting out how they are to be used to meet assurance requirements.
    • Documented policies and procedures may use a traditional document-centered approach, and dissemination may be a manual process.
*   **Score 2:**
    • Software assurance related to DevSecOps metrics are defined and collected.
    • Baseline and threshold levels for software assurance are established.
    • Metrics are tracked over time and made available to all stakeholders as needed.
    • Results of system functional testing are collected and periodically analyzed.
    • Known vulnerabilities in all components that make up the DevSecOps system are periodically collected and analyzed.
    • Processes and policies are in place to periodically compare present metrics to past and make adjustments as necessary.
    • Processes and policies are in place and reviewed periodically.
    • Reports are reviewed from all software assurance products.
    • Processes and policies are in place to identify when the level of software assurance implied by captured metrics and reports exceeds the organization's threshold and to make adjustments as necessary.
*   **Score 3:**
    • The organization has established a comprehensive risk analysis and management program.
    • Software assurance metrics, reporting, and analysis are incorporated into the risk management process.
    • Results of the risk management process are incorporated into software assurance policies and procedures.
    • Software assurance metrics and thresholds are periodically updated as a result of risk management activities.
    • The organization prioritizes software assurance tasks based on the level of risk to the organization.
*   **Score 4:**
    • All software assurance tools, or as many as are feasible, are run continuously and reports are disseminated automatically to all relevant stakeholders.
    • Software that fails to meet the organization's software assurance thresholds is automatically prevented from being delivered or deployed.
    • Automated procedures are in place to remediate software assurance issues found within the operating DevSecOps system.
*   **Score 5:** _WIP — maturity scores to be defined_

##### 1.7.1.10 Quality Assurance

*   **Score 1:**
    • All relevant stakeholders associated with the products and services associated with the product under development and the system that supports it have been identified.
    • All relevant stakeholder expectations and regulatory requirements are documented.
    • Policies and procedures are developed and documented to describe how the DevSecOps processes and tools are required to be used in order to meet all relevant stakeholder requirements.
    • Documented policies and procedures may use a traditional document-centered approach, and dissemination may be a manual process.
    • All current policies and procedures are readily available to all personnel.
*   **Score 2:**
    • Automated tools are used to maintain configuration control of policies and procedures.
    • All relevant stakeholders are automatically notified of changes to policies and procedures.
    • Independent resources have been identified and a plan exists to review or audit activities that have been defined within the documented policies and procedures.
    • DevSecOps processes and tools are periodically audited based on the plan to identify noncompliance with policies and procedures and inadequacies regarding the value stream's ability to consistently produce products and services that meet all relevant stakeholders' expectations and regulatory requirements. The audits may be conducted manually, use automation, or a combination of both.
    • All identified noncompliance and inadequacies are independently documented, reported to relevant stakeholders, and tracked to closure.
*   **Score 3:**
    • DevSecOps tools are configured to automatically enforce policies and procedures as a product under development progresses through the system.
    • Automated processes are monitored by an independent resource in order to detect and report noncompliance issues to all relevant stakeholders.
    • Noncompliance and inadequacy issues identified through automated or manual auditing are documented and tracked to closure using an automated issue tracking system that is consistent with the tools used for all other planning and tracking purposes, in order to integrate all efforts that must be planned and tracked to completion.
    • All quality assurance tools, such as origin and static analysis tools, are fully integrated into the system's pipeline, and associated policies are automatically enforced as the product under development progresses through the system.
    • The system automatically monitors and enforces compliance to defined quality criteria as defined for both the product under development and the system regarding the implementation of enhancements and modifications.
*   **Score 4:**
    • All automated activities are continuously being audit for noncompliance issues through the use of automated tools, with regards to both the system and product under development.
    • Results from the automated auditing tools are automatically reported to all relevant stakeholders to ensure the quality of the automated auditing process, in addition to tracking noncompliance issues to resolution.
    • The system automatically identifies and tracks when the defined quality criteria have not been met or the automated quality controls have been bypassed. All relevant stakeholders will be automatically notified and the noncompliance issue will be tracked to closure.
*   **Score 5:** _WIP — maturity scores to be defined_
