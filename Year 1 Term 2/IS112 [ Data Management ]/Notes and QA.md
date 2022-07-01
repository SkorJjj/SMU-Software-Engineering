
# Table of Contents

- [Entity Relationship Model](#entity-relationship-model)
  - [Entity Relationship Notation](#entity-relationship-notation)
    - [Entity Types](#entity-types)
    - [Attributes Notation](#attributes-notation)
    - [Identifiers](#identifiers)
      - [Characteristics of Identifiers](#characteristics-of-identifiers)
    - [Relationship Notations](#relationship-notations)
      - [Relationship Degrees](#relationship-degrees)
      - [Relationship Cardinality [```Crow Foot Notation```]](#relationship-cardinality-crow-foot-notation)

# Entity Relationship Model
## Entity Relationship Notation
### Entity Types
| Type |      Name     |  Description |
|:----------:|:-------------:|:------:|
| ![image](https://user-images.githubusercontent.com/64523806/176378614-186c2387-5f13-4f43-8efc-07cb6198aa7f.png)|  Strong | A strong entity is not dependent on any other entity in the schema. A strong entity will always have a primary key |
| ![image](https://user-images.githubusercontent.com/64523806/176378669-3053f87c-8d7e-44e0-8743-cea58b7a06ef.png)|    Weak   |   A weak entity is dependent on a strong entity to ensure its existence. Unlike a strong entity, a weak entity does not have any primary key. It instead has a partial discriminator key. |
| ![image](https://user-images.githubusercontent.com/64523806/176378710-178cbd32-dedb-4448-a0a1-636e95438104.png) | Associated |   Associative entities relate the instances of several entity types. They also contain attributes specific to the relationship between those entity instances.|

### Attributes Notation 
![image](https://user-images.githubusercontent.com/64523806/176381593-7107f4c7-a2f0-4609-8b2f-d324401302ec.png)

| Name   |     Example    |  Description |
|----------|:-------------:|------|
| Composite |  ![image](https://user-images.githubusercontent.com/64523806/176382799-450eb604-5777-4044-ab2d-f5fe0be04641.png)| A composite attribute is an attribute that has been broken into different components. Use parentheses (“””) to store composite attributes. The different values inside a composite attribute is known as component attributes. For component attributes, use (). |
| Multivalued |   NIL |   Denoted via {}. Implies multiple values associated with an attribute. |
| Derived | ```[Years Employed]``` derived from  <br>   ```Date Employed``` |    Denoted via []. Implies attribute that is derived from another column. |

### Identifiers
|Type| Definiton|
|--------|------|
|Simple Identifier|Single Attribute|
|Composite Identifier| Made up of multiple attributes. Does not have to be a composite attribute|
#### Characteristics of Identifiers
1. Will not change in value
2. Will not be null: every instance must have a value for the identifier

### Relationship Notations

 #### Relationship Degrees
 1. Unary 
 2. Binary
 3. Ternary
 
 #### Relationship Cardinality [```Crow Foot Notation```]
 |Type| Meaning|
 |-----|-----|
 |![image](https://user-images.githubusercontent.com/64523806/176576975-dc6dbbe2-e403-4600-aca4-1219ab4bc5aa.png) |Mandatory One|
 |![image](https://user-images.githubusercontent.com/64523806/176577013-06e39fe1-9dbb-42a2-a3cf-cea4c1d2bde2.png) |Mandatory Many|
 |![image](https://user-images.githubusercontent.com/64523806/176577041-7026b55f-0e87-44d4-afeb-b591d9951123.png) |Optional One|
 |![image](https://user-images.githubusercontent.com/64523806/176577070-cb33f6e8-ba8d-43fe-8d90-34f80e8ba918.png) |Optional Many|
 
# SQL Queries Tips and Tricks

### How to remember JOIN statements.

See ``` JOIN ``` as which table/relation's column can be returned ```NULL```.  
```(INNER) JOIN``` : Returns records that have matching values in both tables. Nothing can be ```NULL```.  
```LEFT (OUTER) JOIN```: Returns all records from the left table, and the matched records from the right table. Right records can be ```NULL```.  
```RIGHT (OUTER) JOIN```: Returns all records from the right table, and the matched records from the left table. Left records can be ```NULL```.  
```FULL (OUTER) JOIN```: Returns all records when there is a match in either left or right table. Anything can be ```NULL```.  
