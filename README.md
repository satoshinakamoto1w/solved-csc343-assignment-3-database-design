Download Link: https://assignmentchef.com/product/solved-csc343-assignment-3-database-design
<br>
You are helping design a database back-end for Wet World’s dive booking app. Quali ed divers will use the app to book dives with a dive monitor and dive site.

Divers must be at least 16 when a dive occurs and have an open-water certi cation from one of: NAUI, CMAS, or PADI. One diver, the lead,” books a dive, possibly to include other quali ed divers, up to the limit the monitor is willing to take, and taking into account the number the dive site has capacity for at that date and time.

Each monitor has their own price list, according to whether a dive will be morning (9:30 to 11 a.m.), afternoon (12:30 to 2 p.m.) or night (8:30 to 10 p.m.), and whether the dive will be open water, cave diving, or deeper than 30 meters. The price charged by a monitor includes any fees a dive site charges per diver, and a monitor may have booking privileges with one or more dive sites. Monitors also have a maximum group size for each category: open water, cave, or deeper than 30 meters, and they set the maximum to 0 if they do not supervise that category of dive.

All dive sites provide 12 litre aluminum tanks, weight belts and bouyancy compensation vests as part of their fee. Some also provide mask, regulator, ns, and wrist-mounted dive computer, each for additional fees. In addition some sites provide free services from among: video of dives, snacks, hot showers, towel service. Each site lists a maximum number of divers, combining one or more bookings, allowed on site at any daylight hour, and lists smaller maxima for night, cave, or deeper than 30 meter dives. Each site lists one or more dive types they provide from: open water, cave dive, or beyond 30 meters.

A lead diver may book as many dives as they can nd monitors and dive sites for, but only one dive at a given date and time. No monitor is allowed to book more than two dives per 24 hour period, in order to keep their blood nitrogen at safe levels. The lead diver provides credit card information, email addresses and dive certi cation for all divers, and credit card information to secure the dive(s).

All divers may, optionally, rate a site on a scale of 0 (very poor) to 5 (excellent), and lead divers may rate monitors on the same scale.

<h1>schema</h1>

De ne a schema in DDL, stored in                le schema.ddl. Your goals, in priority order, are:

<ol>

 <li>Allow as few redundancies as possible.</li>

 <li>Allow as few NULL or DEFAULT values as possible.</li>

 <li>Without using assertions or triggers, enforce as many constraints from the database description as you can.</li>

</ol>

Wherever goals are in con ict, implement the higher-priority goal. Also you should:

De ne a primary key for each table, and in addition use UNIQUE and de ne foreign keys where appropiate.

You will be repeatedly re-importing schema.ddl as you develop and test it, so it should begin with the following:

drop schema if exists wetworldschema cascade; create schema wetworldschema; set search_path to wetworldschema;

At the top of schema.ddl use a comment to document which constraints could not be enforced, and which you chose not to enforce, and why. We will also provide a data.txt le with a plain text description of a database.

<h1>some queries</h1>

After you have nished schema.ddl de ne a new le data.sql to populate an instance of your database with sample data. We will not be autotesting this, so you get to decide on table structure and attribute names as you like. Write queries for the following:

<ol>

 <li>For each dive category from open water, cave, or beyond 30 meters, list the number of dive sites that provide that dive type and have at least one monitor with booking privileges with them who will supervise groups for that type of dive.</li>

 <li>Find monitors whose average rating is higher than that of all dives sites that the monitor uses. Report each of these monitor’s average booking fee and email.</li>

 <li>Find the average fee charged per dive (including extra charges) for dive sites that are more than half full on average, and for those that are half full or less on average. Consider both weekdays and weekends for which there is booking information. Capacity includes all divers, including monitors, at a site at a morning, afternoon, or night dive opportunity.</li>

 <li>For each dive site report the highest, lowest, and average fee charged per dive.</li>

</ol>

Queries are stored in                les q1.sql, q2.sql, q3.sql, and q4.sql.

<h1>dependencies, decompositions, normal forms</h1>

In        le dependencies.pdf report the following:

<ol>

 <li>Relation R has attributes IJKLMNOP and functional dependencies:</li>

</ol>

S<sub>P </sub>= fM ! IJL;J ! LI;JN ! KM;M ! J;KLN ! M;K ! IJL;IJ ! Kg

<ul>

 <li>Find a minimal basis for R. List the attributes in each LHS in alphabetical order, each RHS in alphabetical order, and your entire set FDs in alphabetical order.</li>

 <li>Find all keys for R.</li>

 <li>Uses 3NF to nd a lossless, dependency-preserving decomposition of R. Be sure to combine FDs with the same LHS into the same into a single relation, and omit relations that are subsets of other relations.</li>

 <li>Does your schema allow redundancy? Explain why, or why not.</li>

</ul>

Show all your intermediate steps, and explain any steps you may legitimately omit.

<ol start="2">

 <li>Relation T contains attributes CDEFGHIJ and functional dependencies:</li>

</ol>

S<sub>T </sub>= fC ! EH;DEI ! F;F ! D;EH ! CJ;J ! FGIg

<ul>

 <li>Which of the FDs in S<sub>T </sub>violate BCNF?</li>

 <li>Decompose T into a collection of relations that are each in BCNF, using the BCNF decomposition algorithm. Your decomposition should be lossless and redundancy-preventing. Show your intermediate steps, explaining any steps that you may legitimately omit. Project S<sub>T </sub>onto your nal set of relations, where every LHS and RHS is in alphabetical order, and each list of projected FDs itself should be in alphabetical order.</li>

</ul>