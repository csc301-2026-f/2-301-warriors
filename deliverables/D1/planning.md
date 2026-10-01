# 301 Warriors
> _Note:_ This document will evolve throughout your project. You commit regularly to this file while working on the project (especially edits/additions/deletions to the _Highlights_ section). 
 > **This document will serve as a master plan between your team, your partner and your TA.**

## Product Details
 
#### Q1: What is the product?

We are building Savi AI, a mobile app (iOS and Android) where you can ask Savi, an AI assistant, to find and book movie tickets at any Cineplex theatre for you, either once or automatically every week.

Now, what is the problem that we’re trying to solve? Booking a movie ticket is not hard, but it is repetitive. Think about someone who goes to the movies with a friend every Tuesday. Every week, they open the Cineplex app or website, pick the same theatre, scroll through the movies, choose a format and showtime, find two seats together, pick a payment method, and check out. It only takes a few minutes, but it is the same few minutes every single week, and most of the choices never change.

We think this process should take zero thought. You should be able to say what you want once, and have it handled for you.

We are working with Savi Finance and helping develop/create this AI agentic system for them, the project is the Cineplex Movie Booking AI Concierge Agent.

What does the product do, and moreso, how does it work? Savi AI lets users book movies by simply asking for them in a chat. Behind the scenes, Savi goes through the Cineplex booking process on the user's own account: it picks the theatre, the movie, the seats, and the payment method, pays for the tickets, and lets the user know when the booking is done. Users can follow along in the app while Savi works, and can step in to change anything they want.

The app has two main modes:
1. One-Time Ticket Mode: The user asks for something like "Buy me 2 tickets to a premium action movie tonight." Savi recommends a theatre and a few movies, and the user can adjust the number of seats or split the bill with friends before picking a showtime and seats.
2. Auto-Book Routine: The user sets up a weekly routine (for example, every Tuesday). Each week, Savi finds the best seats for them and asks for a quick approval before paying. The user can approve it, skip the week, or change the format, showtime, or seats.

![Ticket Modes](ticket-modes.png)

Below, I’ll list some common use cases of our project:
- A couple who sees a movie every Tuesday night and wants the same theatre, format, and seats booked automatically each week.
- A group of friends who want to go to a movie tonight, and want to split the cost without one person paying and chasing everyone for money.
- Someone who just knows the kind of movie they want to see (for example, "something action in IMAX") and does not want to browse showtimes themselves.

Finally, why does this really matter? Beyond saving time for movie-goers, this project is a small look at where apps may be heading: instead of navigating menus and forms, users just say what they want, and an AI agent takes care of the rest.



#### Q2: Who are your target users?

Our target users are Cineplex customers who want a more convenient, personalized way to book movie tickets without manually navigating the traditional booking process.

**Persona 1: The Routine Moviegoer**

A customer who watches movies regularly and has established preferences for theatres, showtimes, seating, and payment methods. They want Savi AI to remember these preferences and automate recurring movie bookings, making it easier to maintain their moviegoing routine.

**Persona 2: The Convenience-Focused Customer**

A customer who enjoys watching movies but has limited time to browse theatres, compare showtimes, select seats, and complete checkout. They want to make a simple request through the mobile app, such as booking two tickets for a particular movie at a nearby theatre, and have the AI concierge handle the booking process.

While routine moviegoers benefit from personalized, recurring automation, occasional moviegoers benefit from a simpler, faster way to book individual outings.

#### Q3: Why would your users choose your product? What are they using today to solve their problem/need?

Today, Cineplex customers typically use the Cineplex website or mobile app to manually select a theatre, movie, showtime, number of tickers, seats, and payment method. While this works for individual bookings, the process can become repetitive for customers who watch movies regularly or already know their preferences.

**Savi AI** provides an alternative through an AI-powered concierge that allows users to describe what they want in a simple request. Instead of navigating each step themselves, users can ask Savi to book a movie based on their preferences, while the system handles theatre selection, showtime selection, seat selection, and checkout.

