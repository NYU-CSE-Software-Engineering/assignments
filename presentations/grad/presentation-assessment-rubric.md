# Project Assessment Rubric
## Project Presentation
### Introduction
The presentation will be scored based on the rubric items shown below. The rubric scoring range is between 0 and 40 points (eight sections, each scored 0-5). Where a section contains several criteria, the criteria are considered together to arrive at a single score for that section. As noted in the Presentation Guidelines, the team score may be modified for any team member who is absent, late, or does not participate roughly equally in the presentation.

### Scoring Scale
| Score | Label | Meaning |
|---|---|---|
| 5 | Exemplary | All required elements are present and presented with depth, insight, and clear rationale. The team goes beyond describing *what* was built to explaining *why* (design decisions, trade-offs, justifications, planned or cut features), and the delivery is clear, engaging, and readable to the audience. |
| 4 - 3 | Meets Requirement | All required elements are present, correct, and adequately explained. The content is accurate and clear, but it is more descriptive than analytical, with limited discussion of rationale or trade-offs. A **4** has only minor gaps in depth or polish; a **3** fully satisfies the requirement and nothing more. |
| 2 - 1 | Partially Meets | One or two required elements are missing, vague, or superficial. Explanations may be incomplete, partly incorrect, hard to follow (e.g., unreadable diagrams), or lack justification. A **2** has most elements present but weakly developed; a **1** has only fragments of the required content. |
| 0 | Unsatisfactory | Core required content is missing, not addressed, or fundamentally incorrect, so the criterion cannot be evaluated. |

### Section I: Content & Structure (Adherence to Guidelines) (0-5 points)
| Criterion | Exemplary (5) | Satisfactory (4-3) | Developing (2-1) | Unsatisfactory (0) |
|---|---|---|---|---|
| **Introduction & Overview** | All required elements (team name, app name, and every team member's role and significant feature contributions) are clearly and engagingly presented. The Project Overview acts as a compelling "elevator pitch" that explains the problem, who it is for, and why it matters. | All required elements for the Introduction and Project Overview are present: every member is introduced with their role, and the problem solved and why the project matters are addressed. | One or two required elements are missing (e.g., some members' contributions, or the problem statement), or the pitch fails to engage the audience. | Core information (team/app name, project goal) is missing, or multiple members are not introduced. |
| **Market Context & Business Model** | Target users and existing alternatives are clearly identified, with a concise statement of how the product differs. The subscription tiers are tied directly to the product's value proposition, with a convincing rationale for what each tier includes. | Target users and the subscription tiers are described, and a basic rationale for the tier split is given. | Target users or the tier rationale are vague, or the tiers are listed without explaining why they are structured that way. | Market context and business model are not addressed. |
| **Key Functionality Overview** | Key/main functionality is insightfully discussed, with clear, concise reasoning for its inclusion and a mention of planned/cut features (and any stretch goals, such as a mobile client that consumes the same API). | Key/main functionality is summarized, and the importance of each part is adequately explained. | Summary of functionality is vague or incomplete, or the discussion of why features were included is missing. | Key functionality is not included in the presentation. |

### Section II: Architecture and Data Flow (Technical Depth) (0-5 points)
| Criterion | Exemplary (5) | Satisfactory (4-3) | Developing (2-1) | Unsatisfactory (0) |
|---|---|---|---|---|
| **REST/Non-REST Endpoints** | A concise list of all primary RESTful resources/actions is provided with HTTP verbs mapped to controller actions, success and error status codes, and any versioning strategy. All non-RESTful endpoints are clearly justified by specific business requirements. | Primary RESTful resources and supported actions are mapped correctly, and any custom non-RESTful routes are identified and justified. | Mapping of RESTful resources is incomplete or confusing, status codes are not discussed, and/or non-RESTful routes are used without adequate justification. | Architecture is not discussed, or the RESTful/non-RESTful mapping is fundamentally incorrect. |
| **Models, Views, and Controllers (MVC)** | Roles of MVC are expertly explained, and the most important Models are detailed, including complex associations and key business logic (scopes/validations). Any service/business-logic layer and the view rendering strategy are explained with clear rationale. | The flow and roles of MVC are clearly explained, and the two to three most important Models are discussed, detailing their associations and custom logic. A key custom controller action and the view strategy are described. | Explanation of the MVC flow is superficial, or the discussion of Model associations, business logic, or view strategy is limited or incorrect. | No clear explanation of the MVC flow, or important model depth is omitted. |
| **Database Schema** | A simplified, highly readable diagram is included and used to explain design decisions (indexing, constraints, complex data types, multi-tenancy, or polymorphic associations). The use of migrations to version-control the schema is explained, including a notable migration challenge. | A simplified, readable diagram of core tables and relationships is included and discussed, and the use of migrations is described. | A diagram is included but is difficult to read from the back, or design decisions (indexing, constraints, complex types) and migrations are not explained. | No database schema diagram is included in the presentation. |

