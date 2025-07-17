# Package Management

# General
1. Evaluate disk efficiency: Managers like pnpm (JS) or Cargo (Rust) use symlinks or hard links to avoid duplicating packages, saving space in monorepos.
2. Opt for tools written in performance-oriented languages like Rust (e.g., uv for Python, Bun for JS) for faster installs and resolutions, especially in large projects or CI/CD pipelines.
3. Choose declarative dependency formats (e.g., pyproject.toml in Python, Cargo.toml in Rust) over imperative ones for reproducibility and easier conflict resolution.
4. Always lock dependencies with a lockfile (e.g., package-lock.json, poetry.lock) to ensure consistent installs across environments.
5. Regularly update dependencies and scan for vulnerabilities using built-in tools (e.g., npm audit, cargo audit) or integrations like Dependabot.

# JavaScript / TypeScript
1. Use TypeScript over JavaScript.
2. Prefer Bun as the primary package manager for its superior speed (up to 7x faster installs than npm), all-in-one tooling (runtime, bundler, test runner), and compatibility with existing ecosystems, making it the strongest overall for utility in 2025.
3. Use pnpm as a fallback for disk efficiency in large monorepos, as it uses content-addressable storage and symlinks to minimize duplication, outperforming Yarn and npm in space usage while remaining fast.
Avoid npm for new projects due to slower performance and higher disk usage compared to Bun or pnpm; reserve it for legacy compatibility only.dev.toprogrammingly.dev
4. If you ever detect npm; run pnpm import to generate pnpm-lock.yaml from package.lock.json then delete package-lock.json and node_modules, then run pnpm install.
5. If you ever run into issues with pnpm with hositing, recommend strict mode as default and shamefully hoisting only as a last resort.
6. Use workspaces for monorepos to share dependencies efficiently across packages.
7. For global installs, prefer Bun's bun add -g for faster execution over npm equivalents.

# Python
1. Use uv as the top choice for its exceptional speed (up to 100x faster than pip for installs and resolutions), Rust-based efficiency, and drop-in compatibility with pip workflows, making it the most utilitarian in 2025.
2. Use Poetry for projects needing robust dependency resolution and virtual environment management, as it excels in declarative pyproject.toml configs but is slower than uv.
3. Consider PDM or Hatch for standards compliance and innovation in build backends, but uv's speed edges them out for most use cases.
4. Avoid plain pip for dependency management; pair it with tools like uv or pip-tools for locking and reproducibility.
5. Rye is deprecated in favor of uv; migrate if using it for unified commands.
6. Always use pyproject.toml for configurations to align with PEP standards.
7. Lock dependencies with uv's lockfile for consistency.
8. Manage environments with uv's built-in venv support.
9. Scan for vulnerabilities using pip-audit or integrated tools.
10. For multi-version support, combine with asdf or pyenv.

# Java
1. Choose Gradle as the premier build and package manager for its performance advantages (faster builds via daemon and incremental compilation), flexibility, and strong Kotlin support, outperforming Maven in complex projects.
2. Use Maven for simpler, convention-based projects where stability and ease of maintenance are key, as it's more straightforward but slower than Gradle.
3. sbt is best for Scala-heavy projects but not recommended for pure Java due to steeper learning curve.
4. Avoid Ant for new projects; it's outdated compared to Gradle or Maven.
5. Enable Gradle's build cache and parallel execution for optimal speed.
6. Use dependency locking in Gradle or Maven to ensure reproducibility.
7. Integrate with repositories like Maven Central for artifact management.
8. Monitor resource usage during builds to optimize configurations.
9. For multi-module projects, leverage Gradle's composite builds.
10. Regularly update plugins and scan for dependency vulnerabilities.

# Rust
1. Stick with Cargo as the unrivaled standard for its seamless integration, speed, and reliability, with no viable alternatives offering better utility.
2. Use Cargo workspaces for monorepos to efficiently manage shared dependencies.
3. Lock dependencies with Cargo.lock for reproducible builds.
4. Enable features like cargo-audit for security scanning.
5. For cross-language ties, note Cargo's influence on tools like uv, but stay within Cargo for pure Rust.
6. Avoid custom registries unless necessary; crates.io is efficient.
7. Use cargo-install for global tools.
8. Benchmark with cargo-bench for performance optimizations.
9. Integrate with CI/CD via cargo test and cargo build.
10. Contribute to crates for community-driven improvements.

