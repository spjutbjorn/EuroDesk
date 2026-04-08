# EuroDesk Synchronization Guide (sync.md)

This document outlines the strict synchronization rules and dependencies between the different files in the EuroDesk repository. As the repository grows, it is crucial to ensure that all documentation reflects the true state of the `products/` directory and the defined roles.

Whenever a change is made to the repository (adding a product, updating a role, etc.), you must follow these synchronization rules.

## 1. Product Addition / Modification (`products/*.md`)
**Rule:** The `products/` directory is the source of truth for all tools.
- **Mandatory Fields:** Every markdown file in `products/` MUST contain the exact following sections as defined in `rules.md`:
  - `**Category:**`
  - `**Type:**`
  - `**Jurisdiction:**`
  - `## Hosting Options` (or `## EU Hosting Options`)
  - `## Compliance Notes`
- **Action:** If a product is added, modified, or removed, you must proceed to Step 2, 3, 4, and 5.

## 2. Main Index (`README.md`)
**Rule:** The README must list every single product currently in the `products/` directory.
- **Action:** When a product is added or its category changes, update the corresponding category table in `README.md`.
- **Validation:** There must be zero "Missing in README" files and zero "Broken links in README".

## 3. Role Definitions (`roles.md`)
**Rule:** Defines the white-collar workforce structure.
- **Action:** If a new department or sector is added to the modern office landscape, document it here first under a new numerical heading (e.g., `### 35. New Sector`).
- **Dependency:** Any new role added here MUST be immediately reflected in `core.md`.

## 4. Role-to-Product Mapping (`core.md`)
**Rule:** Maps tools from `README.md` to roles in `roles.md`.
- **Action:** 
  - If a new product is added, assign it to the relevant roles as a "Role-Specific Core Add-on".
  - If a new role is added to `roles.md`, create a new section here and assign it the Universal Base Stack + specific tools.
- **Validation:** Every numbered category in `roles.md` must have an exact matching numbered category in `core.md`.

## 5. Verification & Audit Reports
**Rule:** Audit reports must reflect the total number of products accurately.
- **`verification_report.md`:** 
  - Must be regenerated to pull the exact `title`, `category`, `jurisdiction`, and `type` from the `products/*.md` files.
  - The total count of verified tools must match the exact number of `.md` files in the `products/` folder.
- **`audit_status.md`:** 
  - If the total number of products changes, update the "kvarstående produkter" (remaining products) count to equal `Total Products - Verified Products`.
- **`risk.md`:** 
  - Update the scale of the "Operational Complexity" risk to reflect the total number of applications (e.g., "70+ separate applications").

## Automated Checks
To verify synchronization between `products/` and `README.md`, you can run a Python script to extract links and compare them against the directory contents. Always ensure that metadata extraction scripts run successfully to update the `verification_report.md`.
