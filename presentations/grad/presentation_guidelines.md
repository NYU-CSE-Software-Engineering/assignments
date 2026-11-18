# Project Presentation Guidelines
## Introduction
Create a presentation of your team project using the following guidelines. The presentation should showcase what the team built, the technologies used in doing so, what works, what does 
not work, what the team completed or failed to complete, where the project can go (if the team chooses to continue it), and what you would do differently. As this is a graduate course, evaluators 
expect you to go beyond what you built and explain why you made key design decisions, which alternatives you considered, and what trade-offs you accepted. The presentation should run 50 minutes and is followed 
by a 10-minute Q&A with the entire class.

As per our syllabus, _"Participation of all team members is required. Failure to attend and participate equally will result in a 0 grade for the presentation."_
It is expected that each team member will participate in the presentation for roughly equal presentation time.  We strongly suggest practicing your presentation to ensure this requirement is met. The evaluation
team will  be timing each member of the team during the presentation. While the rubric reflects the presentation as a whole for the team, the grade may be modified for any team member who is not present, late, or
does not equally participate in the presentation. The team should be prepared to complete the entire presentation if one or more members are missing.

At the time of the presentation, the project will be deployed and hosted (your choice of where/how) so that the evaluation team can utilize the application. Provide the URL to the application in advance, and have
made  3 user accounts (one of each role for the evaluation team). These accounts will also be provided in advance of the presentation. The presentation must remain deployed for 7 days following the
presentation for evaluation purposes.

## Timing Summary
| Section | Slides | Time
|---|---|---|
| Introduction| 1-2| ~2 min|
| Project Overview| 2-3| ~3 min|
| Key Functionality Overview| 2-3| ~3 min|
| Application Architecture and Data Flow| 5-7| ~7 min|
| Core Requirements Deep Dive| 7-10| ~10 min|
| Implementation Details and Production Readiness| 3-6| ~6 min|
| Demo of Key Functionality| 0| ~10 min|
| Concluding Remarks| 1-2| ~4 min|
| Total presentation| | 45 min|
| Questions and Answers| 0| ~5 min|

## Introduction - 1-2 slides, ~2 minutes
The introduction should include the team name (if applicable), the name of the application (e.g., BlueBonnet), and an introduction of each team member. Briefly mention the type of work each member did 
(backend development, database, API design, integrations, frontend development, DevOps, etc.) as well as the features each member owned or contributed to in a significant way.

## Project Overview - 2-3 slides, ~3 minutes
Provide an overview of the system you designed and built. Why did you decide to implement this application? What problem does it attempt to solve, and for whom? Think of this as your elevator pitch for 
possible investors. Grab the audience's attention and get them interested in your work. Why should we care about this project?

- **Market Context**: Briefly identify the target users or customers and how this problem is addressed today. A single sentence on how your product differs from existing alternatives is sufficient.
- **Business Model**: Explain how the subscription tiers support the product's value proposition (e.g., what a Free user gets versus a Pro user, and why that split makes sense).

Screenshots (images of the application) are appropriate here; live demos will occur later.

## Key Functionality Overview - 2-3 slides, ~3 minutes
Discuss the key/main functionality of the system. Summarize what each part does and why it was important to build it or include it in the system. Time and space permitting, include a short discussion of what 
functionality was cut from the system and/or what functionality was not fully implemented or not included (but should have been). If the team pursued a stretch goal such as a mobile client, mention it here 
and note that it consumes the same API endpoints as the web interface.

## Application Architecture and Data Flow - 5-7 slides, ~7 minutes
This section should clearly explain the core components of your Rails application and demonstrate how data flows through the system.
 
- **RESTful Endpoints**
  - **Mapping**: Present a concise list or table of the _primary_ RESTful resources (e.g., /users, /projects/:id, /tasks) implemented in your application.
  - **Actions**: For each resource, map the supported HTTP verbs (GET, POST, PUT/PATCH, DELETE) to the corresponding controller actions and their purpose. Note the status codes returned for success and for common
    error cases, and any API versioning strategy.

- **Models, Views, and Controllers (MVC)**
  - **The Flow**: Clearly explain the role of the Models, Views, and Controllers in your system and how they interact to serve a request.
  - **Model Depth**: Discuss the two or three most important Models in your application. Detail their associations (e.g., `has_many`, `belongs_to`) and any custom scopes or validation rules that enforce business logic.
  - **Controller Logic**: Highlight any key custom action (one that goes beyond the standard 7 RESTful actions) in a Controller and explain why it was necessary.
  - **Service/Business Logic Layer**: If you used service objects, concerns, or other patterns to keep controllers and models thin, explain what you extracted and why.
  - **View Strategy**: Discuss the strategy used for rendering views (e.g., standard ERB, partial views, Hotwire/Turbo/Stimulus, or a frontend framework).