### Section III: Core Requirements Deep Dive (0-5 points)
| Criterion | Exemplary (5) | Satisfactory (4-3) | Developing (2-1) | Unsatisfactory (0) |
|---|---|---|---|---|
| **Role-Based Access Control (RBAC)** | At least three roles and their permission hierarchy are clearly shown (table or diagram). The enforcement mechanism (e.g., Pundit, CanCanCan, custom policies) and the layers where it is applied are explained, along with evidence that lower-privileged roles cannot reach higher-privileged functionality. | At least three roles and their hierarchy are shown, and the enforcement mechanism is identified and explained. | Roles are listed without a clear hierarchy, or enforcement is unclear, inconsistent, or not verified. | Fewer than three roles are implemented, or RBAC is not discussed. |
| **Authentication & Security** | The authentication approach (e.g., JWT with secure HTTP-only cookies, or OAuth 2.0/SSO) is justified against alternatives. Password hashing and the session/token lifecycle (issuance, expiration, revocation) are explained, and additional security measures are tied to the specific threats they address. | The authentication approach and password hashing are clearly described, and at least one additional security measure is discussed. | Discussion is superficial; the token/session lifecycle or the threats addressed are not explained. | Authentication and security are not discussed, or described practices are not industry-standard (e.g., unhashed passwords). |
| **Non-Trivial External API Integration** | The integration is clearly non-trivial (two-way communication or complex data processing) and meaningful to the product. The data flow is explained, failure modes (timeouts, retries, rate limits, unexpected responses, cost, credentials) are addressed, and testing without the live service is described. | A non-trivial integration is identified and its data flow explained, with some discussion of failure handling or testing. | The integration is described but appears trivial or read-only, or failure handling and testing are not addressed. | No external API integration is presented, or it is limited to a simple read-only widget. |
| **Subscription Tiers & Feature Toggling** | At least two tiers and their entitlements are clearly described. Programmatic enforcement (where the logic lives) is explained, including behavior on upgrade, downgrade, and exceeding a limit. Mocked/test-mode payment is acknowledged, with what would change for production. | At least two tiers are described, and programmatic enforcement of tier restrictions is explained. | Tiers are described, but enforcement is unclear, incomplete, or appears to be only cosmetic (e.g., hidden UI elements). | No tiers are implemented, or restrictions are not enforced programmatically. |
| **Usage Tracking & Auditing** | What is tracked and why is clearly explained (billing/usage metrics or security audit trail). The implementation, storage, and how the data is surfaced to admins or users are described, along with performance or data-growth considerations. | Tracked actions or metrics and the implementation approach are clearly described. | Tracking is minimal, or it is unclear how it is implemented or surfaced. | No usage tracking or auditing is implemented or discussed. |
| **Documented RESTful API** | OpenAPI/Swagger documentation is shown, and how it is generated and kept in sync with the code is explained. API design choices (resource naming, verbs, status codes, pagination/filtering, error format, API authentication) are highlighted and justified. | OpenAPI/Swagger documentation is shown, and how it is generated or maintained is explained, with some design choices discussed. | Documentation is partial or its generation/maintenance is not explained, or API design choices are not discussed. | No OpenAPI/Swagger documentation exists, or the API is not discussed. |

### Section IV: Implementation & Production Readiness (0-5 points)
| Criterion | Exemplary (5) | Satisfactory (4-3) | Developing (2-1) | Unsatisfactory (0) |
|---|---|---|---|---|
| **Key Gems and External Services** | The three most critical non-standard gems are discussed, including their purpose, high impact, and clear examples of how they saved time or enabled key features. The alternatives considered and the trade-offs or risks of each choice are explained. | Three critical non-standard gems are discussed, covering their purpose and general impact on the project. | Fewer than three gems are discussed, or purpose and impact are superficial, with no discussion of alternatives or trade-offs. | This section is omitted, or only default Rails gems are discussed. |
| **Testing & Quality Assurance** | The testing strategy (types of tests, coverage goals and results, CI if used) is detailed, including how RBAC rules, tier restrictions, and the external API integration were specifically tested, and how testing ensured stability. | The testing strategy (types of tests) and coverage goals or results are clearly described. | Description of testing is superficial, or the testing of key requirements (RBAC, tiers, external API) is not addressed. | No discussion of testing strategy. |
| **Deployment & Production Environment** | The deployment pipeline and hosting platform are detailed, highlighting key challenges and differences between development and production (e.g., secrets, asset compilation, caching, background workers, migrations on deploy, webhooks). | The deployment process and hosting platform are clearly described. | The deployment process is only briefly mentioned without addressing production challenges. | No discussion of the deployment pipeline. |

