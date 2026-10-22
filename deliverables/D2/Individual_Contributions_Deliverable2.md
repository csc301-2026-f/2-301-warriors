## Team Contributions

### Tarunraj Kalyanasundaram
Extend Ask Savi’s mobile chat interface to support movie-search requests.

**Contributions:**
- Updated the Ask Savi interface to display user-submitted movie requests and a loading indicator while awaiting backend responses.
- Connected the request flow to response handling so the loading state ends when a response arrives.
  
### Zainab Siddiqui
Integrate Cineplex discovery into Ask Savi through a callable backend tool.

**Contributions:**
- Implemented the Go HTTP client and callable Cineplex discovery tool to send validated theatre and showtime search requests to the worker.
- Translated worker responses into the agreed structured format for Ask Savi and mobile consumption.
- Completed `iteration-02-review.md`.

### Akram Klai
Implement natural-language clarification for missing or ambiguous movie-search details.

**Contributions:**
- Updated the Ask Savi agent’s request interpretation and prompts to identify missing or ambiguous locations and dates.
- Added follow-up questions and preserved clarification answers across messages to establish validated search inputs without silently guessing.
- Updated `README.md` to document D2 work.

### Jeremy Chan
Implement and verify Cineplex theatre and movie/showtime discovery

**Contributions:**
- Developed and verified the discovery backend for searching Cineplex theatres and retrieving movie/showtime information.
- Returned structured results with stable identifiers and supported theatre selection when multiple locations matched.

### Aadya
Build mobile UI components for displaying Cineplex search results and errors.

**Contributions:**
- Developed theatre-selection and showtime cards displaying relevant movie and booking details.
- Added distinct UI states for empty results, blocked requests, and unavailable results, with retry behavior and theatre selection to continue the conversation.

### Samaah Abdullah
Implement bot-block detection and error handling for Cineplex discovery operations.

**Contributions:**
- Added CAPTCHA and bot-block detection to theatre and inventory searches, returning PROVIDER_BLOCKED errors with challenge details.
- Implemented browser screenshot capture and Redis-backed pending challenge storage, and added tests for challenge-store configuration.
  
### Yuan Lu
Coordinate the development environment and validate the integrated Cineplex discovery flow.

**Contributions:**
- Coordinated local development setup and tested the end-to-end journey across the mobile interface, Ask Savi agent, and Cineplex worker.
- Documented setup and testing instructions to help teammates reproduce key search flows.
- Submitted the pull request in the main repository.
