# 301 Warriors

**NOTE**: the partner’s repo already had a D2 tag pointing to unrelated work, so the submission is tagged 301-warriors-D2. here’s the snapshot link: https://github.com/cheapreats/ce/tree/301-warriors-D2
​
## Partner Introduction
**Partner Organization**: Savi Finance

**Primary Point of Contact**: 
 * Name: Ralph Maamari
 * Email: ralphpalxyz@gmail.com
 * Title: Co-founder and CEO of Savi Finance
 * Role: Primary Point of Contact

**About the Partner Organization**:

Savi Finance is a Toronto-based personal finance technology company focused on helping people take control of their financial future. Its platform brings financial accounts, spending insights, goals, and planning tools together in one place, with AI-powered features designed to make financial management simpler and more accessible.

## Description

Our project introduces an AI-powered Cineplex booking concierge as a new feature within Savi Finance. Designed for moviegoers, the agent allows users to request movie recommendations and bookings, set personal preferences, and explore available movie options through natural conversation. It interprets user requests, helps discover theatres, movies, and showtimes, and guides users through seat selection and reviewing their booking summary.

This feature aims to simplify the traditional movie-booking process by reducing the need to manually navigate the Cineplex website. Users can discover and select their preferred movie options conversationally while maintaining control over the final booking and payment process.

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

## Core Workflow

The current version of this project supports the following use cases:

