+++
title = "Queries"
date =  2017-09-08T02:04:05-04:00
weight = 6
+++

Still using the USer model as an example

## Simple (By-Equality) queries

Finds
`await jollof.models.User.findBy({firstName: 'foo', lastName: 'bar'})`
`await jollof.models.User.findOneBy({firstName: 'foo', lastName: 'bar'})`

Counts
`await jollof.models.User.countBy({firstName: 'foo', lastName: 'bar'})`

Updates
`await jollof.models.User.updateBy({id: '...'}, newValues)`

Remove
`await jollof.models.User.removeBy({id: '...'})`

## JFQL queries
JFQL is the data language of JollofJS.

It is a simple language that consists of arrays, where each condition in the array is ANDED.

Each condition follows the convention `[FIELD_NAME, COMPARATOR, VALUE ]`.
You can also explicitly define AND or OR conditions by wrapping the condition groups in {and: conditions} or {or: conditions}

```
const date1 = new Date('...');
const date2 = new Date('...');

const query= [
    [ 'firstName', '=', 'Patrick' ],
    [ 'lastName', '=', 'Squid' ],
    {
     or:[
        [ 'dateCreated', '<=', date1],
        [ 'dateCreated', '>=', date2]
    ]}

]
```

You can use this right in the admin backend as well to explore your app's data. (skip `const query=`)

### JFQL comparators
These are the supported comparators for JFQL.

=
!=
>
>=
<
>=

## Native queries
See the Models section on Native functions.