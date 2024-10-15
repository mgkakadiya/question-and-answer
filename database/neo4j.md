
# RDBMS Vs Graph Database

Following is the table which compares Relational databases and Graph databases.

| Sr.No | RDBMS                | Graph Database         |
|-------|----------------------|------------------------|
| 1     | Tables               | Graphs                 |
| 2     | Rows                 | Nodes                  |
| 3     | Columns and Data     | Properties and its values |
| 4     | Constraints          | Relationships          |
| 5     | Joins                | Traversal              |


# Graph Database Concepts & Terminology

| Term                | Meaning                                                                 | Example                                                                                                      |
|---------------------|-------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Node                | The fundamental data element in Neo4j that represents entities.         | A node representing a university: `(:University {name: 'Stanford University', location: 'California'})`.     |
| Relationship        | A connection between two nodes, showing how they relate to each other.  | A relationship representing a university offering a program: `(Stanford)-[:OFFERS]->(Computer Science Program)`. |
| Label               | A tag that groups nodes into categories.                                | A node with a label: `(:Department {name: 'Computer Science'})`.                                             |
| Property            | Key-value pairs that store data on nodes or relationships.              | A node with properties: `(:Course {name: 'Algorithms', credits: 4, course_type: 'required'})`.               |
| Graph               | A network structure consisting of nodes, relationships, and properties. | A university graph where nodes represent universities, departments, and courses, and relationships represent course offerings. |
| Cypher              | The query language used to interact with and manipulate data in Neo4j.  | A Cypher query to find courses in a department: `MATCH (d:Department)-[:OFFERS]->(c:Course) WHERE d.name = 'Computer Science' RETURN c.` |
| Index               | Data structures that improve query performance by allowing faster lookups. | An index on a node's property: `CREATE INDEX FOR (n:Student) ON (n.student_id)`.                             |
| Constraint          | Rules that ensure data integrity in the graph database.                 | A constraint to ensure unique values: `CREATE CONSTRAINT ON (u:University) ASSERT u.name IS UNIQUE`.         |
| Traversal           | The process of exploring nodes and relationships in a graph.            | Traversing a graph to find all courses offered by a department.                                              |
| Path                | A sequence of connected nodes and relationships.                        | A path example: `(University)-[:HAS_SCHOOL]->(School)-[:HAS_DEPARTMENT]->(Department)-[:OFFERS]->(Course)`.  |
| Subgraph            | A subset of the overall graph, containing a specific selection of nodes and relationships. | A subgraph representing all courses offered by the School of Engineering.                                    |
| Property Graph Model| The data model used by Neo4j, consisting of nodes, relationships, properties, and labels. | The structure that represents universities, schools, departments, and their connections.                     |
| Schema              | The constraints and indexes defined on the graph to maintain data integrity and improve performance. | Indexes and unique constraints on properties like university names.                                          |
| Relationship Type   | The type of connection between two nodes, which defines the nature of their relationship. | `[:HAS_SCHOOL]`, `[:HAS_DEPARTMENT]`, `[:OFFERS]`.                                                           |
| Directionality      | Indicates the direction of a relationship between nodes.                | `(Stanford)-[:HAS_SCHOOL]->(School of Engineering)` vs `(School of Engineering)<-[:HAS_SCHOOL]-(Stanford)`.  |
| Supernode           | A node with a very large number of relationships.                       | A node representing a university with thousands of students enrolled.                                        |
| Graph Database      | A database that uses graph structures to store and query data.          | Neo4j is a graph database that stores entities like universities, programs, and courses as nodes with relationships. |
| ACID Compliance     | Ensures atomicity, consistency, isolation, and durability in database transactions. | Neo4j supports ACID transactions, ensuring data integrity for operations like student enrollment.            |