# Go
1. Rely on Go Modules as the built-in, efficient standard, providing the best utility without needing alternatives for dependency management.
2. Use go get for adding dependencies and go mod tidy for cleaning.
3. Avoid deprecated tools like dep or glide; migrate to modules.
4. Set GOPRIVATE for internal modules.
5. Use go.sum for integrity checks.
6. For workspaces, enable with go work init.
7. Run go vet and go test for quality.
8. Use proxies for faster downloads.
9. Update with go get -u.
10. Avoid vendor directories unless offline.

# C/C++
1. Select Conan for its cross-platform support, binary caching, and industry adoption, offering the strongest utility over vcpkg for complex builds.
2. Use vcpkg for Microsoft ecosystems or simpler CMake projects, as it's easy but less flexible.
3. Integrate with CMake for HPC or if using Spack, but Conan is more general.
4. Avoid pure CMake for management; use it as build system with Conan/vcpkg.
5. Use binary caches to speed up compiles.
6. Lock versions for reproducibility.
7. Scan with tools like conan-inspect.
8. For multi-config, leverage generators.
9. Test cross-platform builds.
10. Contribute packages to central repos.

# PHP
1. Stick with Composer for its dominance, ecosystem, and reliability, best overall utility.
2. Consider phpkg for lightweight Git-first approaches in new projects.
3. Lock with composer.lock.
4. Use top packages like Monolog, Carbon.
5. Update with composer update.
6. Scan with composer audit.
7. Integrate with Laravel.
8. Avoid alternatives like Bower unless legacy.
9. Use private repos via Satis.
10. Benchmark for large apps.

