# WolfHowl

## Challenge Description

![](https://github.com/mt3636/HackPack-CTF-2023/blob/main/WolfHowl/images/challengedescription.png)

The description says we need to log in to get the flag. To log in, we need an email and password, and to get those, we'll need to do a SQL injection.

We want to see if there's a table storing this information, so we do a `UNION SELECT` in the site's search bar and experiment with different types of databases and an increasing number of NULL parameters until `" UNION SELECT NULL, NULL, NULL, NULL FROM information_schema -- "` gets us an error message different from the "that artist does not appear to be in our list" one:

![](https://github.com/mt3636/HackPack-CTF-2023/blob/main/WolfHowl/images/tabledoesntexist.png)

So, we now need to get all the tables in the database, so we enter `" UNION SELECT table_name, NULL, NULL, NULL FROM information_schema.tables -- "` to get the page to display them.

![](https://github.com/mt3636/HackPack-CTF-2023/blob/main/WolfHowl/images/databasetables.png)

We're interested in the employee table because of the elevated privileges that'd be associated with it. `" UNION SELECT column_name, NULL, NULL, NULL FROM information_schema.columns WHERE table_name="employee" -- "` will get us all the columns of information associated with all of the employees.

