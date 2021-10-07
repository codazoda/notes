# Interview Outline

## Database

Here are the definitions for two tables that we'll use as examples.

```
  docs
    doc_id INT(10)
    headline VARCHAR(200)
    summary TEXT
    text MEDIUMINT
    publication_date DATETIME

  comments
    comment_id INT(10)
    doc_id INT(10)
    name VARCHAR(50)
    text TEXT
    submit_date DATETIME
```

Here are two PHP code examples.

```
<?php
    $dbh = new PDO($dsn, $username, $passwd, $options);
    $dbh->query("select * from table where id = {$_GET['id']}");
?>


<?php
    foreach($_REQUEST as $k => $v) {
        include($v);
    }
?>
```

- How comfortable are you with SQL?
- How comfortable are you writing SQL?
- Write a query that returns the number of comments for a document with a doc_id of 1234.
- Write a query that returns the top 10 document headlines that have the most comments.
- What is wrong with the first PHP code sample?
- What is wrong with the second PHP code sample?
- What is a trigger?
- What is a transaction?
- How can you tell if a query is using an index? (this will show if they understand indexes, usually I want them to up with either a query plan, or the explain statement)
- How can a mySQL server be backed up? (only if they are super proficient in databases)
- What is the difference between binary and text backups? (only if they are super proficient in databases)
- Has a DBA ever gotten mad at you?  Why? (this is somewhat of a time filler)

[1]:https://drive.google.com/file/d/1C-9v8G3kTZoHw4XxCWs1k3Ktm5pls6zYkILh2RdS7t2ImMAMQBbVzYyJfqwg/view?usp=sharing
[2]:https://drive.google.com/file/d/15Ivlf1fhQhGOTrsUbOe5RzH2axLSWtYBGKw2YABjH29xkC0YyjDARvLw-mGC/view?usp=sharing

## Manager Phone Screen

- Openers

    - About me

		- People's first impression of me is that I look "stoic" or "mean"

		- My memory is sometimes terrible; asked the same question twice in an interview

    - Our team and project

	- Does that sound interesting?

	- Salary requirements?  My budget

	- What are you working on right now?

	- What are you passionate about?

	- Tell me about your preferred development environment

- Experience

	- Let's go through some specific technologies. Let me know if you have experience with it, what your experience is, and your opinions of it.

    	- HTML

		- CSS

    	- PHP

		- MySQL - Which engines, such as MyISAM or InnoDB?

		- Javascript

		- React

		- Laravel / Lumen

		- Python

		- Linux

		- Web Servers, such as Apache, and which ones?

		- Git version control

- Programming

    - Can you describe RESTful web services?

	- If you're brand new to a project and you've got a process that's erroring or crashing, what are some things you could do to troubleshoot it?

- Closing

    - Do you have any hobbies or interests?

    - What questions do you have for me?

## Backend

- Openers

	- Out team...

	- Summarize your work history

	- What are you passionate about?

	- Tell me about your preferred development environment (OS & IDE)

- General questions

	- Use any language you prefer or sudo code

	- Convert a list of comma separated words into an array (one,two,three)

	- How would you strip whitespace from a string?

	- How would you determine if a string contains only numbers?

	- Given an array of 5 words, sort it by longest word

- PHP

	- What is a php session and how do they differ from cookies?

	- How do you sanitize user data for a call to exec?

	- What is the difference between == and ===?

- Random item

    - You’ve got a list of items
        
    - Write some code to se­lect one at ran­dom
        
    - Any lan­guage, don’t wor­ry about syn­tax
        
    - As­sume the built-in ran­dom func­tion is good enough.

- General Questions

	- If you could master one technology this year, what would it be?

	- What made you decide to apply here?

	- What do you like to read?

	- Do you have any hobbies or interests?

- Culture

	- What is one of your biggest frustrations?

	- What is one thing you think you might be able to teach us?
	
	- What will I learn about you, over time, that will not be obvious to me in this interview?
	
	- What are a few things you're good at but not an expert in?

## Technical

- Openers

	- Our team...

	- Summarize your work history.

	- What experience have you had with scrum?