### Section V: Demo of Key Functionality (0-5 points)
| Criterion | Exemplary (5) | Satisfactory (4-3) | Developing (2-1) | Unsatisfactory (0) |
|---|---|---|---|---|
| **Demo Execution & Value Proposition** | The live demo is smooth, highly efficient, and flawlessly showcases the biggest and most important features and the core value proposition of the SaaS application. Any technical issue is handled gracefully with a prepared backup (screenshots or recording). | The live demo is functional, focuses on key features, and walks the audience through the main user workflows. | Demo is disorganized, includes unnecessary features (like sign-up), or encounters multiple minor technical errors with no contingency. | The demo is non-functional, or core features cannot be successfully demonstrated. |
| **Personas, Roles & Tiers** | The demo is structured around pre-configured personas and makes the role hierarchy and subscription tiers clearly visible (e.g., the same feature behaving differently for Free and Pro users, or moderator versus admin capabilities). | Multiple personas are used, and differences between roles or tiers are shown. | Personas are used inconsistently, or the role hierarchy and tier differences are not clearly visible. | Only a single persona is shown, or roles and tiers are not demonstrated. |
| **Requirements in Action** | The demo seamlessly shows (1) the external API integration at work, (2) a tier restriction or usage limit being enforced, (3) the audit log or usage tracking reflecting the actions just performed, and (4) the OpenAPI documentation or an API client call. If OAuth is used, it is highlighted and discussed. | The demo shows at least three of the four required elements. | The demo shows only one or two of the required elements. | None of the required elements are demonstrated. |
| **Deployed Application & Evaluator Access** | The application is deployed and reachable at the URL provided in advance, the three evaluator accounts (one per role) work as provided, and the application remains deployed for the required 7 days following the presentation. | The application is deployed and accessible, and evaluator accounts work, with minor issues quickly resolved. | The URL or accounts were provided late, an account is missing a role or does not work, or access problems affect evaluation. | The application is not deployed, or evaluators cannot access it. |

### Section VI: Concluding Remarks & Reflection (0-5 points)
| Criterion | Exemplary (5) | Satisfactory (4-3) | Developing (2-1) | Unsatisfactory (0) |
|---|---|---|---|---|
| **Concluding Remarks & Reflection** | A single, high-impact item is provided for each of the three required areas (Success, Challenge, Lesson Learned) and demonstrates deep, non-generic insight into the development process. The Lesson Learned clearly follows from the Challenge. | A clear, distinct item is provided for each of the three required areas (Success, Challenge, Lesson Learned). | One or two of the three required reflection items are missing, or the answers are generic (e.g., "We communicated well"). | The Concluding Remarks section is rushed, incomplete, or entirely missing. |

### Section VII: Q&A Engagement (0-5 points)
| Criterion | Exemplary (5) | Satisfactory (4-3) | Developing (2-1) | Unsatisfactory (0) |
|---|---|---|---|---|
| **Q&A Engagement** | The team is highly prepared, confidently and effectively answering all questions from the class and evaluators, often preemptively assigning experts to handle specific domains. Answers are shared across team members. | The team answers questions clearly and maintains a professional demeanor, demonstrating a comprehensive understanding of the project. | Answers are hesitant, vague, or one team member dominates the Q&A section, or the team fails to embrace critical analysis professionally. | The team cannot answer basic questions about their design choices or technology stack. |
| **Depth of Reasoning** | Answers consistently explain why decisions were made, including alternatives rejected, trade-offs accepted, and security implications, and candidly acknowledge limitations. | Answers explain the reasoning behind key design decisions and show an understanding of the technology stack. | Answers describe what was built, but not why, or alternatives and trade-offs are not considered. | The team cannot explain the reasoning behind their design choices. |

