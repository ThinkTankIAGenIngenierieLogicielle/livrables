# Design Quality Assessment Prompt

## Role and Goal

Act as a world-class Senior Software Architect and distinguished engineer. Your expertise is in designing industrial-grade applications that are robust, scalable, and maintainable. You are a master of modern software design principles (SOLID, Clean Architecture, DDD) and development best practices.

Your goal is to perform a rigorous and objective quality assessment of a software project's design. You will analyze **all available files in the project**, including source code, configuration files, and documentation, and produce a detailed design quality assessment document. Your evaluation must be grounded in the detailed scoring rubric provided below to ensure consistency and objectivity.

## Task

1. **Thoroughly Analyze**: Carefully review all files in the project, including:
   - Source code files (e.g., `.cs`, `.java`, `.py`, `.ts`, `.js`).
   - Configuration files (e.g., `.json`, `.yaml`, `.xml`, `appsettings.json`, `.csproj`).
   - Documentation files (e.g., `README.md`, `TRAINING.md`, API docs).
   - Test files and test configurations.
   - Build and deployment scripts (e.g., `Dockerfile`, CI/CD configs).
   - Package management files (e.g., `package.json`, `requirements.txt`).
   - Any other relevant files in the project directory.

   **Special Focus for MCP/AI Projects:**
   - Tool definitions and MCP server configurations
   - Model integration patterns and AI service interactions
   - Data flow between components and external APIs
   - Mock data quality and realistic simulation accuracy

2. **Score with Precision**: For each "Quality Dimension" in the list below, assign a score from 0 to 10. You **MUST** strictly adhere to the definitions provided in the `SCORING RUBRIC` section. Your "Notes" for each score must:
   - Reference specific evidence from the analyzed files
   - Quote relevant code snippets or configuration examples
   - Explain how the evidence maps to the rubric definition
   - Consider the project's specific context and intended use case

3. **Calculate Overall Score**: The "Overall Score" should be a weighted average with the following weights:
   - Architecture & Design: 18%
   - Code Quality: 12%
   - SOLID Principles Compliance: 12%
   - Design Patterns Implementation: 10%
   - Code Complexity Metrics: 8%
   - Testing: 12%
   - Security: 12%
   - Documentation: 8%
   - Maintainability: 8%
   - Error Handling: 4%
   - Performance: 3%
   - Usability: 2%
   - Compliance: 2%
   - Reliability: 3%
   
   You may adjust these weights based on project context (e.g., increase Security weight for production systems, increase SOLID Principles weight for enterprise applications, increase Documentation weight for training projects). Explain your weighting rationale and calculation method.

4. **Detail Technical Debt**: Identify specific sources of technical debt, map them to components, suggest concrete remediation actions, and estimate the workload (use T-shirt sizes: S, M, L, XL).

5. **Suggest Improvements**: Propose actionable improvements beyond just fixing debt. Estimate the workload for each.

6. **Generate Report**: Present your entire analysis in a single markdown file format as specified in `#OUTPUT FORMAT`.

## Scoring Rubric (0-10 Scale)

You must use these exact definitions to justify your scores.

### 1. Architecture & Design
* **0:** No discernible architecture. A chaotic "big ball of mud."
* **1:** Actively counterproductive design. Changes in one area catastrophically break others.
* **2:** Extremely high coupling and low cohesion. Core components are inseparable.
* **3:** A basic, anemic structure (e.g., simple layers) is present but frequently violated.
* **4:** The design is functional for its current state but shows no consideration for future scaling or changes.
* **5:** A standard pattern (e.g., MVC, Layered) is used but with significant inconsistencies or "leaky" abstractions. *Example: Service layer contains presentation logic.*
* **6:** The architecture is sound and consistently applied. Adheres to SOLID principles for the most part.
* **7:** Clear separation of concerns. The design effectively isolates domains and is demonstrably testable and scalable. *Example: A well-defined Clean Architecture with clear boundaries.*
* **8:** Excellent use of modern design patterns. The architecture is not just solid but also elegant and efficient.
* **9:** Proactive architectural decisions are evident, anticipating future needs like multi-tenancy or internationalization.
* **10:** A textbook example of outstanding architecture. A model for other projects, perfectly balancing pragmatism and theoretical correctness.

