# Project Pulse implementation plan

## Goal

Build a lightweight, static Project Pulse dashboard that lets contributors see
active projects, owners, status, recent activity, priority or risk, and a
concise summary at a glance. The dashboard should be responsive, accessible,
and launch directly to its interface in VS Code.

## Ordered implementation phases

### 1. Confirm the shared interface

- **Orchestrator:** Coordinate the specialists, keep file ownership explicit,
  and integrate and verify their work.
- **Planner:** Confirm the phases, dependencies, edge cases, and validation
  criteria in this plan.
- **Designer:** Define the dashboard hierarchy, responsive behavior, accessible
  color and status treatment, and visual direction for project cards.
- **Coder:** Agree on the project data fields and HTML/CSS hooks before
  implementation so the files work together.

### 2. Build the dashboard foundation

- **Coder — `app/project-data.json`:** Create a top-level `projects` array.
  Include representative entries with `name`, `owner`, `status`,
  `recentActivity`, and `priority`; use consistent status and priority values.
- **Designer — `app/styles.css`:** Implement the responsive visual system,
  including readable spacing and contrast, visible status and priority
  treatments, and reusable `.dashboard` and `.project-card` hooks.

These two assignments can proceed in **parallel** once the data contract and
CSS hooks are agreed, because they are separate files and neither requires the
other's implementation details.

### 3. Integrate the interface and launch configuration

- **Coder — `app/index.html`:** Build a semantic, accessible Project Pulse
  dashboard interface, link `styles.css`, and present project information
  using the agreed data contract. Handle an unavailable or invalid data file
  clearly rather than presenting a misleading empty success state.
- **Coder — `.vscode/launch.json`:** Add strict JSON for the **Run Project
  Pulse Dashboard** launch configuration. Serve from `${workspaceFolder}/app`
  and open `index.html`, so launch shows the dashboard instead of a directory
  listing.

This phase follows the foundation phase: the HTML must use the agreed style
hooks and data shape, and the launch configuration must target the completed
app location.

### 4. Integrate and validate

- **Orchestrator:** Check that the page, styles, data, and launch configuration
  agree; resolve integration issues with the responsible specialist.
- **Coder:** Run the app using the configured launch target and verify that
  `index.html` opens and the dashboard displays project cards and their
  required details.
- **Designer:** Review the rendered dashboard at narrow and wide viewport
  sizes for hierarchy, readability, contrast, keyboard access, and responsive
  layout.
- Validate that `project-data.json` parses as JSON, contains the required
  top-level array and fields, and that the launch configuration parses as
  strict JSON with the required name, working directory, and page target.

## Dependencies and ordering

- The data contract and CSS hooks are agreed before implementation.
- `app/index.html` depends on the data shape in `app/project-data.json` and
  selectors in `app/styles.css`.
- `.vscode/launch.json` depends on the app directory and entry page being
  established.
- Integration and validation happen after all assigned files are available.

## Parallel work decisions

- `app/project-data.json` and `app/styles.css` can be implemented in parallel
  after their shared contracts are agreed.
- `app/index.html` should follow those contracts and can be implemented after
  the foundation is defined.
- `.vscode/launch.json` and the HTML integration may be prepared in parallel
  once the `app/` path and `index.html` entry point are fixed; final launch
  validation depends on both.
- Final integration and validation are sequential and follow implementation.

## Validation expectations

- Confirm the page shows the Project Pulse dashboard, not a server directory
  listing.
- Confirm each project card presents its name, owner, status, recent activity,
  priority, and contributor-friendly summary.
- Confirm the responsive layout and accessible text/status presentation remain
  clear at narrow and wide sizes.
- Parse the JSON and strict launch configuration, then launch the app using
  **Run Project Pulse Dashboard** and verify its target is `app/index.html`.