### Section VIII: Professionalism & Presentation Delivery (0-5 points)
| Criterion | Exemplary (5) | Satisfactory (4-3) | Developing (2-1) | Unsatisfactory (0) |
|---|---|---|---|---|
| **Clarity, Pacing, and Timing** | The presentation is smooth, clear, and easy to understand from the back of the room. The team adheres closely to the 50-minute presentation limit (excluding the 10-minute Q&A) and closely to the individual section time allocations (+/- 1-2 minute deviations). | The presentation is clear and generally well-paced. The team deviates from the 50-minute limit (excluding the 10-minute Q&A), and/or the individual section timing (+/- 3-4 minute deviations). | Delivery is inconsistent (e.g., reading from cards, mumbling), or the presentation significantly runs over the time limits. | Presentation is completely disorganized, incomprehensible, or cut off due to excessive length. |
| **Team Participation & Presence** | All team members who are present are on time, present for roughly equal time (as measured by the evaluators' timing), and maintain professional conduct throughout (not on phone/laptop/etc.). The team is able to continue seamlessly if a member is missing. | All team members who are present are on time and present for an adequate, though not roughly equal, amount of time. | One team member presents for a disproportionately small amount of time, or non-speaking members block the screen or interrupt/distract from the presentation. | Professional conduct is not maintained. The presentation is not a serious endeavor. |

### Score Summary - Project Presentation (35%)
 
| # | Criterion | Score (0-5) |
|---|---|---|
| 1 | Introduction & Overview | |
| 2 | Market Context & Business Model | |
| 3 | Key Functionality Overview | |
| 4 | REST/Non-REST Endpoints | |
| 5 | Models, Views, and Controllers (MVC) | |
| 6 | Database Schema | |
| 7 | Role-Based Access Control (RBAC) | |
| 8 | Authentication & Security | |
| 9 | Non-Trivial External API Integration | |
| 10 | Subscription Tiers & Feature Toggling | |
| 11 | Usage Tracking & Auditing | |
| 12 | Documented RESTful API | |
| 13 | Key Gems and External Services | |
| 14 | Testing & Quality Assurance | |
| 15 | Deployment & Production Environment | |
| 16 | Demo Execution & Value Proposition | |
| 17 | Personas, Roles & Tiers | |
| 18 | Requirements in Action | |
| 19 | Deployed Application & Evaluator Access | |
| 20 | Concluding Remarks & Reflection | |
| 21 | Q&A Engagement | |
| 22 | Depth of Reasoning | |
| 23 | Clarity, Pacing, and Timing | |
| 24 | Team Participation & Presence | |
| | **Presentation Total** | **____ / 120** |
| | **Section Total (total \* .35)** | **____ / 100** |

## Project Implementation
### Introduction
This rubric evaluates a team's final project implementation against the minimum core requirements for the semester. Each criterion is scored on a 0-4 scale. Evaluate what is demonstrated in the running application, the repository, and the live demo, not what is only claimed in the README or slides.

### Scoring Scale
| Score	| Label	| Meaning |
|---|---|---|
| 4	| Exceeds Requirement	| The requirement is fully met, and the team went beyond the minimum with polish, depth, robustness, or professional-grade practices. |
| 3	| Meets Requirement	| The requirement is fully and correctly met as stated. This is the expected target for every row. |
| 2	| Partially Meets	| A real attempt is evident and parts work, but the requirement is incomplete, inconsistent, or has significant flaws. |
| 1	| Minimally Meets	| Only a token or superficial effort is evident. The requirement is largely unmet. |
| 0	| Does Not Meet	| The requirement is absent, non-functional, or cannot be demonstrated. |

### Section I: Core Platform
 
| Criterion | Exceeds (4) | Meets (3) | Partially Meets (2) | Minimally Meets (1) | Does Not Meet (0) |
|---|---|---|---|---|---|
| **Ruby on Rails Back End & HTML Web Interface** | Back end is built in Ruby on Rails and follows Rails conventions and good design (thin controllers, logic in models/service objects/concerns, sensible use of gems). The HTML interface is coherent, usable, and exposes all core features. | The back end is built in Ruby on Rails and uses MVC and Rails conventions correctly. A functional HTML web interface exposes the core features of the application. | Application runs on Rails but has significant convention misuse (e.g., business logic in views or controllers), or the HTML interface covers only some core features. | Rails application barely runs or has minimal functionality, or the HTML interface is largely non-functional. | Back end is not Ruby on Rails, or there is no working application to evaluate. |

**Evidence to verify:** `Gemfile`, `config/routes.rb`, controller/model organization, live demo of the HTML interface.

### Section II: Access Control, Authentication & Security
 
| Criterion | Exceeds (4) | Meets (3) | Partially Meets (2) | Minimally Meets (1) | Does Not Meet (0) |
|---|---|---|---|---|---|
| **Role-Based Access Control (RBAC)** | At least three distinct roles with a clear permission hierarchy, enforced consistently at every layer (controllers, API, and views) using a policy approach. Unauthorized access returns correct 401/403 responses. Admins can manage roles through the application. | At least three distinct roles with hierarchical permissions (e.g., Admin, Moderator/Support, Standard User, or Admin, Pro, Free). Permissions are enforced **server-side** on all major protected actions, and boundaries between roles are correct. | Three roles are defined, but enforcement is incomplete or inconsistent (e.g., checks only hide UI elements, the hierarchy is not respected in some actions), or only two roles are meaningfully distinct. | Roles exist in the data model, but permission checks are rare or mostly missing. | No roles, or fewer than two roles exist. |
| **Modern Authentication & Security** | Registration, login, logout, and session management use JWT in secure HTTP-only cookies or OAuth 2.0 SSO. Passwords are hashed with bcrypt/Argon2. Additional hardening is present (e.g., token expiry/refresh/revocation, Secure and SameSite cookie flags, CSRF protection, rate limiting, email confirmation). Secrets are kept out of the repository. | Secure registration, login, and session management using JWT with HTTP-only cookies or OAuth 2.0 (Google, GitHub, etc.). Passwords are securely hashed (bcrypt/Argon2) before storage. Protected endpoints reject unauthenticated requests. No secrets are committed to the repository. | Authentication works but has notable weaknesses (e.g., JWT stored in localStorage or a non-HTTP-only cookie, no token expiration, weak or missing CSRF handling, hard-coded secrets). | Authentication exists but is fundamentally weak (e.g., home-rolled scheme, easily forged sessions, several endpoints unprotected). | No authentication, or passwords are stored in plaintext or in a reversible form. |

**Evidence to verify:** role definitions and policy/ability files, attempts to access restricted actions as a lower-privilege user (UI **and** direct API calls), cookie flags in browser dev tools, `password_digest` in the schema, `git log`/repo scan for committed secrets.

### Section III: Data Layer
 
| Criterion | Exceeds (4) | Meets (3) | Partially Meets (2) | Minimally Meets (1) | Does Not Meet (0) |
|---|---|---|---|---|---|
| **Persistent Storage & Migrations** | A relational SQL database with a well-designed, normalized schema. All schema changes are versioned through Rails migrations that run cleanly from scratch and are reversible. Constraints (foreign keys, NOT NULL, unique indexes) and indexes on key query paths are present. Seed data supports demonstration. | A relational SQL database with a formal schema. All schema changes are made through Rails migrations that run cleanly from scratch. Relationships and basic constraints are correct. | Database and migrations are present, but the schema has missing constraints or relationships, migrations were edited after the fact, or the schema was changed outside migrations. Migrations may not run cleanly from scratch. | Minimal schema that poorly supports the application's features. Migrations are mostly absent, or the schema was modified manually. | No relational database or no migration system (e.g., flat files or in-memory data only). |
 
**Evidence to check:** `db/migrate/`, `db/schema.rb` (or `structure.sql`), a fresh `rails db:drop db:create db:migrate` run, which database adapter is configured.
 
### Section IV: REST API & Documentation
 
| Criterion | Exceeds (4) | Meets (3) | Partially Meets (2) | Minimally Meets (1) | Does Not Meet (0) |
|---|---|---|---|---|---|
| **RESTful API Design** | Resource-oriented routing, correct HTTP verbs, and precise status codes (e.g., 200 / 201 / 204 / 400 / 401 / 403 / 404 / 422) used consistently. Consistent JSON response and error formats. Includes additional design maturity such as pagination, filtering, or versioning. The API clearly covers all core features. | Cleanly designed REST API with resource-based routes, appropriate HTTP verbs, appropriate status codes, and consistent JSON responses. It covers the application's core functionality. | API is mostly RESTful but has inconsistencies (e.g., verbs in URLs, returning 200 for errors, inconsistent response shapes) or has gaps in coverage of core features. | Few endpoints, mostly RPC-style routes, or status codes are largely incorrect. | No API is exposed. |
| **OpenAPI / Swagger Documentation** | OpenAPI spec is **automatically generated** (e.g., rswag or equivalent) and served through an interactive UI. It documents all endpoints, parameters, request/response schemas, authentication, and error responses, with examples. Documentation stays in sync with the code (e.g., generated from request specs). | OpenAPI/Swagger documentation is automatically generated and accessible. It covers all endpoints with parameters and response schemas. | Documentation exists but covers only part of the API, is hand-written and stale, or is missing schemas or authentication details. | Documentation is a stub or covers only a handful of endpoints with little useful detail. | No OpenAPI/Swagger documentation. |
 
**Evidence to check:** `rails routes`, calling endpoints with curl/Postman and inspecting status codes and error bodies, the Swagger UI URL, whether the spec file is generated or hand-edited.  URL to API documentation is provided by the team prior to the start of the presentation.

### Section V: External Integration
 
| Criterion | Exceeds (4) | Meets (3) | Partially Meets (2) | Minimally Meets (1) | Does Not Meet (0) |
|---|---|---|---|---|---|
| **Non-Trivial External API Integration** | At least one external API is integrated in a way that is central to the product's value, involving complex data processing or two-way communication (e.g., Stripe checkout plus webhooks, Twilio send and receive, an LLM API with structured prompt/response handling). Includes robust error handling (timeouts, retries, failure states), secured credentials, and webhook signature verification where applicable. Integration is covered by tests using stubs/mocks (e.g., WebMock/VCR). | At least one external API is integrated meaningfully, with complex data processing or two-way communication. Failures are handled gracefully, credentials are secured, and the integration works in the demo. | Integration exists but is shallow (mostly one-way fetch and display, or a thin pass-through wrapper), is fragile (little or no error handling), or is only partially functional. | Integration is trivial or read-only (e.g., a weather or stock widget), or the "integration" is entirely faked with no real call path. | No external API is used. |
 
**Evidence to check:** the service/client code, how API keys are stored (credentials/ENV), webhook endpoints, behavior when the external API is unavailable or returns an error, live demonstration of the full round trip.
 
### Section VI: Business Logic: Tiers & Auditing
 
| Criterion | Exceeds (4) | Meets (3) | Partially Meets (2) | Minimally Meets (1) | Does Not Meet (0) |
|---|---|---|---|---|---|
| **Subscription Tiers & Feature Toggling** | At least two tiers with premium features **and** usage limits enforced server-side through a centralized, maintainable mechanism (e.g., entitlements, policy objects, feature flags). Upgrade and downgrade flows work (payments mocked or in test mode) and handle their effect on existing data. Users receive clear feedback when blocked by a tier limit. | At least two service tiers (e.g., Free and Pro). At least one premium feature or usage limit is programmatically restricted based on the active tier. Users can change tiers (payment mocked or in test mode). | Tiers exist, but gating is incomplete, enforced only in the UI, scattered or inconsistent in the code, or upgrade/downgrade does not work reliably. | A tier attribute exists on the user or tenant, but little or no application behavior depends on it. | No subscription tiers. |
| **Usage Tracking or Auditing** | Key user actions or usage metrics are recorded persistently with actor, action, target resource, timestamp, and useful metadata (e.g., IP, before/after values). Records are viewable by an authorized role with filtering or summarization, and the log is protected from tampering. Usage data feeds billing or tier-limit enforcement. | Key user actions or usage metrics are recorded persistently, including at least who, what, and when. Records are accessible to an authorized role (UI, API, or admin console). | Tracking exists but is incomplete (covers few actions, missing actor or timestamp), is not viewable by anyone through the application, or is applied inconsistently. | Minimal tracking (e.g., only the default Rails log, or a single action tracked). | No usage tracking or auditing. |
 
**Evidence to check:** where tier checks occur in the code (model, policy, controller, or only the view), attempts to exceed a free-tier limit via the API directly, the audit/usage table in the schema, a demonstrated action that produces a log entry.

### Score Summary - Project Implementation (65%)
 
| # | Criterion | Score (0-4) |
|---|---|---|
| 1 | Ruby on Rails Back End & HTML Web Interface | |
| 2 | Role-Based Access Control (RBAC) | |
| 3 | Modern Authentication & Security | |
| 4 | Persistent Storage & Migrations | |
| 5 | RESTful API Design | |
| 6 | OpenAPI / Swagger Documentation | |
| 7 | Non-Trivial External API Integration | |
| 8 | Subscription Tiers & Feature Toggling | |
| 9 | Usage Tracking or Auditing | |
| | **Implementation Total** | **____ / 36** |
| | **Section Total (total \* .65)** | **____ / 100** |
 
