# Awesome Terraform Compliance [![Awesome](https://awesome.re/badge.svg)](https://github.com/sindresorhus/awesome)

Tools, frameworks, and resources for implementing compliance, security, and governance controls in Terraform and OpenTofu infrastructure.

Maintained by [Anton Babenko](https://github.com/antonbabenko), creator of [terraform-aws-modules](https://github.com/terraform-aws-modules) and [a few other Terraform projects](https://github.com/antonbabenko/terraform-aws-devops).

## Contents

- [Legend](#legend)
- [Policy Engines](#policy-engines)
- [IaC Security Scanners](#iac-security-scanners)
  - [Multi-Framework Scanners](#multi-framework-scanners)
  - [Terraform-Specific Scanners](#terraform-specific-scanners)
  - [Terraform Testing](#terraform-testing)
  - [Intentionally Vulnerable Terraform](#intentionally-vulnerable-terraform)
- [Compliance-Ready Modules](#compliance-ready-modules)
  - [AWS](#aws)
  - [Azure](#azure)
  - [GCP](#gcp)
- [Cloud Provider Compliance Tools](#cloud-provider-compliance-tools)
  - [AWS](#aws-1)
  - [Azure](#azure-1)
  - [GCP](#gcp-1)
  - [Multi-Cloud](#multi-cloud)
- [Compliance Frameworks and Standards](#compliance-frameworks-and-standards)
  - [CIS Benchmarks](#cis-benchmarks)
  - [SOC 2](#soc-2)
  - [PCI DSS](#pci-dss)
  - [NIST and FedRAMP](#nist-and-fedramp)
- [Evidence and Audit](#evidence-and-audit)
  - [OSCAL Tooling](#oscal-tooling)
  - [Evidence Generation](#evidence-generation)
  - [Drift Detection](#drift-detection)
- [Policy Libraries and Rulesets](#policy-libraries-and-rulesets)
  - [OPA/Rego Libraries](#oparego-libraries)
  - [Sentinel Libraries](#sentinel-libraries)
  - [Guard Rule Libraries](#guard-rule-libraries)
- [Terraform Automation Platforms](#terraform-automation-platforms)
- [CI/CD and Platform Integration](#cicd-and-platform-integration)
- [Learning Resources](#learning-resources)
  - [Articles](#articles)
  - [Conference Talks](#conference-talks)
  - [Books](#books)
  - [Courses](#courses)
  - [Newsletters](#newsletters)
- [Related Awesome Lists](#related-awesome-lists)
- [Curation Policy](#curation-policy)

## Legend

- 💲 - Commercial/paid product or service
- 🆓 - Free tier available (for commercial products)
- 🏛️ - Government/public sector focused
- ⚠️ - Archived, deprecated, or entering maintenance mode (no new features/customers)

## Policy Engines

*General-purpose policy engines used to evaluate Terraform plans and configurations against compliance rules.*

- [Open Policy Agent (OPA)](https://www.openpolicyagent.org/) - General-purpose policy engine using Rego language, CNCF graduated project with extensive Terraform integration via Conftest and terraform-plan evaluation.
- [HashiCorp Sentinel](https://www.hashicorp.com/sentinel) - Policy-as-code framework embedded in Terraform Cloud/Enterprise for enforcing compliance rules on runs. 💲
- [Cloud Custodian](https://cloudcustodian.io/) - Rules engine for cloud resource management with Terraform plan evaluation and runtime policy enforcement. CNCF incubating project.

## IaC Security Scanners

*Tools that analyze Terraform code, plans, or state for security misconfigurations and compliance violations.*

### Multi-Framework Scanners

*Scanners that support multiple IaC frameworks including Terraform.*

- [Checkov](https://www.checkov.io/) - Static analysis tool with 1,000+ built-in policies covering CIS, SOC 2, HIPAA, PCI DSS, and NIST benchmarks for Terraform, CloudFormation, Kubernetes, and more.
- [Trivy](https://trivy.dev/) - Security scanner for IaC misconfigurations, vulnerabilities, secrets, and licenses with Terraform HCL and plan support (absorbed tfsec).
- [KICS](https://kics.io/) - Open-source scanner by Checkmarx with 1,900+ queries across Terraform, Ansible, Docker, and Kubernetes.
- [Terrascan](https://www.tenable.com/cloud-security/solutions/iac) - Static code analyzer supporting 500+ OPA/Rego policies across Terraform, Kubernetes, Helm, and CloudFormation. ⚠️
- [Snyk IaC](https://snyk.io/product/infrastructure-as-code-security/) - IaC security testing integrated with the Snyk developer security platform. 💲 🆓
- [SonarQube IaC Analysis](https://github.com/SonarSource/sonar-iac) - SonarSource's IaC static analyzer covering Terraform, CloudFormation, Kubernetes, and Docker with security and quality rules.
- [Drogon](https://github.com/filipi86/drogonsec) - High-performance open-source scanner combining SAST, SCA, secret detection, and IaC analysis for Terraform and other formats, built for CI/CD pipelines.

### Terraform-Specific Scanners

*Scanners focused specifically on Terraform or OpenTofu.*

- [terraform-compliance](https://terraform-compliance.com/) - BDD-style testing framework for Terraform using Cucumber syntax to write compliance tests in natural language.
- [tflint](https://github.com/terraform-linters/tflint) - Pluggable Terraform linter with AWS, Azure, and GCP rulesets for detecting errors and enforcing best practices.
- [CloudFormation Guard (cfn-guard)](https://github.com/aws-cloudformation/cloudformation-guard) - Policy-as-code DSL from AWS for writing rules that validate JSON and YAML data, including Terraform plan JSON and HCL configurations.
- [Tirith](https://github.com/StackGuardian/tirith) - Policy framework for Terraform stacks that evaluates infrastructure configurations against compliance policies defined in JSON.
- [pike](https://github.com/jamesWoolfenden/pike) - Scans Terraform and OpenTofu code to calculate the minimum IAM permissions required for deployment across AWS, GCP, and Azure.

### Terraform Testing

*Tools for writing automated tests that verify Terraform modules meet compliance and correctness requirements.*

- [Terratest](https://terratest.gruntwork.io/) - Go library for writing integration tests for Terraform modules, deploying real infrastructure and running assertions against it.
- [Terraform test](https://developer.hashicorp.com/terraform/language/tests) - Built-in Terraform 1.6+ testing command for writing unit and integration tests in `.tftest.hcl` files without external dependencies.

### Intentionally Vulnerable Terraform

*Repositories with deliberately misconfigured Terraform for testing and benchmarking security scanners.*

- [TerraGoat](https://github.com/bridgecrewio/terragoat) - Bridgecrew's "vulnerable by design" Terraform repository covering common misconfigurations across AWS, Azure, and GCP.
- [sadcloud](https://github.com/nccgroup/sadcloud) - NCC Group's tool for spinning up intentionally misconfigured AWS infrastructure via Terraform to test detection coverage.

## Compliance-Ready Modules

*Pre-configured Terraform modules designed with compliance controls built in.*

### AWS

- [Compliance.tf](https://compliance.tf/) - Compliance-ready Terraform modules wrapping terraform-aws-modules with enforced compliance controls and audit evidence generation for SOC 2, HIPAA, PCI DSS, NIS2, DORA, and ISO 27001. 💲 🆓
- [opsZero](https://opszero.com/solutions/compliance/) - Compliance automation platform providing Terraform modules for AWS infrastructure meeting HIPAA, PCI DSS, FedRAMP, StateRamp, and CMMC requirements. 💲
- [terraform-aws-secure-baseline](https://github.com/nozaq/terraform-aws-secure-baseline) - Terraform module to configure an AWS account with the secure baseline recommended by CIS Amazon Web Services Foundations Benchmark and AWS Foundational Security Best Practices.

### Azure

- [Azure CAF Terraform](https://github.com/aztfmod/terraform-azurerm-caf) - Cloud Adoption Framework landing zone modules with built-in governance and compliance patterns.

### GCP

- [Google Cloud Foundation Toolkit](https://docs.cloud.google.com/docs/terraform/blueprints/terraform-blueprints) - Google-maintained Terraform blueprints for secure GCP deployments with organizational policy compliance.
- [Secure Cloud Foundation](https://github.com/GoogleCloudPlatform/pbmm-on-gcp-onboarding) - Protected B/Medium/Medium GCP landing zone with Canadian government compliance patterns. 🏛️
- [GCP Hardening Toolkit (GHT)](https://github.com/GoogleCloudPlatform/gcp-hardening-toolkit) - Google-maintained Terraform modules and blueprints for incrementally hardening brownfield GCP environments, with custom IAM role generation and organization policy constraints.

## Cloud Provider Compliance Tools

*Cloud-native services that complement Terraform-managed infrastructure compliance.*

### AWS

- [AWS Config Rules](https://docs.aws.amazon.com/config/latest/developerguide/managed-rules-by-aws-config.html) - Managed and custom rules evaluating AWS resource configurations against compliance baselines, deployable via Terraform.
- [AWS Security Hub](https://aws.amazon.com/security-hub/) - Aggregated security and compliance findings across AWS accounts with CIS, PCI DSS, and NIST benchmarks.
- [AWS Audit Manager](https://aws.amazon.com/audit-manager/) - Automated evidence collection mapped to compliance frameworks including SOC 2, PCI DSS, HIPAA, and GDPR. ⚠️
- [AWS Control Tower](https://aws.amazon.com/controltower/) - Managed landing zone service with SCPs and Config rules as guardrails for multi-account AWS environments, configurable via Terraform.
- [AWS Service Control Policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html) - Preventive governance policies at the AWS Organizations level, deployable via Terraform to enforce compliance boundaries across all accounts.
- [AWS Control Tower Controls with Terraform](https://github.com/aws-samples/aws-control-tower-controls-terraform) - Official AWS sample showing how to implement and administer preventive, detective, and proactive Control Tower guardrails via Terraform IaC.
- [deny.cloud](https://deny.cloud/) - Web-based builder for AWS Service Control Policies and Resource Control Policies with 150 pre-built templates mapped to CIS, PCI DSS, SOC 2, and HIPAA, exporting ready-to-apply Terraform HCL.
- [terraform-iam-policy-validator](https://github.com/awslabs/terraform-iam-policy-validator) - AWS CLI tool that validates IAM policies in Terraform plan JSON against best practices using IAM Access Analyzer checks.

### Azure

- [Azure Policy](https://learn.microsoft.com/en-us/azure/governance/policy/) - Policy enforcement service for Azure resources with built-in compliance definitions deployable via Terraform.
- [Microsoft Defender for Cloud](https://www.microsoft.com/en-us/security/business/cloud-security/microsoft-defender-cloud/) - Cloud security posture management configurable via Terraform (`azurerm_security_center_*` resources) with regulatory compliance dashboards for CIS, PCI DSS, ISO 27001, and SOC 2. 💲

### GCP

- [GCP Organization Policy](https://docs.cloud.google.com/organization-policy/overview) - Centralized policy constraints for GCP organizations manageable via Terraform.
- [Security Command Center](https://cloud.google.com/security/products/security-command-center) - GCP security findings and compliance monitoring platform, with notification configs and source management via `google_scc_*` Terraform resources. 💲

### Multi-Cloud

- [Prowler](https://github.com/prowler-cloud/prowler) - Open-source security assessment tool for AWS, Azure, GCP, and Kubernetes covering CIS, PCI, HIPAA, SOC 2, ISO 27001, and more.
- [Steampipe](https://steampipe.io/) - SQL query engine for live cloud resource data across AWS, Azure, and GCP via plugins. Used as the data layer for Powerpipe compliance benchmarks.
- [Powerpipe](https://powerpipe.io/) - Benchmark and dashboard runner for compliance controls, using Steampipe as its data source. Runs CIS, SOC 2, HIPAA, PCI, NIST, and FedRAMP benchmarks across AWS, Azure, and GCP.
- [CloudQuery](https://www.cloudquery.io/) - Open-source cloud asset inventory tool that syncs AWS, Azure, and GCP resources into SQL or Parquet for compliance queries and reporting.

## Compliance Frameworks and Standards

*Resources mapping compliance framework requirements to Terraform infrastructure controls.*

- [AWS Audit Manager Framework Library](https://docs.aws.amazon.com/audit-manager/latest/userguide/framework-overviews.html) - Overview of all compliance frameworks supported by AWS Audit Manager, covering SOC 2, PCI DSS, HIPAA, ISO 27001, NIST 800-53, FedRAMP, GDPR, and more with AWS-native evidence collection. ⚠️

### CIS Benchmarks

- [CIS AWS Foundations Benchmark](https://www.cisecurity.org/benchmark/amazon_web_services) - Center for Internet Security benchmark for AWS with Terraform-implementable controls.
- [CIS Azure Foundations Benchmark](https://www.cisecurity.org/benchmark/azure) - CIS benchmark for Azure covering identity, networking, logging, and monitoring controls.
- [CIS GCP Foundations Benchmark](https://www.cisecurity.org/benchmark/google_cloud_computing_platform) - CIS benchmark for Google Cloud Platform deployments.

### SOC 2

- [SOC 2 Compliance Mapping for Terraform](https://compliance.tf/docs/frameworks/aws/soc_2/) - Mapping of SOC 2 Trust Services Criteria to Terraform resource configurations and controls. 💲

### PCI DSS

- [PCI DSS v4.0 on AWS](https://docs.aws.amazon.com/securityhub/latest/userguide/pci-standard.html) - AWS Security Hub PCI DSS v4.0 controls with Terraform-provisionable remediation.

### NIST and FedRAMP

- [NIST SP 800-53 Controls](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final) - Security and privacy control catalog (1,000+ controls) used as the baseline for FedRAMP, FISMA, and CMMC. Controls map to cloud resource configurations but the document itself is framework-only, not Terraform-specific. 🏛️
- [OSCAL (Open Security Controls Assessment Language)](https://pages.nist.gov/OSCAL/) - Machine-readable compliance format by NIST for expressing security control implementations. 🏛️
- [FedRAMP Authorization Boundary Guidance](https://demo.fedramp.gov/resources/documents/CSP_A_FedRAMP_Authorization_Boundary_Guidance.pdf) - FedRAMP guidance on defining cloud system boundaries, directly relevant to scoping Terraform-managed infrastructure for federal authorization. 🏛️

## Evidence and Audit

*Tools for generating, managing, and formatting compliance evidence from Terraform-managed infrastructure.*

### OSCAL Tooling

- [Compliance Trestle](https://github.com/oscal-compass/compliance-trestle) - SDK and CLI for creating and validating OSCAL documents, part of the OSCAL Compass project.
- [Lula](https://github.com/defenseunicorns/lula) - Tool for mapping OSCAL component definitions to live infrastructure for continuous compliance validation. 🏛️
- [GovReady-Q](https://github.com/GovReady/govready-q) - Compliance-as-code platform for generating System Security Plans with OSCAL output. 🏛️

### Evidence Generation

- [Drata](https://drata.com/) - Compliance automation platform with infrastructure evidence collection including Terraform state integration. 💲
- [RegScale](https://regscale.com/) - Continuous compliance automation platform with OSCAL-native evidence management. 💲
- [Yor](https://github.com/bridgecrewio/yor) - Automated IaC tagging tool that applies Git metadata, trace identifiers, and custom tags to Terraform resources for audit trail and ownership tracking.
- [mapotf](https://github.com/Azure/mapotf) - Meta-programming tool for Terraform that matches and transforms HCL blocks, letting module authors inject governance patterns such as `ignore_changes` rules and private-endpoint wrappers across existing modules.

### Drift Detection

- [Driftctl](https://snyk.io/) - Detect infrastructure drift between Terraform state and actual cloud resource configurations. ⚠️
- [Digger](https://digger.dev/) - Open-source Terraform CI/CD with drift detection capabilities.
- [cloud-concierge](https://github.com/dragondrop-cloud/cloud-concierge) - Open-source tool that surfaces infrastructure drift, security findings, and cost estimates as pull requests against your Terraform codebase.
- [DriftHound](https://github.com/treezio/drifthound) - Receives Terraform drift reports via API and provides a web dashboard with historical tracking, analytics, and Slack notifications.
- [atlantis-drift-detection](https://github.com/cresta/atlantis-drift-detection) - Runs Atlantis-driven `terraform plan` across every project in an `atlantis.yaml` monorepo, reports drift and untracked workspaces to Slack, and optionally triggers remediation workflows.
- [tfe-drift](https://github.com/slok/tfe-drift) - Automates drift-detection plans across Terraform Cloud and Terraform Enterprise workspaces with rate limiting, Prometheus metrics, and a ready-to-use GitHub Action.

## Policy Libraries and Rulesets

*Reusable policy collections for enforcing compliance rules on Terraform code.*

### OPA/Rego Libraries

- [Conftest](https://www.conftest.dev/) - Utility for writing tests against structured configuration data using OPA/Rego, widely used for Terraform plan validation.
- [Fugue Regula Rules](https://github.com/fugue/regula) - Library of OPA/Rego rules for Terraform covering CIS benchmarks and custom compliance checks. ⚠️
- [Regal](https://docs.styra.com/regal) - Linter for Rego policies with 50+ built-in rules covering correctness, style, and performance. Catches bugs and anti-patterns before policies reach production.
- [tflint-ruleset-opa](https://github.com/terraform-linters/tflint-ruleset-opa) - TFLint plugin for writing custom compliance rules in Rego, bridging tflint's Terraform-native linting with OPA policy evaluation.
- [Prancer Compliance Test](https://github.com/prancer-io/prancer-compliance-test) - Rego policy library with a dedicated `terraform/` ruleset for IaC scanning alongside AWS, Azure, GCP, and Kubernetes policies, designed for OPA and the Prancer platform. 💲 🆓

### Sentinel Libraries

- [terraform-sentinel-policies](https://github.com/hashicorp/terraform-sentinel-policies) - Example Sentinel policies for Terraform Cloud/Enterprise demonstrating common compliance patterns.
- [Terraform Foundational Policies](https://github.com/hashicorp/terraform-foundational-policies-library) - HashiCorp's official Sentinel policy library covering CIS benchmarks for AWS, Azure, and GCP. ⚠️

### Guard Rule Libraries

*Rule libraries for CloudFormation Guard, which evaluates Terraform plan JSON.*

- [AWS Guard Rules Registry](https://github.com/aws-cloudformation/aws-guard-rules-registry) - Official AWS registry of Guard rules covering CIS, NIST, PCI DSS, HIPAA, and SOC 2 compliance frameworks, applicable to Terraform plan JSON via cfn-guard.

## Terraform Automation Platforms

*Remote execution platforms for Terraform and OpenTofu with policy enforcement built into the run lifecycle. Unlike the CI/CD integrations below, these replace or wrap your pipeline entirely.*

- [HCP Terraform and Terraform Enterprise](https://developer.hashicorp.com/terraform/cloud-docs) - HashiCorp's Terraform execution platform with native Sentinel and OPA policy enforcement on runs, audit logging, and team access controls, available as cloud-hosted (HCP Terraform) or self-hosted (Terraform Enterprise). 💲 🆓
- [Spacelift](https://spacelift.io/) - Terraform and OpenTofu automation platform with built-in OPA policy evaluation on plans, drift detection, and custom policy frameworks. 💲 🆓
- [env0](https://www.env0.com/) - Terraform and OpenTofu automation platform with OPA and Checkov policy integration, cost governance, and environment lifecycle management. 💲 🆓
- [Scalr](https://scalr.com/) - Terraform automation platform with OPA policy enforcement and hierarchical policy inheritance across organizations, accounts, and environments. 💲 🆓
- [Terrateam](https://terrateam.io/) - GitOps-based Terraform and OpenTofu automation via GitHub and GitLab pull requests, with OPA policy enforcement, drift detection, and access controls. 💲 🆓
- [StackGuardian](https://stackguardian.io/) - Terraform and OpenTofu automation platform with OPA and Checkov policy enforcement built into every run, drift detection, and role-based access controls across environments. 💲 🆓
- [OTF](https://github.com/leg100/otf) - Open-source alternative to Terraform Enterprise with SSO, team management, and agent support, no per-resource pricing.
- [Terrakube](https://docs.terrakube.io) - Open-source Terraform automation platform with custom workflow definitions, identity provider integration via DEX, and pluggable compliance tool hooks.
- [Terrapod](https://github.com/mattrobinsonsre/terrapod) - Open-source, self-hosted Terraform and OpenTofu automation platform with governance controls, drift detection, RBAC, and HCP Terraform API compatibility.
- [ops0](https://ops0.com/) - Governance-first Terraform and OpenTofu platform with OPA and Checkov policy enforcement, drift detection, and compliance mapping to 27+ frameworks including SOC 2, HIPAA, PCI DSS, and CIS. 💲 🆓
- [Terramate](https://terramate.io/) - Open-source IaC orchestration and code generation engine for Terraform, OpenTofu, and Terragrunt stacks with change detection, policy hooks, and graph-based run ordering. Optional Terramate Cloud adds drift detection, observability, and misconfiguration reporting. 💲 🆓

## CI/CD and Platform Integration

*Tools and patterns for integrating Terraform compliance checks into deployment pipelines.*

- [Terraform Cloud Run Tasks](https://developer.hashicorp.com/terraform/cloud-docs/integrations/run-tasks) - Integration point for adding compliance checks to Terraform Cloud/Enterprise runs.
- [Atlantis](https://www.runatlantis.io/) - Self-hosted Terraform pull request automation with pre-apply policy check hooks.
- [Pre-commit Terraform](https://github.com/antonbabenko/pre-commit-terraform) - Collection of Git pre-commit hooks for Terraform including linting, validation, and security scanning.
- [grept](https://github.com/Azure/grept) - Extensible repository linter with HCL-defined rules and a plan/apply workflow, used by Azure Verified Modules to enforce license, file-structure, and content standards across Terraform module repos.
- [trunk.io](https://trunk.io/) - Developer tooling platform with Terraform linter orchestration including Checkov, tflint, and Trivy. 💲 🆓
- [Cloud Security Plugin](https://github.com/NordCoderd/cloud-security-plugin) - JetBrains IDE plugin (IntelliJ, PyCharm, etc.) for IaC security scanning including Terraform, enabling shift-left detection in the editor.

- [Terraform Risk Assessor](https://github.com/Liam-Johnston/terraform-risk-assessor) - GitHub Action that analyses Terraform plan JSON and comments risk levels on pull requests.

## Learning Resources

### Articles

- [Policy as Code on AWS](https://aws.amazon.com/blogs/infrastructure-and-automation/a-practical-guide-to-getting-started-with-policy-as-code/) - AWS practical guide to implementing policy-as-code in infrastructure workflows.
- [Terraform Best Practices](https://www.terraform-best-practices.com/) - Community-maintained guide to Terraform conventions and patterns including some security and compliance considerations. Translated into 20+ languages.
- [A Deep Dive into Terraform Static Code Analysis Tools](https://devdosvid.blog/2024/04/16/a-deep-dive-into-terraform-static-code-analysis-tools-features-and-comparisons/) - Side-by-side comparison of Terraform security scanning tools with feature matrices.
- [Shifting Cloud Security Left: Scanning Infrastructure as Code for Security Issues](https://blog.christophetd.fr/shifting-cloud-security-left-scanning-infrastructure-as-code-for-security-issues/) - Christophe Tafani-Dereeper's guide to integrating IaC security scanners into development workflows, covering tfsec, Checkov, and Terrascan.
- [Run Security Scans on Terraform and OpenTofu with Trivy and GitHub Actions](https://janik6n.net/posts/run-security-scans-on-terraform-and-opentofu-project-with-trivy-and-github-actions/) - Step-by-step guide to automating Trivy misconfiguration scanning for Terraform and OpenTofu projects in GitHub Actions pipelines.
- [Compliant Secrets with Terraform](https://infrahouse.com/blog/2024-09-30-compliant-secrets/) - Patterns for managing secrets in Terraform without exposing sensitive values in state files, covering AWS Secrets Manager and compliant credential handling.
- [ISO 27001 on AWS with Terraform](https://infrahouse.com/blog/2026-03-28-iso-27001-on-aws/) - Practical implementation of ISO 27001 controls on AWS infrastructure provisioned with Terraform, with control-to-resource mappings.

### Conference Talks

- [Securely Deploying Infrastructure as Code](https://www.youtube.com/watch?v=tPdDS3UZpOQ) - Chris Ayers at NDC Security 2023 walks through integrating Terraform security scanning tools including Checkov, tfsec, and secret detection into CI/CD pipelines.
- [Supply Chain Attacks in the Terraform Registry](https://www.youtube.com/watch?v=BZavu1e9eag) - Kyle Kotowick at NDC Security 2025 demonstrates typosquatting and malicious module attack vectors targeting the public Terraform Registry.
- [Managing Policy as Code With Terraform and Sentinel](https://www.youtube.com/watch?v=z_m4fFYym30) - HashiCorp deep dive into enforcing compliance guardrails on Terraform Cloud runs using Sentinel policies and the Foundational Policies Library.
- [Policy as Code: IT Governance With HashiCorp Sentinel](https://www.youtube.com/watch?v=ORi4ZNcUVwg) - Chris Marchesi at HashiConf 2019 introduces Sentinel as a policy-as-code framework for Terraform, Vault, Consul, and Nomad enterprise governance.
- [Open Policy Agent (OPA) Intro and Deep Dive](https://www.youtube.com/watch?v=hENwFyrtm1g) - Anders Eknert (Styra) and Xander Grzywinski (Microsoft) at KubeCon NA 2024 cover OPA fundamentals including Terraform plan validation via Conftest with production examples.

### Books

- [Terraform: Up & Running](https://www.terraformupandrunning.com/) - Yevgeniy Brikman's Terraform guide covering modules, testing, production patterns, and team workflows.
- [Infrastructure as Code](https://infrastructure-as-code.com/) - Kief Morris' guide to managing infrastructure with automation covering compliance and governance patterns.
- [The `Dao` of Terraform Modules](https://lonegunmanb.github.io/dao-of-terraform-modules-book-english/) - Free online book on Terraform module design, governance, and toolchain, by a core Azure Verified Modules developer, covering Checkov, Conftest, Trivy, grept, mapotf, tflint, and yor.

### Courses

- [Styra Academy](https://academy.styra.com/) - Free courses on OPA, Rego, and policy-as-code for infrastructure and application authorization.
- [HashiCorp Sentinel Training](https://developer.hashicorp.com/sentinel/tutorials) - Official tutorials for writing Sentinel policies in Terraform Cloud/Enterprise.

### Newsletters

- [weekly.tf](https://www.weekly.tf/) - Weekly newsletter covering Terraform, OpenTofu, and infrastructure-as-code ecosystem news.
- [tl;dr sec](https://tldrsec.com/) - Weekly newsletter covering security tooling, policy, and compliance engineering.
- [CloudSecList](https://cloudseclist.com/) - Curated cloud security newsletter covering IaC security, CSPM, and compliance tools.

## Related Awesome Lists

- [awesome-tf](https://github.com/shuaibiyy/awesome-tf) - Curated Terraform and OpenTofu resources.
- [awesome-cloud-security](https://github.com/4ndersonLin/awesome-cloud-security) - Cloud security resources across AWS, Azure, and GCP.
- [awesome-devsecops](https://github.com/JakobTheDev/awesome-devsecops) - DevSecOps tools and resources including IaC security.
- [awesome-opa](https://github.com/open-policy-agent/awesome-opa) - Open Policy Agent tools, frameworks, and articles.
- [awesome-oscal](https://github.com/oscal-club/awesome-oscal) - OSCAL ecosystem tools and resources.

## Curation Policy

This list is a curation, not a collection. Every entry must clear these gates:

**Accepted:**
- Tools, modules, or resources directly usable in Terraform or OpenTofu workflows
- Actively maintained (meaningful activity within 12 months; open-source projects need 20+ GitHub stars)
- Solves a specific compliance, security, governance, or evidence problem at the IaC layer
- Framework references must map controls to Terraform-implementable resources, not just describe the framework

**Not accepted:**
- Kubernetes-only policy tools with no Terraform integration path
- Generic cloud security or GRC platforms without a Terraform/IaC-specific integration
- Vendor blog posts or product documentation pages (learning resources must be genuinely educational, not marketing)
- Unmaintained, archived, or abandoned projects (use ⚠️ for recent deprecations only; remove truly dead projects)
- Duplicate entries covering the same tool from different angles
- Tools available only in a cloud provider console with no Terraform resource or provider support

## Contributing

Contributions welcome! Read the [contributing guidelines](contributing.md) first.
