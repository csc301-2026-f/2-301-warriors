# 301 Warriors
​
## Partner Intro
**Partner Organization**: Savi Finance

**Primary Point of Contact**: 
 * Name: Ralph Maamari
 * Email: ralphpalxyz@gmail.com
 * Title: Co-founder and CEO of Savi Finance
 * Role: Primary Point of Contact

**About the Partner Organization**:

Savi Finance is a Toronto-based personal finance technology company focused on helping people take control of their financial future. Its platform brings financial accounts, spending insights, goals, and planning tools together in one place, with AI-powered features designed to make financial management simpler and more accessible.

## Description about the project

Our project introduces an AI-powered Cineplex booking concierge as a new feature within Savi Finance. Users can request movie tickets through a conversational interface, while the AI agent handles the booking process based on their preferences.

The feature addresses the repetitive and time-consuming nature of traditional movie booking by reducing the need to manually navigate through theatres, showtimes, seat selection, and checkout.

[View our interactive mockup](deliverables/D1/mockup.md)
​
## Key Features
### Conversational Movie Booking
Users can describe the movie experience they want in natural language. Savi interprets the request, combines it with relevant saved preferences, and proposes a suitable booking.

### Personalized Booking Preferences
Savi can remember preferences such as a user's usual ticket quantity, theatre, movie format, and seating preferences. Users can always review and override remembered information for an individual booking.

### Movie, Showtime, and Seat Selection
Users can review or modify the recommended movie, theatre, format, showtime, ticket quantity, and seats. Savi can also suggest seats based on the user's seating preferences.

### Review, Checkout, and Tickets
Before payment, users can review the complete booking and make changes. After a successful booking, Savi displays the booking confirmation and digital ticket information.

### Recurring Auto-Booking
Returning users can save recurring movie-going preferences. Savi can use these preferences to prepare a booking proposal that the user can modify, approve, or skip.

### Group Booking Coordination
Users can invite friends to a booking by Savi username or email. Savi can track participant confirmations and help coordinate whether the organizer waits, proceeds alone, purchases all tickets, or sends split-payment requests.

### Coupons, Vouchers, and Credits
During checkout, Savi can surface eligible savings from both authorized connected email accounts and Savi-provided offers. Users choose which eligible savings to apply before payment.

## Instructions
 > **Current status:** The application is still under development. The interactive mockup above can currently be used to explore the intended user experience. Production access instructions will be added once a testable mobile build is available.

### One-Time Booking

1. Open the Savi mobile application and access the Cineplex concierge.
2. Enter a natural-language request, such as a preferred movie type, time, or number of tickets.
3. Savi combines the request with relevant saved preferences and proposes a booking.
4. Review or modify the movie, theatre, ticket quantity, format, and showtime.
5. Select seats manually or use Savi's suggested seating.
6. If booking with friends, invite participants and choose how the group booking should proceed.
7. Review available coupons, vouchers, or credits and apply any desired savings.
8. Review the complete booking summary and total price.
9. Confirm checkout.
10. After a successful purchase, view the booking confirmation and tickets in Savi.

### Recurring Booking

1. Configure or save movie-going preferences.
2. Savi uses those preferences to generate a recurring booking proposal.
3. Review and modify the proposed movie, theatre, showtime, seats, and price.
4. Choose to approve the proposal or skip that booking.
5. Approved proposals continue through the normal review and checkout process.

 ## Development requirements
 ### Technology Stack

The current partner-confirmed stack includes:

- **Mobile:** React Native, TypeScript, Expo, Styled Components
- **Backend / SF1 API:** Go, MongoDB
- **Browser Automation:** Browserbase, Playwright
- **Chrome Extension:** HTML, CSS, JavaScript
- **Other option discussed with partner:** Computer Use

The existing Cineplex browser-worker also uses infrastructure including Bazel, Redis-based execution coordination, and browser automation abstractions.

### Local Development

A developer will require access to the Savi codebase and the services/configuration supplied by the partner.

 ## Deployment and Github Workflow

 ### GitHub Workflow
​The team uses `main` as the stable integration branch. Development work is completed on separate branches rather than directly on `main`.

Branches follow the convention:

- `feature/<feature-name>` for new functionality
- `fix/<issue-name>` for bug fixes
- `docs/<change-name>` for documentation changes

When a task is ready:

1. The developer pushes their branch to GitHub.
2. The developer opens a pull request from their branch into `main`.
3. At least one other team member reviews the pull request.
4. The author resolves requested changes and merge conflicts.
5. Relevant tests must pass before the pull request is merged.
6. Approved changes are merged into `main`.

### Deployment

The release flow is:

`Development Branch → Pull Request → Review & Testing → main → Deployment`

Only reviewed code merged into `main` should be eligible for deployment.

 ## Coding Standards and Guidelines
 
We follow idiomatic Go and TypeScript/React Native conventions, use descriptive naming, keep components and functions focused, and follow the existing structure of the Savi codebase. Code should be formatted and linted using the tools configured in the relevant repository, and new functionality should include appropriate testing where feasible.
​
 ## Licenses
​
This project uses the **MIT License** for code authored by the CSC301 team. We chose MIT because it is a simple and permissive license that allows others to use, modify, and distribute our code while preserving attribution and the original license notice.

This license applies only to code owned by the student team. Any pre-existing Savi Finance code, third-party libraries, or external dependencies remain subject to their original licenses and ownership terms.

## Deployed URL / Access Instructions

**Not deployed yet.**

## D3 Improvement Highlight

**Not there yet.**
