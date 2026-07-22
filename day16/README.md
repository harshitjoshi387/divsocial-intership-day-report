Worked answers to the five presentation topics. Every topic makes the same point: think like a backend developer — someone who assumes things will be attacked, and builds so they cannot break. Read your own topic closely, but all five connect into one lesson.

1. The CBSE Portal — How Marks Could Be Changed (Himanshu's topic)

What happened (from news reports): In 2026, a 19-year-old named Nisarga Adhikary, who had just finished Class 12, looked at CBSE's On-Screen Marking (OSM) portal — where teachers evaluate scanned answer sheets online. He found basic security holes and reported them. CBSE first denied any breach, then later acknowledged vulnerabilities in the provider's portal and ordered an audit. He didn't exploit it for gain — he reported it, which is exactly what an ethical hacker does.

The flaws, and what each teaches:

The flaw	The backend lesson
A master password was written into the source code, visible in the browser	Never put secrets in code that reaches the browser — anyone can read it with Ctrl+F
The OTP check could be bypassed	A security check the client can skip is not a security check
Password reset didn't ask for the old password — any user ID + gibberish reset it	The server must verify every step; never trust that the client did the checking
An examiner's identity could be edited through browser storage	Never trust data from the browser — the server decides who you are, not the client
Internal dashboards were open with no login	Every private route needs an access-control check, on the server, every time

One-sentence answer: The marks were changeable because the system trusted the browser. Passwords, identities, and checks all lived where the user could see and edit them. In his own words: "These aren't advanced defences. They're the basics." A backend developer's first rule is the opposite of what CBSE did: never trust the client, verify everything on the server.

2. How 10,000+ Records Get Created in Minutes (Deepesh's topic — happened at Shorter Loop)

A human types slowly — creating 10,000 records by hand would take days. So it wasn't done by hand. It was done by a script: a small program that repeats an action in a loop, as fast as the server allows. This isn't advanced — it's a beginner-level loop pointed at an unprotected endpoint.

Why a site lets this happen, and how to stop it:

What was missing	The fix a backend developer adds
No rate limit	Cap how many requests one user/IP can make per minute
No bot check on the form	A CAPTCHA (or similar) on public create-endpoints
The endpoint was open, no login needed to create records	Require authentication so anonymous scripts can't post at will
No validation catching obviously fake/duplicate data	Server-side validation and duplicate checks that reject junk

One-sentence answer: 10,000 records appeared because a script hit an endpoint with no rate limit, no bot check, and no login. Lesson: assume any open endpoint will be hit by a machine, not a polite human — and put limits in before it happens, not after.

3. What Information Is Kept in the UI (Divya Bora's topic)

The UI is the HTML, CSS, and JavaScript that runs in the browser. The single most important fact: everything in it is visible to everyone. Anyone can right-click → "view source" or open dev tools and read every line.

What lives in the UI	Remember
Page structure & text (HTML)	Readable by anyone, always
Styling (CSS)	Readable, harmless, fine to be public
Logic that runs in the browser (JavaScript)	Fully readable — never hide a secret in it
Values stored in the browser (local storage, cookies)	Readable and editable by the user

One-sentence answer: The UI holds only what you're willing to show the whole world, because the whole world can read it. This is exactly the CBSE mistake: a master password sat in browser code, and browser storage decided who you were. Rule: never put a secret, a password, or a trust decision in the UI — the browser is the user's territory, not yours.

4. Who Are Ethical Hackers (Gaurav & Ayush's topic)

An ethical hacker uses the same skills as an attacker, but with permission, to find security holes so they can be fixed before a real attacker uses them. Same knowledge, opposite intent — done legally and reported responsibly.

Ethical hacker	Malicious hacker
Has permission, or reports responsibly	No permission, hides the act
Finds a hole and tells the owner to fix it	Uses the hole for gain or damage
Makes systems safer	Makes victims
Paid by companies, bug bounties, security jobs	Faces jail

Nisarga (from Topic 1) is the live example — he found serious flaws and reported them to the authorities and CERT-In instead of exploiting them for money. That single choice — report it rather than abuse it — is the whole line between the two columns.

One-sentence answer: Ethical hackers are the people who find the holes before criminals do, with permission and in the open — and it's a real, paid career. The skills are the same as an attacker's; the intent and legality are what make them ethical.

5. The Movie: Pritam Pedro (Anishka & Divyani's topic)

Pritam Pedro is Rajkumar Hirani's 2026 cybercrime thriller on JioHotstar. It pairs two opposite cops — Pedro, an old-school investigator who trusts traditional methods, and Pritam, a young tech-savvy officer who works through modern technology and code. Together they solve cybercrimes, starting with a mystery around an abandoned ATM on a beach and building to a kidnapping case.

Watch for these while viewing:

The two mindsets — Pedro trusts instinct, Pritam trusts the system and the code. A backend developer needs both: discipline to verify everything, and instinct to sense when something is wrong.
Where does trust break? — Cybercrime happens because someone trusted something they shouldn't have (a system, a person, a piece of data) — the exact lesson from the CBSE topic.
What's exposed, and what's hidden? — Connects to what we learned about the UI exposing everything, and identities being faked through the browser.
How is the attacker caught? — The tech-savvy investigation is backend thinking in action: following data, spotting what doesn't add up.
The Coding Side: What a Clicked Link Actually Reveals

The practical task here is the "location from a link" question — most people get it wrong.

What people believe	What actually happens
A clicked link reveals exact location	It reveals only the public IP — city/ISP level at best
You can read their local address (192.168.x.x)	You cannot — it stays inside their router, never reaches any server

Why the local IP never arrives: A device has a private address (e.g. 192.168.1.7) inside its home network. On the way out, the router swaps it for the one public IP the whole house shares — this is called NAT. Your server only ever receives that public IP; the private one never leaves the local network.

So how do "they found my exact location from a link" stories happen? Almost never the link by itself:

How exact location really leaks	What it needs
The page asks "Allow Location?" and the person taps Allow	The person's own consent — the GPS prompt can't be skipped
The person uploaded a photo/post with location, or has malware/a hacked account	The person handing data over themselves, or an already-compromised device
Police mapping an IP to a real address	A legal request to the ISP — not something a normal person can do

One-sentence answer: A link on its own leaks only the public IP — a rough area, never a street address, never the local IP. Exact location requires the person's consent, their own leaked data, or something already compromised. That gap between what people fear and what actually happens is pure backend thinking: the server only sees what the request carries.

What to bring back: Don't just retell the plot — bring three moments that connect to misplaced trust, exposed information, scale, or how a crime was traced through the system.

The Thread Through All Five

One idea, five topics:

Marks were changed because the browser was trusted.
Records were flooded because an endpoint had no limits.
The UI exposes everything because it runs on the user's machine.
Ethical hackers are the people who find these gaps first.
The film makes the mindset stick.

The single sentence under all of it: A backend developer assumes attack, never trusts the client, and verifies everything on the server.