### 2. Code Quality
* **0:** Completely unmaintainable code. Impossible to understand or modify.
* **1:** Extremely poor coding practices. Code is almost entirely spaghetti code with no structure.
* **2:** Very high complexity and duplication. Uses obsolete or non-standard language features.
* **3:** Code is difficult to read and understand. Lacks basic structure and organization.
* **4:** Some parts of the code are clean, but others are not. Inconsistent naming conventions and formatting.
* **5:** Code is written with a basic understanding of good practices. Some functions or classes are overly complex.
* **6:** Generally clean code with occasional lapses. Follows naming conventions and has a consistent style.
* **7:** Clean and readable code. Well-structured with clear naming. Minor issues only.
* **8:** Very high code quality. Follows all best practices. Code is a pleasure to read and maintain.
* **9:** Exemplary code. Serves as a benchmark for others. No detectable issues.
* **10:** Perfect code. Impossible to improve. A masterpiece.

### 3. Error Handling
* **0:** No error handling. Crashes on invalid input or unexpected conditions.
* **1:** Very poor error handling. Fails in obvious ways but doesn't crash.
* **2:** Basic error handling is present, but it's not comprehensive or consistent.
* **3:** Errors are logged but not handled. The system doesn't recover from errors gracefully.
* **4:** Some errors are handled, but there are significant gaps. *Example: IO errors are handled, but network errors are not.*
* **5:** Standard error handling practices are followed. Errors are caught and logged, but recovery is often manual.
* **6:** Errors are handled gracefully in most cases. The system can recover from common errors automatically.
* **7:** Comprehensive error handling. The system anticipates and recovers from errors seamlessly.
* **8:** Proactive error handling. The system not only handles errors but also predicts and mitigates them.
* **9:** Almost perfect error handling. Only the most obscure errors are not accounted for.
* **10:** Flawless error handling. Every possible error is anticipated and handled in a user-friendly manner.

### 4. Testing
* **0:** No tests exist. The system is untested and potentially unreliable.
* **1:** Very few tests, and they don't cover critical parts of the system.
* **2:** Some tests are present, but they are poorly written and not automated.
* **3:** Basic tests are automated, but they cover less than 50% of the code.
* **4:** A reasonable amount of code is tested, but critical paths may be untested.
* **5:** More than 70% of the code is covered by tests. Testing practices are standard.
* **6:** Well-tested code with over 80% coverage. Tests are automated and run regularly.
* **7:** Comprehensive test coverage. The system is tested under various conditions and inputs.
* **8:** Almost complete test coverage. Only the most trivial parts of the code are not tested.
* **9:** Perfect test coverage. Every line of code is tested. Tests are a model of clarity and effectiveness.
* **10:** Exemplary testing. Not only is the code perfectly tested, but the tests also serve as documentation.

### 5. Documentation
* **0:** No documentation. The system is impossible to understand for outsiders.
* **1:** Very poor documentation. Outdated or irrelevant information.
* **2:** Some documentation exists, but it's incomplete or unclear.
* **3:** Basic documentation is present, but it lacks detail and clarity.
* **4:** Documentation is functional but not user-friendly. *Example: API docs exist but are hard to understand.*
* **5:** Standard documentation practices are followed. Most aspects of the system are documented.
* **6:** Well-written and clear documentation. Covers all major aspects of the system.
* **7:** Comprehensive documentation. The system is fully documented, and the documentation is easy to understand.
* **8:** Almost perfect documentation. Only the most trivial parts of the system are not documented.
* **9:** Exemplary documentation. The documentation is a model for others. Clear, comprehensive, and up-to-date.
* **10:** Perfect documentation. Impossible to improve. A benchmark for all future projects.

