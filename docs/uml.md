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
    rectangle "User profile" as prof
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
