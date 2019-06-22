# CRMS - Change Request Management System
This is a proof of concept, change management tool, designed for use on cellular tellecommunications optimisation projects, but it could actually be used anywhere.  It is email based where users interact with a server to request or send information, which is then processed (or rejected with a reason) and sent to the next person in the chain.  All change data and status data is stored in a mysql DB in several forms, the main being an accumulating snapshot, which is ideal for tracking processes.  The tool is fully autonomous and can be updated from an administrator email.  Users self register and the admin will verify their position which will give them rights to create or approve changes.  The code basically checks an email server for new emails after a timeout of say 10s or so, once it finds some emails, it processes them sequentially, looking for key instruction text in the hear or body as well as any required attachments.  It then acts based on each email, either opening a CR, moving a CR to the next point in the chain, rejecting the email or performing DB queries for the management or admin.  All users need to be registered with certain rights, which they do by sending in an email, which is then sent to a designated manager for approval and then they are added to the user DB.

*  It uses XL spreadsheets to send/receive CRs because that is what telco corporates like to use, don't talk to me about some stupid web interface with clunky fields that you have to enter info into one by one with dropdown menus and the like.  What if you have 1000 different changes to add to the system.  Lots of arguing on this.  But basically after 20 years in the cellular industry and having suffered through many professional CR tools that were a nightmare to use, and XL spreadsheet based system was a no-brainer, I would say even today it would be, possibly allow submissions via csv would be an imrpovement, but not web page based, not for data entry, absolutely not.  Anyone who makes a tool using a web page interface for this task, has no idea what the hell they are doing, no practical experience.
*  It uses mySQL for the back end DB, because it's free and easy to use.
*  It uses VB.NET as the application software, because I was messing around with .net at the time and VB seemed easier to deal with than C#, however, after having to convert a bunch of modules from C# to VB, the two are really not that different.  Looking back, I should have written it in Python or something, but that LINQ sucked me in.

I wrote it as the project I was on was suffering from the chaos of too many engineers touching a live cellular network without adequate change management, this is a common problem in cellular.  I had a upper level sponsor to support me and encourage me, it was a good experience in coding, however, as I basically coded alone.  I definitely fell into the lack of modularisation trap, however, the code works great, it was used on a live network for around 3 months before the vendor finally bit the bullet and allowed the project team to use one of their full fledged change management tools for free, which was our goal in the first place (to prod a stubborn management).  Coming back to the tool, even 1 year later, the lack of modularisation and spiders web graph like interconnectedness, makes it nasty to get back into.  So I learned some lessons here on keeping your code as simple and modular as possible for the sake of the future.  What worked really well, was .net, it was easy to publish on windows, easy to setup background workers, easy to make dialogs, linq was great, my error handling structure worked really well, made it really easy to debug when I was emailed failure event reports from the application.  I would definietely consider re-writing this tool in python or something in the future as it was so useful, also with a web interface.  However, the email interface was actually great for a corporate project setting, you can utilise the built-in security of the email system.  Maybe a web interface would be good for analytics.