The main benefits are **convenience, personalization, and automation**. Savi can remember preferences such as preferred theatres, seating, and payment methods, reducing repeated inputs and the number of manual steps required for future bookings. For routine moviegoers, recurring bookings can further reduce the effort required to plan regular movie outings. For individual bookings, users can make a request without manually navigating through multiple booking screens.

While Cineplex already provides a digital booking experience, Savi differs by introducing a **conversational AI interface and autonomous booking process**. Rather than requiring users to operate the interface themselves, Savi is designed to carry out the booking on their behalf and allow users to view the booking and follow the agent's progress through the mobile application.

This approach supports our partner's goal of exploring how **AI agents can move beyond traditional interfaces and automate everyday tasks**, while providing Cineplex customers with a more seamless way to book and manage their movie experiences.

#### Q4: What are the user stories that make up the Minumum Viable Product (MVP)?

 * At least 5 user stories concerning the main features of the application - note that this can broken down further
 * You must follow proper user story format (as taught in lecture) ```As a <user of the app>, I want to <do something in the app> in order to <accomplish some goal>```
 * User stories must contain acceptance criteria. Examples of user stories with different formats can be found here: https://www.justinmind.com/blog/user-story-examples/. **It is important that you provide a link to an artifact containing your user stories**.
 * If you have a partner, these must be reviewed and accepted by them. You need to include the evidence of partner approval (e.g., screenshot from email) or at least communication to the partner (e.g., email you sent)

#### Q5: Have you decided on how you will build it? Share what you know now or tell us the options you are considering.

Our partner has specified the preferred technology stack for this project:

- **Backend:** Go
- **Frontend:** React Native with TypeScript and styled-components, for a shared iOS/Android codebase
- **Development tooling:** Claude, Codex, and Cursor as AI-assisted coding tools throughout the project

Since we are continuing an existing, partly-built prototype rather than starting from scratch, our architecture decisions build on what the partner has already set up. The remaining components we are responsible for are:

- **Web browser traversal & payment:** Automating the Cineplex booking flow (theatre, movie, showtime, seat, and payment selection) on the user's behalf. Since our backend is in Go, we are considering browser automation libraries that integrate natively with Go (e.g., driving headless Chrome via the Chrome DevTools Protocol) rather than introducing a separate automation service in another language.
- **Mobile RAG integration:** Retrieving a user's stored preferences (preferred theatre, seat type, price range, genre, booking frequency) so the AI agent can make contextually appropriate decisions without the user re-specifying them each time.
- **UI/Front-end:** Building the chat-based request flow, a live view of the agent's booking progress, and a confirmation step before any payment is made.
- **Stretch goal:** Exploring the HTTP 402 "Payment Required" status code in the context of agent-conducted payments, to better understand emerging standards for AI agents handling payment flows autonomously.

We have not yet finalized our exact deployment process or third-party dependencies beyond what the partner will provide, and will confirm these details with our partner as we get further into development.

----
## Intellectual Property Confidentiality Agreement 

Our partner has agreed that we may share the work our team creates for this project, including our code and software. We will not share code created by the partner or other contributors unless they give us permission.

----

## Teamwork Details

#### Q6: Have you met with your team?

Yes, we have met each other!

For our team-building activity, we decided to meet up online and play a competitive drawing game called Skribbl.io. We played two rounds, where each person took turns drawing different words while the rest of us tried to guess the word. It was a very fun way to get to know each other outside of our project responsibilities, learn more about one another, and bring out our competitive spirits. 

Here is the leaderboard at the end of our game. Although everyone tried their best to win, Jeremy came out on top and stood first place!

![Skribbl.io leaderboard](image.png)

**Fun-facts!**

* Akram is a big Mario fan and enjoys the Super Mario games and characters.
* Tarun grew up watching Pokémon, making it one of the shows he remembers fondly from his childhood.
* Zainab is a coffee lover and enjoys having coffee as part of her daily routine.
* Aadya loves watching sitcoms and her favorite one is Modern Family 



#### Q7: What are the roles & responsibilities on the team?