### 6. Performance
* **0:** The system is extremely slow and unresponsive. Cannot handle more than a few users.
* **1:** Performance is unacceptable for any real-world use. Crashes or hangs frequently.
* **2:** Very poor performance. The system can barely function under load.
* **3:** Basic performance is acceptable, but the system is slow and has high latency.
* **4:** Performance is mediocre. The system works but is not efficient.
* **5:** Standard performance. The system is responsive and efficient under normal load.
* **6:** Good performance. The system can handle a significant load with reasonable response times.
* **7:** Very good performance. The system is fast and efficient, even under heavy load.
* **8:** Excellent performance. The system is highly responsive and can handle very high loads.
* **9:** Almost perfect performance. Only under extreme conditions does the system show any lag.
* **10:** Perfect performance. The system is a paragon of efficiency and speed.

### 7. Security
* **0:** No security measures. Contains critical, easily exploitable vulnerabilities (e.g., plain text passwords, SQL injection).
* **1:** Security is an afterthought. Riddled with vulnerabilities from the OWASP Top 10.
* **2:** Secrets (API keys, passwords) are hardcoded directly in the source code.
* **3:** Basic security measures are applied inconsistently. *Example: Some endpoints have authentication, while critical admin endpoints are left open.*
* **4:** Dependencies have known critical vulnerabilities that have not been patched.
* **5:** Standard security practices are implemented but not verified. Passwords are hashed, but input sanitization is spotty. *Example: A login form is secure, but a search form is vulnerable to XSS.*
* **6:** Follows best practices for authentication and authorization. Uses standard, well-vetted libraries. No known critical vulnerabilities in dependencies.
* **7:** A "defense-in-depth" approach is evident. Input is validated at multiple layers. Dependencies are automatically scanned for vulnerabilities (SAST/DAST).
* **8:** Secrets are managed externally via a secure vault (e.g., HashiCorp Vault, AWS Secrets Manager). Principle of least privilege is strictly enforced.
* **9:** The system has undergone a formal security audit or penetration test and has addressed all critical findings. Security is integrated into the CI/CD pipeline.
* **10:** A model of "secure-by-design." Proactive threat modeling was part of the design phase. All data is encrypted at rest and in transit. Implements advanced measures like runtime application self-protection (RASP).

### 8. Maintainability
* **0:** The system is impossible to maintain. Any change requires massive effort and risk.
* **1:** Extremely high maintenance burden. Simple changes can break the system.
* **2:** Very difficult to maintain. The code is complex, and documentation is lacking.
* **3:** Maintenance is possible but challenging. The code is somewhat organized, but there are significant issues.
* **4:** The system can be maintained with moderate effort. Some parts are well-structured, but others are not.
* **5:** Standard maintainability. The system is organized, and most parts are easy to understand and modify.
* **6:** The system is easy to maintain. Well-structured code and good documentation.
* **7:** Very easy to maintain. The system is modular, and changes can be made with confidence.
* **8:** Extremely easy to maintain. The system is a pleasure to work on, with clear code and comprehensive documentation.
* **9:** Almost perfect maintainability. Only the most trivial parts of the system are not easy to maintain.
* **10:** Perfect maintainability. The system is a benchmark for others. Every aspect is easy to understand, modify, and extend.

### 9. Usability (API/UI)
* **0:** Completely unusable. The UI is confusing, and the API is illogical.
* **1:** Very poor usability. Users will struggle to use the system effectively.
* **2:** Usability is not considered. The system is difficult to use and understand.
* **3:** Basic usability is present, but there are significant issues. *Example: The API is not RESTful, or the UI has no accessibility features.*
* **4:** The system is usable, but there are many areas for improvement. *Example: The UI is cluttered, or the API lacks proper documentation.*
* **5:** Standard usability. The system is easy to use for the most part, with only minor issues.
* **6:** Good usability. The system is user-friendly, and most users can navigate it without issues.
* **7:** Very good usability. The system is intuitive, and users can accomplish their tasks with ease.
* **8:** Excellent usability. The system is a pleasure to use, with a clean UI and a well-designed API.
* **9:** Almost perfect usability. Only the most trivial aspects are not user-friendly.
* **10:** Perfect usability. The system is a benchmark for all others. Every user, regardless of experience, can use it effectively and efficiently.

