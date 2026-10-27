# 301 Warriors

**NOTE**: the partner’s repo already had a D2 tag pointing to unrelated work, so the submission is tagged 301-warriors-D2. here’s the snapshot link: https://github.com/cheapreats/ce/tree/301-warriors-D2
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

Our project introduces an AI-powered Cineplex booking concierge as a new feature within Savi Finance. Users can request for movie bookings, set their preferences, and easily explore movie options, all through a natural conversation. The agent handles everything from interpreting your request to confirming the final booking details.

This feature aims to replace the repetitive and time-consuming nature of traditional movie booking by reducing the need to manually navigate through the Cineplex website while still giving the user full control of the payment/booking process.

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

## Key Use Cases

The current version of this project supports the following use cases:
1. **Movie discovery**: Find movies currently playing at Cineplex theatres near a specified location (i.e. user's location) and date.

2. **Filter movie options**: Search by genre, new releases, format (IMAX or UltraAVX), occasion, or preferred time.

3. **Find and select showtimes**: View and select available movies and showtimes for a selected theatre and date.

4. **Refine requests conversationally**: Change the location, date, theatre, movie, or time without restarting the search.

5. **Remember preferences**: Save preferences such as a usual theatre, favourite genres, preferred format, or viewing time.

6. **Start a new request**: Reset the current search and begin a new movie discovery request.

<img src="deliverables/D2/usecase_ex.png" alt="A screenshot of the app showing a simple user request and cineplex movie discovery tool" width="250">
<img src="deliverables/D2/usecase_ex2.png" alt="A screenshot of the app showing the user's saved preferrences" width="250">

**Left**: shows a simple user request and the search results based on the request. 

**Right**: shows the user setting their preferrences for the agent to remember for future bookings. 

Use cases such as ticket purchasing, reserving seats, and checkout are NOT included in this version. 

**Current Functionality to Test**
The current grading build supports movie discovery through the predefined suggestion chips (buttons) in Ask Savi. Tap a movie suggestion chip to trigger the implemented flow and review the movie, theatre, and showtime information displayed in the app.


## Instructions for use

### 1. Install the app

Open the link in an **incognito/private browser window only**.
**[Download the grading APK](https://expo.dev/accounts/tarunnn65/projects/savi-finance/builds/99a46d44-fec8-4705-8018-f2c5a2bda637)** or scan the QR code below. 

![APK download QR code](apkqr.png)

- **Android:** Download and open the `.apk` file, follow the installation prompts, then open Savi Finance.
- **Mac:** Start an Android emulator through Android Studio’s **Virtual Device Manager**. Drag the downloaded APK onto the **running emulator window**, then open Savi Finance.

The app opens signed in to a **demo account**. Internet access is required. The APK does not run on iPhones or the iOS Simulator.

### 2. Open Ask Savi

Select the **Ask Savi** tab at the bottom of the screen.
![home screen](sc1.png)

### 3. Test movie discovery
**Use the chips to test this build.** Manually typed requests currently return the default AI response. Booking and payment are not included.

Tap a suggestion chip:
- **Movies near me**
- **Theatres in Waterloo**
- **Movies tonight**
- **Pick a movie for me**

Review the displayed **theatre, movie, and showtime options**.


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

- `feat(cineplex): <feature-name>` for new functionality
- `fix(cineplex): <issue-name>` for bug fixes
- `docs(cineplex): <change-name>` for documentation changes

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

Here is a link to a demo of the app: https://drive.google.com/drive/folders/1O4-SBhU0E2u_yQp2FOtGiVEq8jyFI5Ef?usp=sharing

## D3 Improvement Highlight

**Not there yet.**
