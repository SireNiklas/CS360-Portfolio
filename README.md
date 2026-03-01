# CS 360 — Event Tracker App

Nicholas Harris — Southern New Hampshire University

## Reflection

**Briefly summarize the requirements and goals of the app you developed. What user needs was this app designed to address?**

The app is an event tracker for Android. Users can create an account, log in, add events with dates and times, edit or delete them, and get an SMS notification the day of an event. The whole point is just helping people not forget things — appointments, deadlines, whatever. Nothing fancy, just reliable.

**What screens and features were necessary to support user needs and produce a user-centered UI for the app? How did your UI designs keep users in mind? Why were your designs successful?**

There are four screens: login, event list, add/edit event, and an SMS permission screen. The event list uses a RecyclerView to show everything in a grid with delete buttons on each row and a floating action button to add new ones. I tried to keep each screen focused on one thing so the user isn't overwhelmed. I also locked down the layouts before writing any backend code, which helped me avoid redoing work later.

**How did you approach the process of coding your app? What techniques or strategies did you use? How could those techniques or strategies be applied in the future?**

I built the database layer first with a singleton DatabaseHelper class, then wired up login, then event CRUD, then notifications last. Each piece got its own file — eight Java classes total, each with one job. That made it way easier to debug because I always knew where to look when something broke. That approach of keeping things modular is something I already do at work and it translated well here.

**How did you test to ensure your code was functional? Why is this process important, and what did it reveal?**

Tested on the emulator as I went. After each feature I'd run through the flow — create account, log in, add an event, edit it, delete it, check that the list updates. For SMS I tested both accepting and declining the permission to make sure the app didn't crash either way. Caught a few things I wouldn't have noticed just reading the code, like the empty state message not showing up correctly after deleting the last event.

**Consider the full app design and development process from initial planning to finalization. Where did you have to innovate to overcome a challenge?**

The notification system was the hardest part. Android needs SCHEDULE_EXACT_ALARM, POST_NOTIFICATIONS, and SEND_SMS to all be handled, and the app still has to work if the user says no to any of them. I built the SMS permission screen as its own activity to explain why the app needs it before hitting the user with a system dialog. That part required the most actual problem-solving.

**In what specific component of your mobile app were you particularly successful in demonstrating your knowledge, skills, and experience?**

The database layer. The singleton pattern, separated CRUD methods, clean table structure — that's the part of the codebase I'm most confident in. I work with backend systems and infrastructure professionally so structuring data access felt natural. Everything else in the app just calls into the helper without touching SQL directly, which is how it should be.