Describe the different roles on the team and the responsibilities associated with each role (e.g., frontend, database). 
 * Roles should reflect the structure of your team and be appropriate for your project. One person may have multiple roles.  
 * Add role(s) to your Team-[Team_Number]-[Team_Name].csv file on the main folder.
 * At least one person must be identified as the dedicated partner liaison. They need to have great organization and communication skills.
 * Everyone must contribute to code. Students who don't contribute to code enough will receive a lower mark at the end of the term.

List each team member and:
 * A description of their role(s) and responsibilities including the components they'll work on and non-software related work
 * Why did you choose them to take that role? Specify if they are interested in learning that part, experienced in it, or any other reasons. Do no make things up. This part is not graded but may be reviewed later.


#### Q8: How will you work as a team?

Our team attends the online tutorial on Tuesdays to answer the TA’s questions and discuss our progress. We also meet online on Tuesdays from 6:30–7:00 p.m. for the team-building activity. After tutorial, we discuss the following week’s work, assign tasks, and identify any blockers.

We meet with our project partner online every Wednesday from 10:40–11:00 p.m. to review user stories, get feedback, and agree on next steps. We will have two partner meetings before D1 is due; if needed, we will schedule an additional online meeting before the deadline. For the rest of the term, we will continue the weekly Wednesday schedule and arrange coding sessions or code reviews as needed. We will record minutes for each partner meeting in deliverables/minutes.

#### Q9: How will you organize your team?

List/describe the artifacts you will produce to organize your team. (We strongly recommend that you use standard collaboration tools like Linear.app, Jira, Slack, Discord, GitHub.)       

 * Artifacts can be To-Do lists, Task boards, schedule(s), meeting minutes, etc.
 * We want to understand:
   * How do you keep track of what needs to get done? (You must grant your TA and partner access to systems you use to manage work)
   * **How do you prioritize tasks?**
   * How do tasks get assigned to team members?
   * How do you determine the status of work from inception to completion?

#### Q10: What are the rules regarding how your team works?

**Communications:**

Our team meets approximately 1–2 times per week, usually through Google Meet, to discuss our progress, upcoming tasks, blockers, and next steps. We use Discord as our primary method of internal communication for updates, questions, reminders, and coordination between meetings.
For communication with our partner, we use Slack, where we have a shared group chat. The team representative is primarily responsible for broader communication with the partner, such as scheduling meetings, confirming decisions, and discussing project-wide questions. However, individual team members may contact the partner directly when they have specific technical or task-related questions.
 
**Collaboration:**

All team members are expected to attend scheduled tutorial meetings. For internal team meetings and partner meetings, members should avoid missing more than one meeting consecutively unless there is a valid reason. We believe regular communication and frequent check-ins are important for keeping everyone aligned and ensuring that issues are identified early.

Team members are also expected to complete their assigned tasks by the agreed deadlines and communicate early if they are unable to do so. If a team member becomes unresponsive or repeatedly fails to complete assigned work, the team representative will first contact them through Discord, our primary communication channel. If there is still no response, we will attempt to reach them by email.
If the issue continues, it will be documented in the individual feedback required by the course, and the team will clearly record any incomplete or unfulfilled responsibilities in the relevant deliverable documentation.

## Organisation Details

#### Q11. How does your team fit within the overall team organisation of the partner?
Given the current team structure of our partner, our team will contribute mainly towards the Product Development of the Cineplex AI Concierge service. Our main task would be to build on the existing codebase and complete the end-to-end implementation of the Booking and AI Payment System that is to be offer through this service.
	
We are fit for this role due to our prior technical experience and eagerness to learn. Team members have previously worked with full-stack projects, AI integrations through LLM APIs, RAG, prompt engineering, NLP, and machine learning and developed applications with tools like TypeScript, React/Next.js, Python, REST APIs, PostgreSQL, and Docker. We have also taken courses like CSC311 and CSC309 which have further strengthened our technical capabilities. This gives us a strong foundation for working across the different components of the Cineplex AI Concierge 

