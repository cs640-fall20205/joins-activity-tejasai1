# Assignment 2


## Day 1


0.  Read Day 1. Skip section on Unions on page 270. Work through the
    examples in the text. Save your database to dump.rdb (see README.md).


1. What is the URL to Redis' documentation on its commands:

```

```

2. What is the runtime complexity (in Big-O notation) for LSET?

```

```

3. Let's explore the equivalence of MUTLI blocks and SQL-style transactions.
    In an SQL-style transaction if any operation in the transaction fails,
    none of the operations succeed (even the ones that appear before the
    failing command). Is this true for MULTI blocks? Make an experiment
    to determine or confirm your answer and write the statements you executed
    below.

```

```

4. What two commands would you use to use a list as a stack?

```

```

5. The text tells us that ZINCRBY will increment the score of an entry.
    But the text only shows that it returns the incremented score, but
    does not show that the score for the entry has actually been changed
    in the sorted set. Write a short example that determines if ZINCRBY
    actually changes the score of an entry.

```

```

6. By default Discord expires invite links in 7 days. Reproduce this concept
    in Redis by storing a key named 'link' whose value is a URL (your choice),
    that expires in 7 days. Do it in a single command. Write that command below.

```

```


## Day 2

Read the following sections in Day 2.
You do not have to "do" them. Just read and study them.

1. Publish-subscribe
2. Durability
3. Snapshotting
4. Append-Only File
5. Security
6. Master-Slave Replication

There is nothing to turn in for Day 2.

## Day 3 - Skip


## Submission

1. The following files should contain all your work for this assignment:
    * assignment2.md
    * dump.rdb
2. All work must be submitted to your individual GitLab account to be considered submitted.
    * Use `save-and-stop` or just `save` in GitPod to save your work to GitLab.
    * Confirm your submission by opening your repository in a browser on GitLab (not GitPod).
    * If this fails, work with your instructor to fix the problem before the grace period ends.

