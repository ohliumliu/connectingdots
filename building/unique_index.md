* Need to generate a migration file to add an index column which is a uniqu attribute
`add_index database_name, :attr, unique: true`

* When doing db:migrate, it will check all the existing entries.
