type User {
  fullName: String
  nickname: String
  name: String @deprecated(reason: "Use `fullName`.")
}

----

# Operation
{
  hero {
    name
    appearsIn
  }
}


# Response
{
  "data": {
    "hero": {
      "name": "R2-D2",
      "appearsIn": [
        "NEWHOPE",
        "EMPIRE",
        "JEDI"
      ]
    }
  }
}


# Object types and fields


schema and object types -- the most basic components of a GraphQL --> which just represent a kind of object you can fetch from your service ++ the fields it has. 

type Character {
  name: String!
  appearsIn: [Episode!]!
}

* Character -- GraphQL Object Type --- it is a type with some fields. Most of the types in my schema will be object types.
* `name` and `appearsIn` are fields on the Character type. That means that name and appearsIn are the only fields that can appear in any part of a GraphQL query that operates on the Character type.
* String -- a built-in scalar type -- type that resolve to a single scalar object, and can't have sub-selections in the query. 
* String! -- meaning the field is non-nullable -- GraphQL service promises to always give you a value when you query this fied. In the type language --- we represent those with an exclamation mark.
* [Episode!]! represents an array of Episode objects. Since it is also non-nullable, you can always expect an array (with zero or more items) when you query the appearsIn field. And since Episode! is also non-nullable, you can always expect every item of the array to be an Episode object.


# Arguments

type Starship {
  id: ID!
  name: String!
  length(unit: LengthUnit = METER): Float
}