- **Database Schema**
  - **Requirement**: Include a simplified diagram of the core database tables and their relationships. This is essential for demonstrating data architecture.
  - **Focus**: Explain design decisions concerning indexing, constraints (foreign keys, uniqueness, null rules), complex data types, multi-tenancy, or polymorphic associations.
  - **Migrations**: Describe how migrations were used to version-control schema changes, including any notable migration that required careful handling (e.g., backfilling data or changing a column on a
    populated table).

## Core Requirements Deep Dive - 7-10 slides, ~10 minutes
This section demonstrates how the team met each of the project's core technical requirements. For each topic, explain your approach, the design decisions and alternatives you considered, and any limitations. 
Allocate time according to where your team invested the most effort. Not every topic needs equal time, but every topic must be addressed.

- **Role-Based Access Control (RBAC)**
  - Identify the three roles in your system and show the permission hierarchy, either as a table or a diagram.
  - Explain how authorization is enforced (e.g., Pundit, CanCanCan, or custom policies) and where it is enforced (controllers, policies, views, API layer). Explain how you verified that a lower-privileged role 
    cannot reach higher-privileged functionality.

- **Authentication and Security**
  - Describe your authentication approach (e.g., JWT with secure HTTP-only cookies, or OAuth 2.0/SSO with a provider such as Google or GitHub) and why you chose it over the alternatives.
  - Explain how passwords are hashed and stored (e.g., bcrypt/Argon2), and how sessions or tokens are issued, expired, and revoked.
  - Discuss other security measures you applied and the threats they address (e.g., CSRF protection, strong parameters, secrets management, rate limiting, input validation, SQL injection and XSS defenses).

- **Non-Trivial External API Integration**
  - Identify the external API(s) (e.g., Stripe, Twilio, SendGrid, an LLM API) and explain why the integration is meaningful to the product.
  - Describe the data flow, including any complex data processing or two-way communication (e.g., webhooks, callbacks, streaming responses, or asynchronous processing via background jobs).
  - Discuss how you handled failure modes: timeouts, retries, rate limits, invalid or unexpected responses, API cost, and credential management. Explain how the integration is tested without calling the live
    service (e.g., stubbing, VCR/WebMock, or sandbox/test mode).

- **Subscription Tiers and Feature Toggling**
  - Describe the service tiers (at least two) and what each one allows.
  - Explain how tier restrictions are enforced programmatically (feature flags, usage limits, policy checks) and where that logic lives. Explain how the system behaves when a user upgrades, downgrades, or
    exceeds a limit.
  - If payment processing is mocked or in test mode, say so and describe what would change to move to production.

- **Usage Tracking and Auditing**
  - Describe what is tracked (e.g., API call counts for billing, or an activity log of who changed or deleted a resource) and why.
  - Explain the implementation (e.g., an audit gem such as PaperTrail or Audited, custom event models, or middleware), how the data is stored, and how it is surfaced to admins or users. Discuss any
    performance or data-growth considerations.

- **Documented RESTful API**
  - Show how the API is documented using OpenAPI/Swagger (e.g., rswag or a similar tool) and how the documentation is generated and kept in sync with the code. A screenshot of the rendered
    documentation is appropriate.
  - Highlight design choices such as resource naming, use of HTTP verbs and status codes, pagination, filtering, error response format, and authentication of API requests.

## Implementation Details and Production Readiness - 3-6 slides, ~6 minutes
This section focuses on the specific tools and processes that shaped the final product.
- **Key Gems and External Services**
  - Discuss the three most critical non-standard gems your team used (i.e., beyond the default Rails gems). Gems already covered in the Core Requirements section (e.g., an authorization or API documentation
    gem) may be counted here, but discuss them from the perspective of the decision to adopt them rather than repeating the implementation details. For each, explain:
    - **Purpose**: What specific problem did the gem solve?
    - **Impact**: How did it save the team time or enable a key feature?
    - **Trade-offs**: What alternatives did you consider, and what risks or limitations came with the choice (maintenance status, complexity, lock-in)?
  - Examples: Gems for authentication, authorization, background jobs (e.g., Sidekiq), testing (e.g., RSpec/FactoryBot), API documentation, or payment processing.

- **Testing and Quality Assurance**
  - **Strategy**: Describe your team's testing strategy. What types of tests were implemented (unit, integration, request/API, feature/system)? How did you test the RBAC rules, tier restrictions, and external
    API integration specifically?
  - **Metrics**: Mention the team's code coverage goals and results and/or how testing helped ensure the application's stability. If you used continuous integration, describe it briefly.