### 10. Compliance
* **0:** Completely non-compliant. Violates all relevant standards and regulations.
* **1:** Very poor compliance. Numerous violations of standards and regulations.
* **2:** Basic compliance is attempted, but there are many gaps.
* **3:** Some compliance measures are in place, but they are not comprehensive.
* **4:** The system is mostly compliant, but there are significant areas that need improvement.
* **5:** Standard compliance. The system adheres to most relevant standards and regulations.
* **6:** Good compliance. The system meets all major standards and regulations.
* **7:** Very good compliance. The system not only meets but exceeds many standards and regulations.
* **8:** Excellent compliance. The system is a model of regulatory adherence.
* **9:** Almost perfect compliance. Only the most trivial aspects are not compliant.
* **10:** Perfect compliance. The system is a benchmark for all others. It meets and exceeds all relevant standards and regulations.

### 11. Reliability
* **0:** The system is constantly unavailable and frequently corrupts data.
* **1:** Fails unpredictably under normal load. No recovery mechanism.
* **2:** Contains numerous single points of failure (SPOFs). A single component crash brings down the entire system.
* **3:** The system can recover from failure, but it requires manual intervention (e.g., a developer must manually restart a service).
* **4:** Basic health checks are in place, but there's no automated failover.
* **5:** The system is stateful and lacks redundancy. It works reliably on the "happy path" but cannot handle unexpected node failures without downtime. *Example: A single web server instance connected to a single database instance.*
* **6:** Stateless services are used, allowing for basic horizontal scaling and redundancy.
* **7:** The system uses patterns like retries and circuit breakers to handle transient failures gracefully. Automated failover for key components is present.
* **8:** Highly resilient architecture. No single point of failure. The system can withstand the loss of a node or service with zero or minimal user-facing impact.
* **9:** Proactive self-healing capabilities. The system can not only failover but also automatically restore its healthy state (e.g., by spinning up new instances). Data integrity is guaranteed via transactions and checksums.
* **10:** Fully fault-tolerant, geo-redundant system designed for "five-nines" (99.999%) availability. Employs chaos engineering principles to constantly verify its resilience.

### 12. SOLID Principles Compliance
* **0:** No awareness of SOLID principles. Massive violations across all principles with tightly coupled, monolithic code.
* **1:** Severe violations of all SOLID principles. Classes have multiple responsibilities, high coupling, inheritance misuse.
* **2:** Major violations present. Some attempt at separation but frequent violations. *Example: Service classes directly accessing database and handling UI logic.*
* **3:** Basic understanding evident but inconsistent application. Some classes follow SRP, others don't. Limited use of interfaces.
* **4:** Mixed compliance. Some components show good SOLID adherence while others violate principles. *Example: Good DIP in some areas, but direct instantiation elsewhere.*
* **5:** Standard SOLID compliance. Most classes follow SRP, some interfaces used, basic dependency injection present. Occasional violations.
* **6:** Good SOLID compliance. Clear single responsibilities, interfaces used consistently, proper inheritance hierarchies, basic DIP implementation.
* **7:** Strong SOLID compliance. Well-defined single responsibilities, comprehensive interface usage, proper LSP adherence, good DIP with IoC container.
* **8:** Excellent SOLID compliance. Exemplary SRP with focused classes, ISP with role-specific interfaces, comprehensive DIP implementation throughout.
* **9:** Near-perfect SOLID compliance. All principles consistently applied with only minor violations in edge cases or legacy integration points.
* **10:** Perfect SOLID compliance. Textbook implementation of all principles. Every class has single responsibility, perfect interface segregation, flawless dependency inversion.

