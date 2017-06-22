A reporting tool that prints out the reports (in plain text) based on data in the database.
This reporting tool is a Python program using psycopg2 module to connect to the database.

The database contains newspaper articles, web server log for the newspaper website.

The tools answers the following questions:
1) What are the most popular three articles of all time?
2) Who are the most popular article authors of all time?
3) On which days did more than 1% of the requests lead to errors?

The project uses Linux Virtual machine. The tools Vagrant and Virtual Box are used to install and manage the VM.
After installing vVgrant and Virtual Box, you can use Github to fork and clone the repository https://github.com/udacity/fullstack-nanodegree-vm that has the VM configuration. 

Start the VM with the vagrant up and after logging in change to the /vagrant directory which is shared with the vagrant folder on your computer.

Load data into the database by running the newsdata.sql file in the vagrant directory of VM.
Before the program is run, the following views are to be created within the news database where the tables for the project reside.

create view author_name as select distinct authors.name, articles.slug from authors join articles on  authors.id = articles.author;

create view error_count as select distinct date(time), count(status) as count from log where status like '%NOT FOUND' group by date(time);

create view req_count as select distinct date(time), count(status) as count from log group by date(time);


