# Tuple

Tuple is a simple set of functions for operating on tuples. It is lightweight with few abstractions, concepts to understand, or assumptions about the underlying use cases.

That said, it was designed out of my frustration with processing and parsing SQL result sets. More than not I find myself reaching for heavy-weight ORMs for the wrong reasons. For example, I often use an ORM out of laziness so I don't have to manually parse and transform the tabular output of SQL queries into a hierarchical format that is better suited for application processing (e.g. outputting as JSON, etc.) This library hopes to make simple tasks like this (i.e. SQL queries to JSON output) easier.

# Status

Tuple is in very early stage of development. Right now I am focusing on designing the API and interface and less about actual implementation. Any examples shown in this README do not work for real and are there to help explore features and syntaxes.


# API



    results = SQL.execute('SELECT students.id
    ,  students.name
    ,  students.email
    ,  students.gender
    ,  class_enrollments.id
    FROM students
      JOIN class_enrollments ON class_enrollments.student_id = students.id
    ;')
    
    # Option 1
    students = Tuple::NormalizeSet.new
    
    for result in results do
      students.merge(result, {key: 0, has_many: 4})
    end
    
    # Option 2
    students = Tuple::NormalizeSet.new
    students.merge_all(results, {key: 0, has_many: 4})
    students.reduce(results, {key: 0, has_many: 4})
    students.collect(results, {key: 0, has_many: 4})
    
    # Output
    
    assert students[0][0] == 0                    # id
    assert students[0][1] == 'bob'                # name
    assert students[0][2] == 'bob@example.com'    # email
    assert students[0][3] == 'm'                  # gender
    assert students[0][4] == [0, 4, 8]            # the collapsed class_enrollments as an array
    

    