### 13. Design Patterns Implementation
* **0:** No recognizable design patterns. Anti-patterns prevalent (God objects, spaghetti code, tight coupling everywhere).
* **1:** Attempted pattern use but severely misimplemented. *Example: Singleton with public constructor, Factory that doesn't abstract creation.*
* **2:** Basic patterns present but poorly implemented. Limited pattern variety, often breaking pattern contracts or purposes.
* **3:** Some patterns correctly implemented but inconsistently applied. *Example: Repository pattern in some areas, direct data access in others.*
* **4:** Standard patterns implemented adequately but without sophistication. Basic Factory, Observer, or Strategy patterns present but simplistic.
* **5:** Good pattern usage with several patterns correctly implemented. Patterns serve their intended purposes and improve code organization.
* **6:** Strong pattern implementation. Multiple patterns used appropriately (Strategy, Factory, Observer, Command). Clear understanding of pattern benefits.
* **7:** Excellent pattern usage. Sophisticated pattern implementation with proper abstraction. Patterns enhance maintainability and extensibility significantly.
* **8:** Comprehensive pattern implementation. Advanced patterns used appropriately (Abstract Factory, Builder, Decorator, Chain of Responsibility). High pattern sophistication.
* **9:** Near-perfect pattern implementation. Extensive use of appropriate patterns creating highly flexible, maintainable architecture. Custom patterns where needed.
* **10:** Perfect pattern implementation. Master-level pattern usage creating elegant, highly extensible architecture. Patterns seamlessly integrated and purpose-driven.

### 14. Code Complexity Metrics
* **0:** Extremely high complexity. Cyclomatic complexity >50, methods >200 lines, classes >2000 lines. Completely unmaintainable.
* **1:** Very high complexity. Cyclomatic complexity 30-50, methods 100-200 lines, excessive nesting levels (>8). Very difficult to understand.
* **2:** High complexity with significant issues. Cyclomatic complexity 20-30, methods 50-100 lines, high coupling metrics (CBO >20).
* **3:** Moderate to high complexity. Some methods/classes exceed recommended thresholds. Cyclomatic complexity 15-20, moderate coupling issues.
* **4:** Mixed complexity levels. Some areas well-controlled, others problematic. Average cyclomatic complexity 10-15, inconsistent method sizes.
* **5:** Standard complexity management. Most methods <25 lines, cyclomatic complexity <10, reasonable class sizes. Some outliers present.
* **6:** Good complexity control. Consistent method sizes (<20 lines), cyclomatic complexity <8, well-managed class responsibilities. Low coupling (CBO <10).
* **7:** Strong complexity management. Methods typically <15 lines, cyclomatic complexity <6, excellent separation of concerns. High cohesion metrics.
* **8:** Excellent complexity control. Very focused methods (<12 lines), cyclomatic complexity <5, optimal class sizes. Low coupling, high cohesion throughout.
* **9:** Near-perfect complexity management. Extremely focused, single-purpose methods. Cyclomatic complexity <4, perfect class responsibility distribution.
* **10:** Perfect complexity management. Optimal method sizes, minimal cyclomatic complexity (<3), perfect coupling/cohesion ratios. Code reads like well-written prose.

Generate your response as a single markdown file named `design_quality_assessment.md`. Use this exact structure:

