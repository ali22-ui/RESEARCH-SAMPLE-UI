# RESEARCH-SAMPLE-UI

Smart City citizen + admin portal prototype built with static HTML, Tailwind CSS (CDN), and vanilla JavaScript using `localStorage` for cross-page persistence.

## Tech Stack

- HTML5 (`index.html`, `admin.html`, `login.html`, `payment.html`)
- Tailwind CSS via CDN
- Vanilla JavaScript
- Browser `localStorage` for app state
- GitHub Actions workflow for GitHub Pages deployment (`.github/workflows/deploy-pages.yml`)

## System Modules

### Citizen Portal (`index.html`)

- Dashboard and service discovery cards
- Grouped mobile burger menu with accordion behavior
- Sticky quick-jump navigation and back-to-top actions
- Session badge and logout flow
- Bilingual service copy (English + Tagalog)

### Admin Portal (`admin.html`)

- Operations overview + KPIs
- Review queue and permit processing controls
- Queue monitor and schedule management
- Announcements publishing
- Citizen request moderation/processing

## Core Features Implemented

### 1) Face-to-Face Payment Booking

- Custom schedule input with:
  - 12-hour format (`HH`)
  - minutes limited to `00` and `30`
  - uppercase meridiem (`AM` / `PM`)
- Slot capacity enforcement per date/time
- Payment modal with cash/online handling
- Ticket ID, queue token, claim code generation
- Receipt text export/download

### 2) Document Request + Pickup Scheduling

- Request metadata capture (type, purpose, email)
- Pickup scheduling with same constrained time rules (`00/30`, `AM/PM`)
- Capacity checks and queue metadata
- Shared payment and status flow

### 3) Offline Draft Mode (Citizen)

- Draft save for appointment and document forms
- Auto-save on form input
- Explicit Save Draft / Clear Draft buttons
- Restore drafts on reload
- Online/offline status messaging
- Service card badges showing `Unsaved Draft`
- One-time pulse highlight for draft badges
  - Re-triggers after clear → new draft cycle

### 4) Smart Rebooking Suggestions (Citizen)

- When selected slot is full, system proposes nearest available alternatives
- Alternative suggestions rendered inline
- One-click apply to schedule fields

### 5) Priority Routing Engine

- Citizen-side priority metadata capture:
  - citizen type (regular/senior/PWD/pregnant/solo parent)
  - urgent flag
  - optional note
- Admin-side scoring and sorting by:
  - citizen weight
  - urgency
  - SLA aging risk
- Priority levels: `Normal`, `Medium`, `High`, `Critical`

### 6) Auto-Assign Window by Priority

- Admin action auto-routes active requests to desks/windows based on priority tier
- Assignment metadata persisted to booking records

### 7) Supervisor Override Console

- Admin can manually override booking priority level
- Required reason field
- Override metadata stored (`overrideBy`, `overrideReason`, `overrideAt`)
- Override takes precedence in routing calculations

### 8) Bulk Operations (Admin)

- Multi-select bookings (row checkbox + select-all)
- Bulk actions:
  - Confirm selected
  - Complete selected
  - Escalate to critical
  - Auto-assign desk

### 9) Escalation Queue (Admin)

- Separate queue panel for SLA-risk and critical items
- Escalation count + prioritized list for supervisor attention

### 10) Compact Request UI + Reduced Scrolling

- Compact summary request cards
- Expandable `View full details` sections to preserve full payload
- Sticky quick navigation for faster section access

### 11) Notifications, Timeline, and Support

- Citizen/admin notification feeds
- Mark-as-read actions
- Unified citizen timeline (requests, follow-ups, incidents, emergency)
- Follow-up ticketing and tracking by ticket ID
- Customer service ticket submission

### 12) Feedback, Suggestions, Incident Reporting

- Citizen feedback submission + admin insights
- Suggestion voting, moderation, and admin responses
- Incident reporting and admin resolution workflow

### 13) Emergency Operations Mode

- Admin emergency command center (activate/deactivate + severity)
- Citizen emergency banner, hotline, and help ticket submission
- Admin emergency queue actions (acknowledge/dispatch/resolve)

### 14) Accessibility + UX Enhancements (Admin)

- Large text / high contrast / reduce motion toggles
- Section title polishing and iconized headers
- Last-visited section memory (citizen + admin)

## Data Persistence

The system uses `localStorage` keys for bookings, drafts, incidents, suggestions, notifications, emergency state, profile data, and more.

## Project Structure

- `index.html` — citizen-facing portal
- `admin.html` — admin operations portal
- `login.html` — login entry page
- `payment.html` — payment ledger view
- `photos/` — static image assets
- `.github/workflows/deploy-pages.yml` — GitHub Pages deployment automation

## Run Locally

Open `login.html` or `index.html` in a browser.

## Deploy to GitHub Pages

1. Push project to GitHub repository.
2. In GitHub repo settings:
   - Go to **Settings → Pages**
   - Under **Build and deployment**, set **Source** to **GitHub Actions**
3. Push to `main` branch (or run workflow manually from **Actions** tab).
4. Site URL will be:
   - `https://<your-username>.github.io/<repo-name>/`

## Notes

- This is a prototype using browser-side storage and no backend authentication.
- For production, migrate to secure backend APIs, real auth, and server-side persistence.