- **Deployment and Environment**
  - **The Pipeline**: Detail your chosen deployment process. Where is the application hosted (e.g., Heroku, Render, Fly.io, etc.) and how are changes deployed?
  - **Production Environment**: Discuss any key differences or challenges in setting up the production environment compared to the development environment (e.g., environment variables and secrets, asset compilation, 
      caching, background workers, database migrations on deploy, webhook endpoints).    

- **Deployment and Environment**
  - **The Pipeline**: Detail your chosen deployment process. Where is the application hosted (e.g., Heroku, etc.)
  - **Production Environment**: Discuss any key differences or challenges in setting up the production environment compared to the development environment (e.g., environment variables, asset compilation, caching).

# **Demo of Key Functionality - 0 slides, ~10 minutes**
Demonstrate the system live, focusing on the key functions and the core value proposition of your SaaS application.
- **Prioritize**: Since time is limited, focus on the biggest and most important features. The goal is to give the audience the best possible overview of the system's capabilities and its primary purpose.

- **Walkthrough**: Guide the audience through the main user workflows that showcase the team's most significant achievements and the unique aspects of the Rails application.

- **Personas**: Use pre-configured user accounts. Structure your demo in terms of different personas (e.g., Platform Admin, Moderator/Support, Standard User; or Admin, Pro User, Free User). Your demo should
  make the role hierarchy and the subscription tiers visible, for example by showing the same feature behaving differently for a Free user and a Pro user, or by showing a moderator's capabilities compared to
  an admin's.

- **Requirements in Action**: The demo should show, at a minimum, (1) the external API integration at work, (2) a tier restriction or usage limit being enforced, and (3) the audit log or usage tracking
  reflecting the actions you just performed. Briefly show the OpenAPI documentation (or an API client call) to demonstrate the REST API.

- **Efficiency**: Avoid spending time on common features like sign-up or basic profile creation, as nearly all teams implement these. If your implementation used an OAuth approach, be sure to highlight
  and discuss it.

- **Contingency**: Have a backup plan (screenshots or a short recording) in case of network or service failures, particularly for external API calls.

## Concluding Remarks - 1-2 slides, ~4 minutes
The conclusion must include a brief, focused reflection on the project's development process. You must provide one single, high-impact item for each of the following three areas.
- ✅ What the Team Did Correctly (Success)
  - Identify the single most impactful technical or process decision that contributed significantly to the project's success or stability. This should be a decision unique to your team and project, not a
    generic statement.
  - Example Focus: Choosing a specific Rails gem (like Stimulus for the frontend), a successful database design pattern, a clean approach to enforcing tier restrictions, or an effective deployment strategy.\
    
- ❌ What the Team Did Incorrectly (Challenge)
  - Identify the single greatest challenge, mistake, or technical misstep that consumed the most time, caused the most rework, or negatively affected the final application.
  - Example Focus: An initial misjudgment of a feature's complexity, a critical database migration error, retrofitting authorization late in development, or a flaw in the chosen external API integration.
    
- 🔁 What the Team Would Do Differently (Lesson Learned)
  - Based on the "incorrect" item above, identify the single most important change the team would implement if they could start the project again. This demonstrates a clear lesson learned.
  - Example Focus: "We would have spent one extra sprint designing the payment flow before coding it," or "We would have adopted TDD from week one for our backend models."

If the team plans to continue the project, you may close with one brief slide on future directions (e.g., production payment processing, a mobile client, scaling concerns).

# **Questions and Answers - 0 slides, ~5 minutes**
This dedicated time is for the audience to engage with your team, providing valuable feedback and commentary.
- Engagement and Professionalism
  - **Open Dialogue**: Be prepared for questions regarding your design choices, implementation work, feature set, architecture, security decisions, and technology stack (Rails-specific decisions). At the
    graduate level, expect follow-up questions that probe your reasoning and the alternatives you rejected.
  - **Embrace Analysis**: View critical analysis or suggestions for alternative approaches as a professional opportunity to demonstrate your comprehensive understanding of the project's technical landscape.
  - **Professional Conduct**: Maintain a professional and respectful demeanor regardless of the nature of the question or comment.
    
- Preparation Strategy
  - **Anticipate**: As a team, brainstorm and prepare for the most challenging questions the audience might ask about your application or development process.
  - **Assign Experts**: Proactively identify team members best suited to answer questions in specific areas (e.g., the front-end developer for UX questions, the database designer for schema questions, the
    integration owner for external API questions, or the lead architect for deployment and security strategy). This ensures a clear, confident, and efficient response.