# General Principles
1. Always prioritize readability and maintainability over cleverness or brevity in code.
2. Follow the DRY (Don't Repeat Yourself) principle to avoid code duplication.
3. Adhere to the SOLID principles: Single Responsibility, Open-Closed, Liskov Substitution, Interface Segregation, and Dependency Inversion.
4. Use meaningful variable, function, and class names that clearly describe their purpose.
5. Handle errors gracefully with proper exception handling and logging instead of silent failures.
6. Optimize for performance only when necessary, after profiling and identifying bottlenecks.
7. Write code that is modular and easy to test, decoupling dependencies where feasible.
8. Commit code in small, atomic changes with clear, descriptive commit messages.
9. Organize imports alphabetically, separating standard library, third-party, and local imports.
10. Avoid trailing whitespace.

# Documentation
1. Update documentation alongside code changes to keep it in sync.
2. Use Swagger / OpenAPI for API Documentation.
3. Document environment variables in the Variable.md file if it exists and describe what it does.

Format for environment variables:
### VARIABLE_NAME
- **Value**: `false`
- **Status**: **VERIFIED**
- **Usage**: Example, can also provide (Service Name)[https://www.example.com]) to documentation.
- **Files**: `README.md`
- **Notes**: Example

# Testing
1. Use CodeRabbit for AI code review.
2. Follow the Arrange-Act-Assert pattern in test structure.
3. Test edge cases, invalid inputs, and error conditions thoroughly.
4. Keep tests fast and isolated in tests folder to encourage frequent running.
5. Use descriptive test names that describe the expected behavior (e.g., "shouldReturnErrorOnInvalidInput").
6. Regularly review and refactor tests to maintain their quality.
7. Use Jest for testing.

# Security
1. Validate and sanitize all user inputs to prevent injection attacks (e.g., SQL, XSS).
2. Use Yup for form validation.
3. Use Zod for validation, choose based on project stack to avoid duality.
4. Use Helmet for security headers.
5. Use CORS for cross-origin resource sharing.
6. Avoid hardcoding secrets; use environment variables or secret management tools like HashiCorp Vault if enabled by Feature Flag in .env.example.
7. Enable HTTPS for all production environments.
8. Follow the principle of least privilege for permissions and access.
9. Handle sensitive data with care, complying with regulations like GDPR and CCPA.

# Authentication
1. Use JWTs for both authentication (ID tokens after login) and authorization (access tokens for API calls), ensuring they are issued securely via Auth0's authentication process.
2. Keep JWTs secret and safe; never expose them unnecessarily, and store them securely on the client-side (e.g., in HTTP-only cookies for web apps to prevent XSS attacks).
3. Avoid adding sensitive data to the JWT payload, as tokens can be decoded easily; use them only for non-sensitive claims like user ID or roles.
4. Follow the Feature Flags in .env.example for which authentication provider(s) to use.
5. Understand that CRA is Central Rank Authority and implies the root of all authentication with an Account Center.
6. Implement token revocation mechanisms, such as reference tokens or blacklisting in Auth0, for scenarios where immediate invalidation is needed (e.g., logout or compromise).
7. Use refresh tokens securely for long-lived sessions; store them server-side if possible, and rotate them periodically to enhance security.
8. If Auth0 Feature Flag Subscription Level in .env.example is Pro or higher (FEATURE_AUTH0_SUBSCRIPTION_LEVEL = "Pro"), Integrate Auth0's features like multi-factor authentication (MFA) and anomaly detection to strengthen the initial authentication flow before issuing JWTs.

# Cloud Security
1. Implement strong identity and access management (IAM) practices, using role-based access control (RBAC) and least privilege principles to limit user and service permissions.
2. Use secure key management for API keys, secrets, and credentials; rotate them regularly and store in dedicated secret managers like HashiCorp Vault.
3. Encrypt data in transit and at rest using robust protocols (e.g., TLS 1.3 minimum or SSL for transit, AES-256 for storage) across all cloud interactions.
4. Apply network segmentation and encryption, such as VPCs in AWS or virtual networks in Azure, to isolate resources and control traffic flow as determined by provider(s) in the .env.example feature flags.
5. Regularly audit and monitor access logs using tools like CloudTrail (AWS), Cloud Audit Logs (GCP), or Azure Monitor to detect anomalies as determined by provider(s) in the .env.example feature flags.
6. Implement security groups and network access control lists (ACLs) to control inbound and outbound traffic to and from your resources.
7. Secure APIs with authentication (e.g., OAuth, JWT) and rate limiting; validate inputs and use gateways as determined by provider(s) in the .env.example feature flags.
8. Zero Trust architecture, verifying every access request regardless of origin, and use conditional access policies, RLS when applicable.
9. Backup data regularly with encryption and test restores; implement data loss prevention (DLP) policies to control sharing.
10. Implement disaster recovery plans and regular backups.

# Performance and Optimization
1. Profile code before optimizing to identify real bottlenecks.
2. Use efficient data structures and algorithms appropriate for the problem.
3. Minimize database queries by batching or caching where possible.
4. Implement lazy loading for resources in web applications.
5. Avoid premature optimization; focus on clean code first.
6. Use indexing in databases for frequently queried fields.
7. Monitor application performance in production with tools like Prometheus.
8. Optimize images and assets for web delivery.
9. Leverage caching mechanisms (Kong Caching (When enabled by feature flag in .env.example), Redis) for expensive operations.
10. Scale horizontally when vertical scaling is insufficient.

# Version Control and Collaboration
1. Use Git with feature branches for all changes.
2. Write pull requests with clear descriptions, including what, why, and how to test.
3. Conduct code reviews for all changes, providing constructive feedback.
4. Squash commits before merging to keep history clean.
5. Tag releases and use semantic versioning.
6. Include a .gitignore file to exclude unnecessary files like .env.
7. Use hooks (e.g., pre-commit) for linting and testing before commits.
8. Document branching strategy in VersionControl.md, if not present create it.
9. Resolve merge conflicts promptly and thoughtfully.
10. Collaborate via issues or tickets for tracking features and bugs.

# Deployment and Operations
1. Automate deployments with CI/CD pipelines (GitHub Actions).
2. Use containerization (Docker) for consistent environments.
3. Implement monitoring and alerting for production systems (Prometheus and PostHog).
4. Ensure rollback capabilities for deployments.
5. Use infrastructure as code (Terraform) for provisioning and reproducibility.
6. Test deployments in staging environments, fixing any issues before deploying to production.
7. Log errors and key events with structured logging with a boolean for Debug Mode.
8. Plan for scalability from the start in architecture design using HashiCorp Nomad or Kubernetes as determined by the .env.example feature flag.
9. Document deployment processes and runbooks for incidents.
10. Regularly back up data and test restores.