- Problems

    - Random item

    	- You’ve got a list of items.
        
        - Write some code to se­lect one at ran­dom.
        
        - Any lan­guage, don’t wor­ry about syn­tax.
        
        - As­sume the built-in ran­dom func­tion is good enough.

- Environment

	- Tell me about your preferred development environment (OS & IDE)

- HTML

	- What does a doctype do?

	- What is the difference between HTML and XHTML?

	- Describe the difference between cookie, sessionStorage and localStorage

- CSS

	- What is the difference between a class and an ID in CSS?

	- Describe z-index and what it does.

	- Describe media queries and how they are used for mobile specific layouts in CSS.

	- How would you implement a web design comp that uses a non-standard font?

	- What does “* { box-sizing: border-box; }” do?

- Programming

	- General questions, use any language you prefer or sudo code

	- Convert a list of comma seperated words into an array (one,two,three)

	- How would you strip whitespace from a string?

	- How would you determin if a string contains only numbers?

	- Given an array of 5 words, sort it by longest word

- Testing

	- What testing frameworks have you used?

	- What is the difference between a functional and a unit test?

- HTTP

	- What is the difference between GET and POST?

	- What is a cookie?

- Javascript

	- What is the difference between a variable that is null or undefined?

	- Can you explain AJAX?

	- What is the difference between == and ===?

- PHP

	- What is a php session and how do they differ from cookies?

	- How do you sanitize user data for a call to exec?

	- What is the difference between == and ===?

- MySQL

	- How comfortable are you with MySQL / SQL?

	- What is the difference between MyISAM and InnoDB?

	- How can you tell if a query is using an index?

	- Using this [Database Tables](DatabaseTables.md) printout:

		- Query for a list of users.  Return their id's and their first names.

		- Write a query that returns the number of comments for article 1234.

		- Write a query that returns the top 10 articles with the most comments.

	- Using this [Code Samples](CodeSamples.md) printout:

		- What is wrong with the code in sample 1?

		- What is wrong with the code in sample 2?

	- What is a trigger?

	- What is a transaction?

- MongoDB

	- Search a collection for documents that contain an 'id' of '1234'.

	- What is a Map Reduce?

- Git

   - How do you create a new git repository?

   - How do you 

- More General Questions

	- If you could master one technology this year, what would it be?

	- What made you decide to apply here?

	- What do you like to read?

	- What is one of your biggest frustrations?

	- Do you have any hobbies or interests?

## Scrum
	
- Is there anything you think is missing from Scrum?

- When estimating, what do points indicate?

- What challenges have you faced working with a Scrum team?

- Give me an overview of a retrospective meeting.

- What does a story look like?

- How might you help a team find a strong sense of purpose?

- What types of dysfunction might you encounter on a team? (5 dysfunctions of a team)

- How would you deal with those dysfunctions?

- How would you encourage everyone to openly express their opinions?

- How might you help the team identify positive and negative changes during retrospectives?

- How would you help the team to find techniques to help them be more collaborative?

- How would you help and encourage healthy conflict during team meetings?

- Do a fake sprint planning of a snow day; clear the snow from a big box store.

## Non-Technical

- Openers

	- Our team...

	- Do you have any questions for me?

	- What made you decide to apply here?

	- What do you know about this position?
	
	- What experience have you had with scrum?

- Culture

	- What is one thing you think you might be able to teach us?
	
	- What will I learn about you, over time, that will not be obvious to me in this interview?
	
	- What are a few things you're good at but not an expert in?

- Work Preferences

	- What is your preferred professional communication style?

	- Tell me about your preferred work computer?

	- Describe your ideal working space.

- Work / Life Balance

	- What books have you read lately?

	- What are you passionate about in your personal life?

	- What are you passionate about in your professional life?

- Education

	- What do you read on a weekly basis?

	- How do you typically learn and study new things?

- Personality / View of Self

	- If you had unlimited resources and could do anything what would it be?

	- When I Google you, what will I find?

- Silly Questions / Frustration Tests

	- How many cars are there in the United States?

	- Using the properties of stars, explain why barns are red

- More General Questions

	- What is one of your biggest frustrations?

## Interviewing Me

- How did your company respond to the COVID-19 pandemic?
- How do you track employee morale?
