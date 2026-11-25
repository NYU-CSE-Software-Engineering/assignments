# Project Evaluation Rubric
This rubric evaluates a team's final project implementation against the minimum core requirements for the semester. Each criterion is scored on a 0-4 scale. Evaluate what is demonstrated in the running application, the repository, and the live demo, not what is only claimed in the README or slides.

## Scoring Scale
| Score	| Label	| Meaning |
|---|---|---|
| 4	| Exceeds Requirement	| The requirement is fully met, and the team went beyond the minimum with polish, depth, robustness, or professional-grade practices. |
| 3	| Meets Requirement	| The requirement is fully and correctly met as stated. This is the expected target for every row. |
| 2	| Partially Meets	| A real attempt is evident and parts work, but the requirement is incomplete, inconsistent, or has significant flaws. |
| 1	| Minimally Meets	| Only a token or superficial effort is evident. The requirement is largely unmet. |
| 0	| Does Not Meet	| The requirement is absent, non-functional, or cannot be demonstrated. |

---
 
## I. Core Platform
 
| Criterion | Exceeds (4) | Meets (3) | Partially Meets (2) | Minimally Meets (1) | Does Not Meet (0) |
|---|---|---|---|---|---|
| **Ruby on Rails Back End & HTML Web Interface** | Back end is built in Ruby on Rails and follows Rails conventions and good design (thin controllers, logic in models/service objects/concerns, sensible use of gems). The HTML interface is coherent, usable, and exposes all core features. | The back end is built in Ruby on Rails and uses MVC and Rails conventions correctly. A functional HTML web interface exposes the core features of the application. | Application runs on Rails but has significant convention misuse (e.g., business logic in views or controllers), or the HTML interface covers only some core features. | Rails application barely runs or has minimal functionality, or the HTML interface is largely non-functional. | Back end is not Ruby on Rails, or there is no working application to evaluate. |

**Evidence to verify:** `Gemfile`, `config/routes.rb`, controller/model organization, live demo of the HTML interface.

## II. Access Control, Authentication & Security
 
| Criterion | Exceeds (4) | Meets (3) | Partially Meets (2) | Minimally Meets (1) | Does Not Meet (0) |
|---|---|---|---|---|---|
| **Role-Based Access Control (RBAC)** | At least three distinct roles with a clear permission hierarchy, enforced consistently at every layer (controllers, API, and views) using a policy approach. Unauthorized access returns correct 401/403 responses. Admins can manage roles through the application. | At least three distinct roles with hierarchical permissions (e.g., Admin, Moderator/Support, Standard User, or Admin, Pro, Free). Permissions are enforced **server-side** on all major protected actions, and boundaries between roles are correct. | Three roles are defined, but enforcement is incomplete or inconsistent (e.g., checks only hide UI elements, the hierarchy is not respected in some actions), or only two roles are meaningfully distinct. | Roles exist in the data model, but permission checks are rare or mostly missing. | No roles, or fewer than two roles exist. |
| **Modern Authentication & Security** | Registration, login, logout, and session management use JWT in secure HTTP-only cookies or OAuth 2.0 SSO. Passwords are hashed with bcrypt/Argon2. Additional hardening is present (e.g., token expiry/refresh/revocation, Secure and SameSite cookie flags, CSRF protection, rate limiting, email confirmation). Secrets are kept out of the repository. | Secure registration, login, and session management using JWT with HTTP-only cookies or OAuth 2.0 (Google, GitHub, etc.). Passwords are securely hashed (bcrypt/Argon2) before storage. Protected endpoints reject unauthenticated requests. No secrets are committed to the repository. | Authentication works but has notable weaknesses (e.g., JWT stored in localStorage or a non-HTTP-only cookie, no token expiration, weak or missing CSRF handling, hard-coded secrets). | Authentication exists but is fundamentally weak (e.g., home-rolled scheme, easily forged sessions, several endpoints unprotected). | No authentication, or passwords are stored in plaintext or in a reversible form. |

**Evidence to verify:** role definitions and policy/ability files, attempts to access restricted actions as a lower-privilege user (UI **and** direct API calls), cookie flags in browser dev tools, `password_digest` in the schema, `git log`/repo scan for committed secrets.

## III. Data Layer
 
| Criterion | Exceeds (4) | Meets (3) | Partially Meets (2) | Minimally Meets (1) | Does Not Meet (0) |
|---|---|---|---|---|---|
| **Persistent Storage & Migrations** | A relational SQL database with a well-designed, normalized schema. All schema changes are versioned through Rails migrations that run cleanly from scratch and are reversible. Constraints (foreign keys, NOT NULL, unique indexes) and indexes on key query paths are present. Seed data supports demonstration. | A relational SQL database with a formal schema. All schema changes are made through Rails migrations that run cleanly from scratch. Relationships and basic constraints are correct. | Database and migrations are present, but the schema has missing constraints or relationships, migrations were edited after the fact, or the schema was changed outside migrations. Migrations may not run cleanly from scratch. | Minimal schema that poorly supports the application's features. Migrations are mostly absent, or the schema was modified manually. | No relational database or no migration system (e.g., flat files or in-memory data only). |
 
**Evidence to check:** `db/migrate/`, `db/schema.rb` (or `structure.sql`), a fresh `rails db:drop db:create db:migrate` run, which database adapter is configured.
 
