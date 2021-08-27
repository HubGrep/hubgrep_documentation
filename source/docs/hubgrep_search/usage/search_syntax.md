# Search syntax cheatsheet

We are using [manticore]() as a search backend, and it has some nice functions to write your queries.
for a complete list, check out the section in the [manticore manual](https://manual.manticoresearch.com/References#Full-text-search-operators)!

## Searching in specific fields

Search for "alice" in all fields, and "carrol" in the username field

    alice @username carrol

The fields you can use are

| field | explanation |
|-------|-------------|
| username | name of user or organization |
| name | the name of the repository |
| description | the repository description |


## Searching for an exact string

Put a string in quotes, to search for exactly this phrase

    "alice in wonderland"

## Excluding a word from search

Search for results with alice, but without wonderland

    alice !wonderland

## Or-operator

Search for "wonderland" or "looking glass".

    wonderland | (looking glass)

Note that without parenthesis it would be interpreted as `(wonderland|looking) glass`, because the `|`(or) operator has higher precedence.


### Maybe-operator

If "wonderland" is in results, it influences the score (has to be uppercase!). Results containing "wonderland" but not "alice" will not match, however.

    alice MAYBE wonderland





