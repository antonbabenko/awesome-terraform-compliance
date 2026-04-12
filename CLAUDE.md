# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an **awesome list** (curated resource list) for Terraform/OpenTofu compliance, security, and governance tools. It follows the [awesome-list](https://github.com/sindresorhus/awesome) format. There is no application code, build system, or test suite.

The sole content file is `readme.md` — a categorized, annotated link collection maintained by Anton Babenko.

## Editing Guidelines

- **Link format**: `[Tool Name](URL) - Description ending with a period.` Descriptions should be a single sentence explaining what the tool does and why it's relevant to Terraform compliance.
- **Legend icons** appear at the end of entries: `💲` (commercial), `🆓` (free tier), `🏛️` (government/public sector), `🇪🇺` (European regulation specific), `⚠️` (archived/deprecated/maintenance mode).
- **Section order** matters — entries within each section are loosely ordered by relevance/popularity, not alphabetically.
- **Table of Contents** in the `## Contents` section must be kept in sync with any added/removed/renamed sections.

## Writing Style

All descriptions must pass a humanizer check before being added. Rules:

- **No em dashes** (—). Use a comma, period, or restructure the sentence instead.
- **No AI vocabulary**: avoid "comprehensive", "foundational", "pivotal", "crucial", "vital", "landscape", "tapestry", "showcase", "foster", "underscore", "highlight" (as verb), "serving as", "stands as", "marks a".
- **No copula avoidance**: write "is" or "are" instead of "serves as", "functions as", "stands as".
- **No fake-depth -ing phrases**: avoid tacking "...complementing X", "...fostering Y", "...highlighting Z" onto the end of sentences to add perceived depth.
- **No promotional language**: "leading", "groundbreaking", "breathtaking", "vibrant", "robust", "powerful".
- **Keep all technical terminology**: Terraform, OpenTofu, OPA, Sentinel, Checkov, tfsec, Trivy, KICS, SOC 2, HIPAA, PCI DSS, NIS2, DORA, FedRAMP, OSCAL, CIS, NIST, etc. are precise terms and must not be replaced with synonyms.
- **Vary sentence structure**: not every description should follow the same "[Tool] is a [category] that [does X]" template.
- **Be specific**: "1,000+ built-in policies" beats "extensive policy coverage".

## Curation Principles

Before adding any entry, verify it passes ALL of these:

**In scope:**
- Has direct Terraform or OpenTofu integration (module, provider, CLI tool, or policy evaluation against `terraform plan` JSON)
- Actively maintained: last commit within 12 months; open-source projects need 20+ GitHub stars
- Solves a compliance, security, governance, or evidence problem — not general DevOps tooling

**Out of scope — do not add:**
- Kubernetes-only tools (Kyverno, Gatekeeper standalone) unless there is a documented Terraform integration path
- Generic GRC/audit platforms without a Terraform state or IaC-specific integration
- Vendor blog posts, product documentation, or feature pages for tools already listed
- Tools where Terraform support is incidental (e.g., a CloudFormation-first tool that also reads Terraform plan JSON)
- Anything unmaintained, archived, or sunset (mark with ⚠️ if recently deprecated; remove if truly dead)

**Special rules:**
- One entry per tool. No separate entries for a tool's individual features (e.g., a drift detection entry AND a main platform entry for the same product).
- Learning resources must be genuinely educational — no vendor content marketing, no anonymous/low-authority blog posts.
- Conference talks must be from a named conference (HashiConf, KubeCon, NDC, re:Invent, DevSecCon) and publicly available.

## Validation

There is no CI or linting configured. When reviewing changes, manually verify:
- All URLs are valid and not duplicated
- Descriptions follow the single-sentence format with trailing period
- Legend icons are correctly applied
- TOC anchors match section headings