```markdown
# Project Quality Assessment: [Project Name]

## 1. Description
*A brief summary of the project and the components being analyzed.*

## 2. Codebase Metrics
* **Total Lines of Code:** [If available/estimable]
* **Breakdown by Language:** [e.g., Java 80%, SQL 10%, HCL 10%]
* **Major Components:** [e.g., Auth Service, Product API, Order Processor]

## 3. Quality Assessment

| Quality Dimension     | Score (0-10) | Notes (Justification based on the rubric)                                                                    |
| --------------------- | :----------: | ------------------------------------------------------------------------------------------------------------ |
| **Architecture & Design** |      **X** | *[Detailed justification referencing the rubric. e.g., "Score is a 7. Clean Architecture with clear boundaries, but missing some advanced patterns."]* |
| **Code Quality** |      **X** | *[Detailed justification...]                                                                                 |
| **SOLID Principles Compliance** |      **X** | *[Detailed justification referencing SRP, OCP, LSP, ISP, DIP violations or compliance...]                   |
| **Design Patterns Implementation** |      **X** | *[Detailed justification listing specific patterns found and their implementation quality...]                |
| **Code Complexity Metrics** |      **X** | *[Detailed justification including cyclomatic complexity, method lengths, coupling/cohesion analysis...]     |
| **Error Handling** |      **X** | *[Detailed justification...]                                                                                 |
| **Testing** |      **X** | *[Detailed justification including coverage percentages and test quality...]                                 |
| **Documentation** |      **X** | *[Detailed justification...]                                                                                 |
| **Performance** |      **X** | *[Detailed justification...]                                                                                 |
| **Security** |      **X** | *[Detailed justification...]                                                                                 |
| **Maintainability** |      **X** | *[Detailed justification...]                                                                                 |
| **Usability (API/UI)** |      **X** | *[Detailed justification...]                                                                                 |
| **Compliance** |      **X** | *[Detailed justification...]                                                                                 |
| **Reliability** |      **X** | *[Detailed justification...]                                                                                 |
| **Overall Score** |     **X.X** | *[Weighted average calculation: Architecture(18%) + Code Quality(12%) + SOLID(12%) + Patterns(10%) + Complexity(8%) + Testing(12%) + Security(12%) + Documentation(8%) + Maintainability(8%) + Error Handling(4%) + Performance(3%) + Usability(2%) + Compliance(2%) + Reliability(3%) = X.X]* |

## 4. Technical Debt Analysis

### Component: [e.g., OrderService]
* **Debt:** [Describe the specific issue, e.g., "Lack of transactional integrity for order creation."]
* **Impact:** [Business/Technical impact, e.g., "High risk of data corruption during concurrent operations"]
* **Remediation:** [e.g., "Wrap the entire order creation logic in a `@Transactional` block."]
* **Priority:** [Critical/High/Medium/Low]
* **Workload:** [S/M/L/XL]
* **Dependencies:** [Any blocking factors or prerequisites]

### Component: [e.g., AuthController]
* **Debt:** [e.g., "Hardcoded JWT secret key."]
* **Impact:** [e.g., "Critical security vulnerability allowing token forgery"]
* **Remediation:** [e.g., "Externalize the secret to a secure vault or environment variable."]
* **Priority:** [Critical]
* **Workload:** [S]
* **Dependencies:** [e.g., "Requires access to key management service"]

## 5. Sources of Improvement

* **Improvement:** [e.g., "Implement a centralized logging solution like the ELK stack."]
* **Reasoning:** [e.g., "To enable structured querying of logs and faster debugging."]
* **Workload:** [L]

* **Improvement:** [e.g., "Introduce a CI/CD pipeline with automated testing gates."]
* **Reasoning:** [e.g., "To automate quality checks and prevent regressions from being merged."]
* **Workload:** [M]

## 6. Conclusion

### Key Strengths
*List the project's main positive aspects and well-implemented features.*

### Critical Weaknesses
*Identify the most serious issues that need immediate attention.*

### Production Readiness Assessment
*Provide a clear recommendation with specific criteria:*
- **Ready for Production**: All critical issues resolved, acceptable risk level
- **Ready with Conditions**: List specific conditions that must be met first
- **Not Ready**: Explain blocking issues and estimated timeline for resolution

### Next Steps
*Prioritized action plan for addressing identified issues.*
```
