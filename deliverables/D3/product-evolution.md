# 301 warriors

## 1. What Needed to Improve

The most significant limitations identified after D2 were the incomplete movie booking workflow and the lack of robust handling for bot-detection challenges when interacting with Cineplex's systems.

First, the movie booking workflow stopped after users selected a theatre, movie, and showtime. Although users could discover available screenings, they could not proceed through the complete booking process because seat selection and subsequent booking steps were not fully integrated. We identified this gap by evaluating the existing end-to-end user journey against our goal of building an AI-powered movie booking concierge. Selecting a showtime is only one part of making a reservation; users must also be able to view available seats, select their preferences, review booking details, and confirm their purchase. Without these capabilities, the agent functioned primarily as a movie discovery assistant rather than a complete booking solution.

Second, we identified a reliability limitation in how our Cineplex browser automation handled bot-detection and CAPTCHA challenges. When Cineplex presented a human-verification challenge, the worker needed a way to recognize that the request was blocked rather than treating it as a normal browsing or inventory failure. Without explicit challenge detection and handling, these situations could result in unsuccessful requests, unclear error responses, or automation attempting to continue without being able to access the required information.

These limitations also highlighted the importance of stronger integration between the conversational AI agent, the Cineplex backend, and the browser automation infrastructure. Each component must communicate accurate state and meaningful errors so the mobile application can respond appropriately. For example, selected seats must correspond to the chosen showtime, while a CAPTCHA challenge must be surfaced to the application as a distinct blocked state rather than an ordinary failure.

Our priorities following D2 were therefore to extend the existing discovery functionality into a more complete booking experience while improving the reliability and transparency of the browser automation. Rather than treating these as isolated features, we focused on strengthening the overall integration so users could move through the booking journey with clearer feedback, while the backend could detect and appropriately handle situations that prevented automated access.

## 2. What You Did

Following D2, our team focused on extending the movie booking experience and improving the reliability of the underlying Cineplex integration. This involved changes across the mobile application, backend services, and browser automation worker.

### Extending the Booking Workflow

We extended the existing movie discovery flow to support seat selection as another step in the booking journey. Previously, users could explore movies, theatres, and showtimes, but the workflow did not provide a way to proceed with selecting seats. To address this, we implemented a seat-map retrieval and selection flow that allows users to view the seating layout for a selected screening, identify available and unavailable seats, and select their preferred seats.

This required coordinating four interconnected components:

- **Seat-map scraping:** Extracting seat positions, labels, identifiers, and availability from supported screening previews and returning a normalized seat-map snapshot.
- **Backend integration:** Retrieving the correct screening's seat map, maintaining selected seat IDs within the authenticated chat flow, and validating screening identity, snapshot freshness, and seat availability.
- **Showtime navigation:** Connecting showtime selection to the seat-map request, passing selected seat IDs to the backend, and displaying a summary of the user's choices.
- **Interactive seat-map UI:** Rendering the seating layout with available, unavailable, and selected states, while supporting seat selection, deselection, and appropriate loading and error states.

A key design consideration was maintaining consistency between the screening and its associated seat selections. For example, if a user changes showtimes, previously selected seats must be invalidated rather than carried over to a different screening. Backend validation also ensures that submitted seat IDs belong to the correct screening and correspond to selectable seats. These measures help prevent stale or inconsistent booking information from progressing through the workflow.

### CAPTCHA and Bot-Detection Handling

Another major implementation was CAPTCHA and bot-detection handling in the Cineplex browser automation worker. Previously, when Cineplex presented a human-verification challenge, the worker needed a more reliable way to identify and communicate that automated access had been blocked.

We introduced explicit challenge detection and a structured `PROVIDER_BLOCKED` error response. When a challenge is detected, the worker captures a screenshot and generates a challenge ID so that the verification attempt can be identified and referenced. This allows provider-side restrictions to be distinguished from ordinary browsing or inventory failures.

We also introduced a PendingChallenge model and Redis-backed challenge storage to preserve pending verification information beyond an individual browser operation, rather than relying exclusively on in-memory state.

Additionally, we extended the browser abstraction to support screenshot capture through Chrome DevTools Protocol (CDP) and exposed the Browserbase LiveViewURL. This provides access to the relevant browser session for inspection when human verification is required.

On the frontend, we worked on integrating the CAPTCHA verification flow into the Ask Savi interface. The goal was to allow users to interact with the same browser session used by the worker through a supported handoff mechanism, view and solve CAPTCHA challenges, and receive updates on their status. The interface accounted for pending, completed, failed, and expired states, along with clear error messages and recovery options.