1. **Movie Discovery**: Find movies currently playing at Cineplex theatres near a specified location (i.e. user's location) and date.

2. **Filter Movie Options**: Search by genre, new releases, format (IMAX or UltraAVX), occasion, or preferred time.

3. **Find and Select Showtimes**: View and select available movies and showtimes for a selected theatre and date.

4. **Refine Requests Conversationally**: Change the location, date, theatre, movie, or time without restarting the search.

5. **Remember Preferences**: Save preferences such as a usual theatre, favourite genres, preferred format, or viewing time.

6. **Start a New Request**: Reset the current search and begin a new movie discovery request.

7. **Select a Seat**: Automatically select the best available seats based on the number of tickets, or manually choose preferred seats from the seating map. Users can also switch to D-BOX seating.

9. **Review Booking Summary**: View a summary of the selected theatre, movie, showtime, and seats. This does not include checkout or payment processing.

### Example Screenshots:

#### Movie Discovery and Saved Preferences

<p align="center">
  <img src="deliverables/D3/movie-discovery.jpg" alt="Movie discovery request and search results" width="250">
  <img src="deliverables/D2/usecase_ex2.png" alt="User setting saved preferences for the agent" width="250">
</p>

<p align="center">
  <em>Left: A user request and the movie discovery results generated from it.</em><br>
  <em>Right: The user setting preferences for the agent to remember for future bookings.</em>
</p>

#### Seat Selection and Booking Summary

<p align="center">
  <img src="deliverables/D3/seat_selection.jpg" alt="Savi automatically selecting seats for a movie booking" width="250">
  <img src="deliverables/D3/seat_map.jpg" alt="Cineplex seating map showing available, occupied, and accessible seats" width="250">
  <img src="deliverables/D3/booking_summary.jpg" alt="Booking summary displaying the selected movie, showtime, and seats" width="250">
</p>

<p align="center">
  <em>Left: Savi's automatic seat selection.</em><br>
  <em>Centre: The seating map where users can change their seats.</em><br>
  <em>Right: The final booking summary before checkout.</em>
</p>

## Instructions For Use

### 1. Install the app

Open the link in an **incognito/private browser window only**.

## For D2:
**[Download the grading APK for D2](https://expo.dev/accounts/tarunnn65/projects/savi-finance/builds/99a46d44-fec8-4705-8018-f2c5a2bda637)** or scan the QR code below.

![D2 APK download QR code](deliverables/D2/apkqr.png)

## For D3:
**[Download the grading APK for D3](https://expo.dev/artifacts/eas/yDBSoeRq_DHV07A_PkVaqQOMjscm2JDK-AVscRAHISs.apk)** or scan the QR code below. 
![D3 APK download QR code](deliverables/D3/apkqrcode.png)

- **Android:** Download and open the `.apk` file, follow the installation prompts, then open Savi Finance.
- **Mac:** Start an Android emulator through Android Studio’s **Virtual Device Manager**. Drag the downloaded APK onto the **running emulator window**, then open Savi Finance.

The app opens signed in to a **demo account**. Internet access is required. The APK does not run on iPhones or the iOS Simulator.

### 2. Open Ask Savi

Select the **Ask Savi** tab at the bottom of the screen.

### 3. Movie Discovery
**Use the suggestion chips to test this build.** Manually typed requests currently return the default AI response. Booking and payment are not included.

Tap one of the following suggestion chips:
- **Movies near me**
- **Theatres in Waterloo**
- **Movies tonight**
- **Pick a movie for me**

Manually select a **theatre** to view its available movies and showtimes. Savi automatically selects the best available movie, showtime, and seats based on your request. Select `Other Movies` to explore alternative movie and showtime options.

### 4. Seat Selection
After selecting a theatre, movie, and showtime, Savi automatically selects the best available seats based on the number of tickets.

To change the selection:
1. Click `Change Seats`.
2. Choose your preferred seats on the seating map.
3. Optionally switch to D-BOX seating.
4. Review the seating map, which indicates available, occupied, and accessible seats, with labels explaining each category.
5. Click `Use These Seats`, then click `Save` to proceed to the final booking summary.

## Testing

Frameworks: Go's `testing` package run through Bazel (backend and Cineplex worker), Node scripts, Python `unittest`, and Jest (mobile app).

### Run the tests (no credentials needed)

From `sf1/`:

```bash
bazel test //api/rpc/handlers/send_ai_chat_message/... //cineplex-browser-worker/...
node cineplex-browser-worker/seat_preview_dom_test.mjs
python3 -B -m unittest discover -s cineplex-browser-worker -p run_live_seats_test.py
```

Then the mobile app:

```bash
cd sba-mobile && npm ci && npm test -- ask-savi
```

Each command prints the passing and failing tests. The Bazel and Jest suites also run in CI on pull requests (`.github/workflows/ci_pr.yaml`).

### What is covered

| Area | Tests |
|---|---|
| Seat map extraction, normalization and validation | `sf1/api/rpc/handlers/send_ai_chat_message/cineplex/seat_map_test.go`, `sf1/cineplex-browser-worker/seat_map_test.go`, `seat_preview_test.go` |
| Saved-page replay: normalized showtimes match the real Cineplex page they came from | `sf1/cineplex-browser-worker/saved_page_replay_test.go` |
| Seat preview reading different page structures | `sf1/cineplex-browser-worker/seat_preview_dom_test.mjs` |
| Live-test runner safety (opt-in only, credentials stay private) | `sf1/cineplex-browser-worker/run_live_seats_test.py` |
| `cineplex_discovery` AI tool (inputs, outputs, error codes) | `sf1/api/rpc/handlers/send_ai_chat_message/tools/cineplex_discovery_test.go` |
| Ask Savi showtime, theatre and chat cards | `sba-mobile/components/ask-savi/*.spec.tsx` |

### Live end-to-end test (needs Browserbase credentials)

This test calls the real Cineplex site through Browserbase. It covers theatre and showtime discovery, live seat retrieval, and backend normalization of the seat map. It uses one paid Browserbase session, so it is optional and is not part of CI.

**Requirements:** Bazel (or Bazelisk) on your `PATH`, a Linux or WSL environment, and Browserbase credentials.

From `sf1/`:

```bash
export BROWSERBASE_API_KEY=<your key>
export BROWSERBASE_PROJECT_ID=<your project id>
CINEPLEX_LIVE_PRODUCTION_SEATS=1 python3 cineplex-browser-worker/run_live_seats.py
```

The script builds the worker test, runs it, then validates the result with the backend's production `DecodeSeatMapResult`. The last line is the result:

- `RESULT: PASS`: the live seat map was retrieved and passed backend validation.
- `RESULT: UNAVAILABLE` (exit code 2): Cineplex blocked the request or no suitable showing was found. This is not a code failure, so run it again later.
- `RESULT: FAIL`: setup or validation failed, and the message says which step.
- `RESULT: SKIP`: the opt-in variable `CINEPLEX_LIVE_PRODUCTION_SEATS=1` was not set, so nothing ran.

Optional: `CINEPLEX_LIVE_SELECTION=first` (default) or `alternate` chooses which suitable showing is used. Do not set `CINEPLEX_PREVIEW_URL` or `CINEPLEX_TARGET_SHOWTIME_ID`, because the script refuses to run with them.

## Development Requirements
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

Open the link in an **incognito/private browser window** to download the APK.
**[Download the APK for D2](https://expo.dev/accounts/tarunnn65/projects/savi-finance/builds/99a46d44-fec8-4705-8018-f2c5a2bda637)** 
**[Download the grading APK for D3](https://expo.dev/artifacts/eas/yDBSoeRq_DHV07A_PkVaqQOMjscm2JDK-AVscRAHISs.apk)** or scan the QR code below.


See [Instructions for use](#instructions-for-use) above for **Android installation** and **Mac emulator** instructions.

This evaluation build is signed in to a **demo account**. Test using the **movie suggestion chips**; manually typed movie requests currently return the default AI response.

[Watch the D3 app demo on Google Drive](https://drive.google.com/drive/folders/1YgJ7Md3n5PAKQMQkcc001SYnELHp-_mQ)


## D3 Improvement Highlight

Since D2, we have extended the booking workflow beyond movie and showtime discovery by implementing automatic and manual seat selection, allowing users to customize their seats and review a final booking summary. We also implemented CAPTCHA and bot-detection handling in the Cineplex worker to detect provider-side challenges and return structured error responses. Users can explore the seat-selection improvements after choosing a theatre, movie, and showtime, while the CAPTCHA handling operates in the backend during Cineplex interactions.

## Non-Functional Requirements

### Accessibility

We considered mobile accessibility by aiming to make the movie discovery and booking workflow clear and easy to navigate. The interface uses clear labels and visual indicators to distinguish available, occupied, and accessible seats. We also included a zoom-in feature that allows users to view the seating map more closely when selecting their seats.

<p align="center">
  <img src="deliverables/D3/labels.jpg" alt="Seat selection interface with labels and visual indicators" width="250">
  <img src="deliverables/D3/zoom1.jpg" alt="Seating map showing the zoom-in option" width="250">
  <img src="deliverables/D3/zoom2.jpg" alt="Zoomed-in seating map with zoom-in and zoom-out options" width="250">
</p>

<p align="center">
  <em>Left: Seat labels and visual indicators.</em><br>
  <em>Centre: Seating map with the zoom-in option.</em><br>
  <em>Right: Enlarged seating map with zoom-in and zoom-out controls.</em>
</p>

### Security and Data Handling

We considered security throughout the Cineplex integration by implementing structured error handling for provider-side CAPTCHA and bot-detection challenges. The backend tracks pending challenges, validates browser session ownership, and independently verifies that a challenge has been resolved before replaying the original operation. This prevents the frontend from simply declaring a CAPTCHA solved without backend verification.

We also use environment-based configuration for sensitive credentials, including the Cineplex worker service secret and Browserbase API credentials, rather than embedding these values directly in the worker's source code.

**CAPTCHA Detection/Response**

The worker detects provider-side CAPTCHA and bot-detection challenges and routes blocked requests to the challenge-handling logic, returning a structured error response.

In `sf1/cineplex-browser-worker/handlers.go`, function `SearchTheatres`:

```go
if out["providerBlocked"] == true {
    return nil, h.blockedChallengeError(c, s, p)
}
```

**Challenge Tracking**

When an interactive challenge is detected, the backend creates and stores a PendingChallenge record containing the challenge ID, session information, original operation, status, and expiration time.

In `sf1/cineplex-browser-worker/handlers.go`, function `blockedChallengeError`:

```go
record := PendingChallenge{
		ID:                id,
		BookingSessionID:  c.Envelope.BookingSessionID,
		BrowserSessionID:  c.Envelope.BrowserSessionID,
		ProviderSessionID: s.SessionID,
		Operation:         c.Envelope.Command,
		Payload:           payload,
		Status:            ChallengePending,
		CreatedAt:         createdAt,
		ExpiresAt:         expiresAt,
	}
	if err := h.Challenges.Create(record); err != nil {
		return blocked
	}

	blocked.ChallengeID = id
	blocked.CaptchaScreenshot = screenshot
	blocked.LiveViewURL = h.challengeLiveView(ctx, c, record)
	return blocked
```

**Backend Verification**

In `sf1/cineplex-browser-worker/handlers.go`, the `CompleteChallenge` function validates browser session ownership, inspects the browser state, and independently verifies that the CAPTCHA challenge has been resolved before replaying the original operation.

```go
if s.SessionID != record.ProviderSessionID {
    return h.finishChallenge(c, record, ChallengeExpired, "BROWSER_SESSION_REPLACED")
}

browserState, stateErr := h.inspectCaptchaBrowser(
    verifyCtx,
    c,
    s,
    record.Operation,
)

if browserState.ChallengeVisible {
    return pending()
}

verified, verifyErr := h.CaptchaVerifier.Verify(verifyCtx, browserState)
if verifyErr != nil {
    return fail(asCommandError(verifyErr, ErrProviderUnavailable))
}
if !verified {
    return fail(&CommandError{Code: ErrChallengeFailed})
}
```

**Credential Configuration**

In `sf1/cineplex-browser-worker/core.go`, in function `ParseConfig`, the worker loads its service authentication secret and Browserbase credentials from environment variables and validates that the required service secret is configured.

```go
c := Config{
    Environment:  strings.TrimSpace(env["ENVIRONMENT"]),
    ServiceSecret: strings.TrimSpace(env["CINEPLEX_BROWSER_WORKER_SERVICE_SECRET"]),
    Version:      strings.TrimSpace(env["CINEPLEX_BROWSER_WORKER_VERSION"]),
    Provider:     strings.TrimSpace(env["CINEPLEX_BROWSER_WORKER_PROVIDER"]),
}

if c.ServiceSecret == "" || len(c.ServiceSecret) < 16 {
    return Config{}, fmt.Errorf("CINEPLEX_BROWSER_WORKER_SERVICE_SECRET is required")
}

c.BrowserbaseAPIKey = strings.TrimSpace(env["BROWSERBASE_API_KEY"])
c.BrowserbaseProjectID = strings.TrimSpace(env["BROWSERBASE_PROJECT_ID"])

if c.Provider == "browserbase" && (c.BrowserbaseAPIKey == "" || c.BrowserbaseProjectID == "") {
    return Config{}, fmt.Errorf("Browserbase configuration is required")
}
```
