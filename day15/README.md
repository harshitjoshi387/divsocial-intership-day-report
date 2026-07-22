Day 5 · Session 2 — SQL, NoSQL & How Data Is Stored

Full-Stack Internship · Module 4: Database Instructor: Dinesh Rawat

This is a recap of everything covered in today's class, plus the four research questions left for tomorrow's presentation.

1. Database vs DBMS
Database = an organised collection of data. Just data, kept in order so it can be found.
DBMS (Database Management System) = the software that stores and manages a database — it saves data, reads it back, keeps it safe, and lets many users access it at once.
Examples: MySQL, PostgreSQL, Oracle, MongoDB.
When you "install MySQL", you're really installing a DBMS.
People often use "database" loosely for both, but now the difference is clear: the database is the data, the DBMS is the program that manages it.
2. Language vs Query
A language is how you talk to a DBMS (just like JavaScript talks to a browser). The most common database language is SQL.
A query is a single question or command sent to the database (e.g. "give me all users from Haldwani", "add this new user"). Every read/write your app does is a query.
So: language = how you speak to the database; query = one thing you say in that language.
3. SQL vs NoSQL: The Two Families
	SQL (e.g. MySQL)	NoSQL (e.g. MongoDB)
Shape	Tables, fixed columns	Flexible documents
Every record	Same columns	Can differ
Plan shape first?	Yes	Not required
Good for	Data with a clear, steady structure	Data that changes shape a lot
SQL databases store data in tables with fixed columns, like a spreadsheet — every row has the same shape.
NoSQL databases store data more freely (often as documents) — different records can have different fields.
Neither is "better" — they're tools for different jobs. Our resume project uses MySQL because a user and a resume have a clear, steady shape.
4. RDBMS — Where "Relational" Comes In
RDBMS (Relational Database Management System) = a DBMS for SQL databases where tables can be related to each other (e.g. a user table linked to a resume table via a foreign key).
That link between tables is exactly what "relational" means.
So MySQL is three things at once:
A DBMS (manages data)
A SQL database (uses tables + the SQL language)
An RDBMS (its tables relate to each other)
5. Structured vs Unstructured Data
Structured data: fixed, predictable shape — fits neatly into rows/columns (e.g. a user's name, email, a resume's title, an order's total). SQL databases are built for this.
Unstructured data: no fixed shape — a photo, a video, a voice recording, free-text chat. Doesn't fit tidy columns; often lives in NoSQL stores or as files.
Our resume fields (name, email, title) are structured, which is why MySQL fits the project.
6. CHAR vs VARCHAR vs STRING
CHAR(n): fixed length. Always reserves n characters worth of space, padding unused space with blanks. Best for values that are always the same length (e.g. a country code like "IN").
VARCHAR(n): variable length. Can hold up to n characters but only uses the space it actually needs. Best for everyday text — names, emails, titles.
STRING: not a real MySQL type — it's a Sequelize word. DataTypes.STRING in a model becomes VARCHAR(255) in MySQL. Same thing, two layers (JS name vs. real DB column).

Example — storing "Deepesh" (7 letters) in a size-10 column:

CHAR(10) → uses all 10 cells (7 letters + 3 padding spaces)
VARCHAR(10) → uses only 7 cells (nothing wasted)

Rule of thumb: use VARCHAR for text that varies in length; use CHAR only when every value is exactly the same size.

7. More MySQL Types: ENUM, BOOLEAN, TINYINT
Type	Holds	Use for
ENUM	One value from a fixed list	status, role, provider
BOOLEAN	True or false	isVerified, isActive
TINYINT	Small number (0–255)	Storage behind BOOLEAN, small counts
ENUM: only allows values from a predefined list (e.g. ENUM('active', 'pending', 'deleted')). MySQL refuses anything else — keeps the column honest.
BOOLEAN: answers a yes/no question about a row.
TINYINT: MySQL has no separate true/false type under the hood — BOOLEAN is actually stored as TINYINT(1) (1 = true, 0 = false). Two names, one storage.
Design takeaway: pick the tightest type that fits your data — a status should be an ENUM (not free text), a yes/no should be a BOOLEAN (not the string "yes"). The type is your first line of defence for clean data.
8. Why Learn SQL Commands When Sequelize Writes SQL For Us?

Even though Sequelize (the ORM) generates SQL automatically, learning raw SQL matters because:

Debugging — when a Sequelize query misbehaves, you can turn on logging, read the generated SQL, and run it yourself in Workbench.
Direct data checks — you can run SELECT yourself in Workbench to confirm data, without needing the app.
Understanding the ORM — Sequelize is a convenience layer, not a replacement for understanding SQL. Knowing SQL means the ORM stops being "magic."
Transferable skill — not every job uses Sequelize, but SQL is the same across MySQL, PostgreSQL, Python, Java, and data analyst roles. The ORM changes; SQL doesn't.

Summary: The ORM writes SQL so you don't have to, day-to-day — but when something breaks, or you move to a project without an ORM, SQL is what saves you.