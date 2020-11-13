# UML test

## Original test

```plantuml
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: another authentication Response
```

## Architecture test

```plantuml
node node1
cloud cloud1
database DB1
database "new database"
```

## DDD test

```plantuml
card "Users bounded context" {
  storage "aggregate" as cardAR {
    rectangle "Credit card" as cc
    rectangle "Expiry date" as expDate

    cc -- expDate
  }
  storage "aggregate" as userProfAR {
    rectangle "User profile" as prof [[$dictionary#user]]
    rectangle "Password" as pw
    rectangle "Home address" as addr
    collections "Credit cards" as cards

    prof -- pw
    prof -- addr
    prof -- cards
  }

  cards -up-> cardAR
}
```

## DDD test with custom syntax

```plantuml
[[!include diagram/context.puml]]

$context("Users bounded context") {
  $aggregate() as cardAR {
    $entity("Credit card") as cc
    $entity("Expiry date") as expDate

    cc -- expDate
  }
  $aggregate() as userProfAR {
    $entity("User profile") as prof [[$dictionary#user]]
    $entity("Password") as pw
    $entity("Hash") as ha
    $entity("Home address") as addr
    $value_object("Home number") as number
    $entities("Credit cards") as cards

    prof -- pw
    pw -- ha
    prof -- addr
    addr -- number
    prof -- cards
  }
  $aggregate() as hashAR {
    $entity("Hash type") as ht
  }

  cards -up-> cc
  ha -up-> ht
}
```

## Single aggregate diagram

```plantuml
[[!include diagram/context.puml]]

$aggregate() as userProfAR {
  $entity("User profile") as prof [[$dictionary#user]]
  $entity("Password") as pw
  $entity("Hash") as ha
  $entity("Home address") as addr
  $value_object("Home number") as number
  $entities("Credit cards") as cards

  prof -- pw
  pw -- ha
  prof -- addr
  addr -- number
  prof -- cards
}
```