We also worked on connecting challenge status checks and completion commands to the backend so that the original operation could continue after successful verification. Additional considerations included preventing duplicate completion submissions and handling timeouts, cancellations, and interrupted sessions.

### Architectural Changes and Integration Challenges

These changes required coordination across multiple parts of the existing architecture:

- **Mobile application:** Extended the Ask Savi booking experience to support seat-map interaction, display seat selections, and integrate the CAPTCHA verification flow.
- **Backend services:** Integrated seat-map retrieval, selection validation, and challenge-state handling with existing services and interfaces.
- **Browser automation worker:** Extended browser interfaces and Cineplex automation scripts to detect verification challenges, capture screenshots, and expose browser session information.
- **Error handling and State Management:** Introduced structured error responses and Redis-backed challenge storage to preserve relevant state and communicate provider-side restrictions to downstream components.

One of the main challenges was maintaining consistency across these components. For seat selection, the screening identity and selected seat IDs needed to remain consistent between the scraper, backend, and mobile interface. For CAPTCHA handling, a challenge detected by the browser worker needed to be captured, stored, and communicated through a structured response while preserving its associated browser session. Maintaining the same session was important because restarting the browser could cause the CAPTCHA to reappear or result in the loss of the existing session context. We also needed to ensure that extending existing browser abstractions did not break other automation workflows or existing tests.

We addressed these challenges by building on existing interfaces and infrastructure rather than introducing entirely separate systems. We also added and updated tests around challenge storage, browser behaviour, and server configuration to validate the new functionality and reduce the risk of regressions.

## 3. Before vs. After

The changes from D2 to D3 expanded the booking workflow beyond movie and showtime discovery while improving the reliability of the Cineplex integration.

| Area | Before | After |
|---|---|---|
| **Movie Discovery** | Users could discover movies, theatres, and available showtimes. | The discovery workflow was extended to allow users to proceed from showtime selection to seat selection. |
| **Seat-Map Retrieval** | No seat-map retrieval was available as part of the booking workflow. | A seat-map scraper retrieves screening-specific seat layouts, including seat positions, labels, identifiers, and availability information where supported. |
| **Seat Selection** | Users could not view or choose individual seats. | Users can interact with a seat map, distinguish available, unavailable, and selected seats, and select or deselect their preferred seats. |
| **Seat Selection Validation** | Seat selections were not associated with a specific screening. | The backend validates that selected seats belong to the correct screening, have valid seat IDs, remain available, and are based on an up-to-date seat map. |
| **Selection Summary** | Users could not review a summary of their booking. | Users can review their selected seats alongside the movie, theatre, date, and showtime details. |
| **CAPTCHA Handling** | CAPTCHA challenges were not explicitly handled as a distinct state. | The worker detects CAPTCHA challenges and returns a structured `PROVIDER_BLOCKED` response. |
| **Challenge Persistence** | No dedicated mechanism existed for preserving pending challenge information. | Challenge IDs and Redis-backed storage maintain pending verification information beyond an individual browser operation. |
| **Error Handling** | Provider-side blocks could be difficult to distinguish from ordinary automation failures. | Structured errors allow downstream components to identify provider-side restrictions. |
| **Debugging** | Limited visibility into blocked browser sessions. | Screenshots and Browserbase `LiveViewURL` provide additional visibility into browser sessions requiring human verification. |

## 4. Reflection

One thing that worked well was dividing the implementation into smaller tasks with clear responsibilities across the mobile frontend, backend, and browser automation worker. This allowed team members to work on different parts of the functionality in parallel while keeping their interfaces and expected behaviour aligned. Regular integration and testing helped identify issues between components early and ensured that the individual contributions worked together as part of the overall booking workflow.

One of the harder aspects was working with the seat-map scraper and ensuring that the retrieved data was correctly represented in the frontend. Translating the scraper's output into an accurate and interactive seat-map UI required coordination between the data structure returned by the backend and how seats were displayed and selected in the mobile application.

We also encountered challenges when testing and integrating the CAPTCHA-handling functionality. Integrating the verification flow into the Ask Savi chat required coordination between the frontend, backend, and browser worker to ensure that challenge information and user interactions were communicated correctly. Simulating CAPTCHA challenges in a controlled testing environment was particularly difficult, making it challenging to validate the complete verification flow and ensure that the original browser session could continue after successful verification.

Moving toward D4, we want to focus on strengthening the end-to-end booking experience and validating the reliability of the complete integration. This includes improving test coverage for failure scenarios, verifying non-functional requirements such as accessibility and secure data handling, and implementing payment processing through the Cineplex backend and Stripe to allow users to complete and confirm their bookings. Our goal is to deliver a cohesive, reliable booking experience that supports users from movie discovery through checkout and booking confirmation.
