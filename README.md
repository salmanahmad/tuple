# Tuple

Tuple is a simple set of functions for operating on tuples. It is lightweight with few abstractions, concepts to understand, or assumptions about the underly use case.

That said, it was designed out of my frustration with processing and parsing SQL result sets. More than not I find myself reaching for heavy-weight ORMs for the wrong reasons. For example, I often use an ORM out of laziness so I don't have to manually parse and transform the tabular output of SQL queries into a hierarchical format that is better suited for application processing (e.g. outputting as JSON, etc.) This library hopes to make simple tasks like this (i.e. SQL queries to JSON output) easier.

# Status

Tuple is in very early stage of development. Right now I am focusing on designing the API and interface and less about actual implementation. Any examples shown in this README do not work for real and are there to help explore features and syntaxes.