We are also eager to put in our time to learn new concepts and frameworks required for this project such as browser automation, secure agentic payment, Go, React Native and apply our existing experience to working with the partner's codebase. By combining our existing knowledge and new technologies, we believe we would be able to help deliver a seamless, reliable, and production-ready booking experience.

#### Q12. How does your project fit within the overall product from the partner?

Savi Finance's core product is a personal finance app that brings together connected accounts, spending insights, financial goals, and AI-powered planning tools in one place. The Cineplex AI Concierge is a new feature being added on top of that existing product — it is not a standalone app, and it is not the foundation the rest of Savi Finance is built on.

```mermaid
graph TD
    A[Savi Finance App] --> B[Connected Accounts]
    A --> C[Spending Insights]
    A --> D[Financial Goals]
    A --> E[AI Planning Tools]
    A --> F[Cineplex AI Concierge]

    F --> F1[Chat-based booking request]
    F --> F2[Browser automation + payment]
    F --> F3[One-time & auto-book modes]

    style F fill:#f9d77e,stroke:#333,stroke-width:2px
    style F1 fill:#fff,stroke:#999
    style F2 fill:#fff,stroke:#999
    style F3 fill:#fff,stroke:#999
```

*(the highlighted branch is our team's scope)*

Our project is not the first prototype of this feature — Savi Finance already has an existing, partly-built implementation (described as roughly half complete and tested), covering the earlier modules of the booking flow. Our team is taking full ownership of completing the remaining core pieces: the web browser traversal payment section, mobile RAG integration for preference-based booking, and the UI/front-end, with a stretch goal of exploring agent-conducted payments (HTTP 402 flow).

Our partner has confirmed that no other team is working on this feature in parallel — our team is the sole group responsible for completing the Cineplex AI Concierge this term.

Unlike a typical course prototype, our partner intends to launch this feature directly to production after this term. They already have a group of users confirmed to use it weekly, so success for them is not just a working demo: it's a feature that is production-ready and reliable enough to launch, with the goal of expanding into similar AI-agent-driven experiences if it proves successful, or otherwise remaining live and supported for its existing user base.

## Potential Risks

#### Q13. What are some potential risks to your project?

1. ***The Cineplex website could change or block automated booking.***
   Savi books tickets by going through the Cineplex website the same way a person would. That means our product depends on a website we don't control. If Cineplex changes its layout, adds a CAPTCHA, or starts detecting and blocking automated visits, the booking flow could break without warning. We also need to confirm with our partner that booking this way is allowed under Cineplex's terms of use, since that affects whether the product can safely launch.

2. ***We are building on code we did not write.***
   The project continues an existing prototype that is described as about halfway done and well tested. That is a big head start, but it also means we need time to understand someone else's code and decisions before we can build on them. If the existing code is harder to work with than expected, or has gaps we don't know about yet, it could slow down the parts we are responsible for.

3. ***Letting an AI agent pay is risky.***
   Most bugs in an app are annoying. A bug here could charge someone for the wrong movie, the wrong number of seats, or book twice. Payment is also the part of the project that is newest to us (including the HTTP 402 "Payment Required" flow), and checkouts often include extra verification steps like a bank confirmation screen that an agent may not be able to get through on its own. On top of that, Savi works on the user's own Cineplex account, so it needs access to their login and saved payment methods.

4. ***The right theatre, movie, and seats are not clearly defined.***
   The expected features say the system should pick the right theatre, movie, seats, and payment method. But what counts as "right" is open to interpretation. If a user asks for "a premium action movie tonight," does that mean IMAX or UltraAVX? What if their usual seats are taken, or the showtime is sold out? If we don't pin these down with our partner, our user stories may end up too vague to build or test, and the result may not match what our partner had in mind.

#### Q14. What are some potential mitigation strategies for the risks you identified?
* Examples of mitigation strategies:
  * More communication with the partner might help with improving clarity.
  * Adding more details for an user story might make it less abstract.
  * Adding an extra user story might increase the project complexity, making it less simple.
* It's ok if you are unable to find mitigation strategies for all the risks right now.