## IV. REST API & Documentation
 
| Criterion | Exceeds (4) | Meets (3) | Partially Meets (2) | Minimally Meets (1) | Does Not Meet (0) |
|---|---|---|---|---|---|
| **RESTful API Design** | Resource-oriented routing, correct HTTP verbs, and precise status codes (e.g., 200 / 201 / 204 / 400 / 401 / 403 / 404 / 422) used consistently. Consistent JSON response and error formats. Includes additional design maturity such as pagination, filtering, or versioning. The API clearly covers all core features. | Cleanly designed REST API with resource-based routes, appropriate HTTP verbs, appropriate status codes, and consistent JSON responses. It covers the application's core functionality. | API is mostly RESTful but has inconsistencies (e.g., verbs in URLs, returning 200 for errors, inconsistent response shapes) or has gaps in coverage of core features. | Few endpoints, mostly RPC-style routes, or status codes are largely incorrect. | No API is exposed. |
| **OpenAPI / Swagger Documentation** | OpenAPI spec is **automatically generated** (e.g., rswag or equivalent) and served through an interactive UI. It documents all endpoints, parameters, request/response schemas, authentication, and error responses, with examples. Documentation stays in sync with the code (e.g., generated from request specs). | OpenAPI/Swagger documentation is automatically generated and accessible. It covers all endpoints with parameters and response schemas. | Documentation exists but covers only part of the API, is hand-written and stale, or is missing schemas or authentication details. | Documentation is a stub or covers only a handful of endpoints with little useful detail. | No OpenAPI/Swagger documentation. |
 
**Evidence to check:** `rails routes`, calling endpoints with curl/Postman and inspecting status codes and error bodies, the Swagger UI URL, whether the spec file is generated or hand-edited.  URL to API documentation is provided by the team prior to the start of the presentation.

## V. External Integration
 
| Criterion | Exceeds (4) | Meets (3) | Partially Meets (2) | Minimally Meets (1) | Does Not Meet (0) |
|---|---|---|---|---|---|
| **Non-Trivial External API Integration** | At least one external API is integrated in a way that is central to the product's value, involving complex data processing or two-way communication (e.g., Stripe checkout plus webhooks, Twilio send and receive, an LLM API with structured prompt/response handling). Includes robust error handling (timeouts, retries, failure states), secured credentials, and webhook signature verification where applicable. Integration is covered by tests using stubs/mocks (e.g., WebMock/VCR). | At least one external API is integrated meaningfully, with complex data processing or two-way communication. Failures are handled gracefully, credentials are secured, and the integration works in the demo. | Integration exists but is shallow (mostly one-way fetch and display, or a thin pass-through wrapper), is fragile (little or no error handling), or is only partially functional. | Integration is trivial or read-only (e.g., a weather or stock widget), or the "integration" is entirely faked with no real call path. | No external API is used. |
 
**Evidence to check:** the service/client code, how API keys are stored (credentials/ENV), webhook endpoints, behavior when the external API is unavailable or returns an error, live demonstration of the full round trip.
 
## VI. Business Logic: Tiers & Auditing
 
| Criterion | Exceeds (4) | Meets (3) | Partially Meets (2) | Minimally Meets (1) | Does Not Meet (0) |
|---|---|---|---|---|---|
| **Subscription Tiers & Feature Toggling** | At least two tiers with premium features **and** usage limits enforced server-side through a centralized, maintainable mechanism (e.g., entitlements, policy objects, feature flags). Upgrade and downgrade flows work (payments mocked or in test mode) and handle their effect on existing data. Users receive clear feedback when blocked by a tier limit. | At least two service tiers (e.g., Free and Pro). At least one premium feature or usage limit is programmatically restricted based on the active tier. Users can change tiers (payment mocked or in test mode). | Tiers exist, but gating is incomplete, enforced only in the UI, scattered or inconsistent in the code, or upgrade/downgrade does not work reliably. | A tier attribute exists on the user or tenant, but little or no application behavior depends on it. | No subscription tiers. |
| **Usage Tracking or Auditing** | Key user actions or usage metrics are recorded persistently with actor, action, target resource, timestamp, and useful metadata (e.g., IP, before/after values). Records are viewable by an authorized role with filtering or summarization, and the log is protected from tampering. Usage data feeds billing or tier-limit enforcement. | Key user actions or usage metrics are recorded persistently, including at least who, what, and when. Records are accessible to an authorized role (UI, API, or admin console). | Tracking exists but is incomplete (covers few actions, missing actor or timestamp), is not viewable by anyone through the application, or is applied inconsistently. | Minimal tracking (e.g., only the default Rails log, or a single action tracked). | No usage tracking or auditing. |
 
**Evidence to check:** where tier checks occur in the code (model, policy, controller, or only the view), attempts to exceed a free-tier limit via the API directly, the audit/usage table in the schema, a demonstrated action that produces a log entry.

## Score Summary
 
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
| | **Required Total** | **____ / 36** |
 
**Interpreting the total:** a team that meets every minimum requirement scores a 3 in each row (27/36, or 75%). Scores of 4 reflect work beyond the minimum, and any row scored 0-1 identifies a core requirement that was not delivered.
## Comments by evaluator:
