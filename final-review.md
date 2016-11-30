1. In a few sentences, describe a motivating example of Big Data usage in industry.

2. In a few sentences, describe two differences between big data and data intensive computing?

3. With a few sentences each, describe the 5Vs of Big Data.

4. What are the five steps in parallel programming for large data?

5. Describe the four key points in a data-intensive approach.

6. In a few sentences, define the concept of "map" in MapReduce. What is the equivalent procedure in MPI?

7. In a few sentences, define the concept of "reduce" in MapReduce. What is the equivalent procedure in MPI?

8. What are the four basic functions that a programmer can implement in MapReduce Programming paradigm?

9. Draw the diagram for MapReduce's architectural design.

10. What are the four hidden items that MapReduce handles for the programmer?

11. With a few sentences, describe the two main limitations on the MapReduce programming paradigm.

12. What are the three main application areas for MapReduce?

13. What are the six design assumptions/goals of HDFS?

14. True or False. Explain your answer.
  a. HDFS is a distributed file system with no bottleneck
  b. The Datanodes store and replicate the individual files
  c. Only the NameNode has the knowledge about where the blocks of the files are stored
  d. The NameNode populates the namespace by contacting the Datanodes and acquiring the metadata
  e. The NameNode periodically contacts the DataNodes to make sure that the DataNodes are active.
  f. Data blocks are replicated multiple times on a single Datanode with RAID support to avoid failure.
  g. When data blocks are written to HDFS, all replications of each block are written at the same time to improve performance.

15. Draw the diagram that shows the integrated relationships between NameNode, DataNodes, Resource Manager, and Node Manager.

16. What are the three key differences between Hadoop 1.0 and Hadoop 2.0?

17. Distinguish between the two optimization approaches, Combiner and In-Mapper Combining, in term of memory requirements, process slots, and shuffle bandwidth.

18. What are the five basic programming patterns for MapReduce?

19. In a few sentences each, describe Partitioning and Binning. What is the tradeoff between these two approaches?

20. Give two different data sets, when can we use Map-side join and when can we use Reduce-side join to merge these data sets? What is a possible alternative to Reduce-side join?

21. Describe the three techniques for chain-folding.

22. What are the target systems and target applications for Spark?

23. What is resilient distributed dataset (RDD)? What are the three characteristics of RDD

24. Describe two applications that are not suitable for Spark and two application that are
27. WIth a few sentences each, describe the underlying architectural concepts for Apache Tez, Apache Spark, and Tachyon.
28. What are the performance challenges in distributed data-intensive computing that Apache Tez, Apache Spark, and Tachyon address?
29. What are the five design assumptions for Tachyon?
30. What are the seven key architectural details for Tachyon?
31. What are the four major components of HPCC?
32. What are the roles of Thor and Roxie in HPCC?
33. List the respected components for Hadoop and HPCC regarding: a) Distributed File System, b) Database capability, c) Data warehouse, and d) Programming languages
34. How can we differentiate between a traditional high performance computing infrastructure (e.g., Beowulf/Palmetto) and a data-intensive computing infrastructure (e.g., Hadoop)
35. What are the two significant limitations in running data-intensive computing application on traditional high performance computing infrastructure in a shared research computing environment? How does PCI Gen 3 Fabric help to alleviate this problem?
36. What are the seven requirements of Stream Processing Engine?
37. Draw a figure that describes the LAMBDA architecture

Be prepared to answer programming questions of the following types:

1. Explain the differences between the three MapReduce implementations of the Airline Delay Time examples

2. Given the following schema for the Movie Rating dataset:

Ratings Data File (250MB)
Each line of these rating data files represents one rating of one movie by one user, and has the following format: UserID::MovieID::Rating::Timestamp
Ratings are made on a 5-star scale, with half-star increments.
Timestamps represent seconds since midnight Coordinated Universal Time (UTC) of January 1, 1970.
Example:
4359::196::3.5::1111755804
70532::2580::4::1111532718
10832::6105::4.5::1137699169
63454::648::3::843184248

Tags Data File (3.5MB)
All tags are contained in the file tags.dat. Each line of this file represents one tag applied to one movie by one user, and has the following format: UserID::MovieID::Tag::Timestamp
Tags are user generated metadata about movies. Each tag is typically a single word, or short phrase. The meaning, value and purpose of a particular tag is determined by each user.
Timestamps represent seconds since midnight Coordinated Universal Time (UTC) of January 1, 1970.
Example:
146::2795::road trip::1225067248
146::2804::based on a book::1198565440
146::2819::based on a book::1226826284
146::2820::based on a play::1206924981
146::2820::Shakespeare::1206924981
146::2821::based on a play::1204116898

Movies Data File Structure (510KB)
Movie information is contained in the file movies.dat. Each line of this file represents one movie, and has the following format: MovieID::Title::Genres
Genres are a pipe-separated list, and are selected from the following:
Action, Adventure, Animation, Children's, Comedy, Crime, Documentary, Drama, Fantasy, Film-Noir, Horror, Musical, Mystery, Romance, Sci-Fi, Thriller, War, Western
Example:
11::American President, The (1995)::Comedy|Drama|Romance
12::Dracula: Dead and Loving It (1995)::Comedy|Horror
13::Balto (1995)::Animation|Children
14::Nixon (1995)::Drama
15::Cutthroat Island (1995)::Action|Adventure|Romance
16::Casino (1995)::Crime|Drama
17::Sense and Sensibility (1995)::Comedy|Drama|Romance
18::Four Rooms (1995)::Comedy|Drama|Thriller

Write pseudo-code to implement each of the following questions using a single MapReduce program:

a. Identify the genre with the highest rating for each year between 2000 and 2010
b. Which user provides the ratings most frequently (Which user has the lowest mean-time between ratings)
c. A continuous string of ratings for a user happens when the user submits at least one rating each month for several months in a row, one month after the next, with no gaps.  Identify the user with the longest continuous string of ratings
d. Identify the user who provides the most rating and also identify which genre does this user watch the most?

While the pseudo-codes are not required to be syntactically correct, it should clearly illustrate the architecture for the Mapper/Reducer class and function and any other necessary support classes. 75% of the grade is based on the correctness of the answers, and 25% of the grade is based on how well the pseudo-codes will perform.  
4. Given a MapReduce pattern, be able to redraw and fold/merge to simply the pattern
