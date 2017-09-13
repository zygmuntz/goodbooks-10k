# goodbooks-10k

This dataset contains six million ratings for ten thousand most popular (with most ratings) books. Ratings go from one to five.

There are also:

* books marked to read by the users
* book metadata (author, year, etc.) 
* tags/shelves/genres

## Contents

**ratings.csv** contains ratings sorted by time. It looks like that:

	user_id,book_id,rating
	1,258,5
	2,4081,4
	2,260,5
	2,9296,5
	2,2318,3
	
Both book IDs and user IDs are contiguous. For books, they are 1-10000, for users, 1-53424. 	

**to_read.csv** provides IDs of the books marked "to read" by each user, as **user_id,book_id** pairs, sorted by time. There are close to a million pairs.

**books.csv** has metadata for each book (goodreads IDs, authors, title, average rating, etc.).

The metadata have been extracted from goodreads XML files, available as **books_xml/books_xml.tar.gz**. The archive contains 10000 XML files. One of them is available as **books_xml/sample_book.xml**.

**book_tags.csv** contains tags/shelves/genres assigned by users to books. Tags in this file are represented by their IDs. They are sorted by `goodreads_book_id` ascending and `count` descending. 

In raw XML files, tags look like this:

	<popular_shelves>
		<shelf name="science-fiction" count="833"/>
		<shelf name="fantasy" count="543"/>
		<shelf name="sci-fi" count="542"/>
		...
		<shelf name="for-fun" count="8"/>
		<shelf name="all-time-favorites" count="8"/>
		<shelf name="science-fiction-and-fantasy" count="7"/>	
	</popular_shelves>

Here, each tag/shelf is given an ID. **tags.csv** translates tag IDs to names.

### goodreads IDs

Each book may have many editions.  **goodreads_book_id** and **best_book_id** generally point to the most popular edition of a given book, while goodreads  **work_id** refers to the book in the abstract sense. **book_id** maps to **work_id** 1:1.

You can use the goodreads book and work IDs to create URLs as follows:

https://www.goodreads.com/book/show/2767052   
https://www.goodreads.com/work/editions/2792775  

