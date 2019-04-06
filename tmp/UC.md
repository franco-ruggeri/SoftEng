```plantuml
left to right direction

actor Manager as m
actor Vendor as v

m --> (Sell capsules with credits)
m --> (Sell capsules with cash)
m --> (Sell credits)
m --> (Buy capsule boxes)
m --> (Show pending orders)
m --> (Show summary)
m --> (Confirm order reception)
(Send order) --> v

(Buy capsule boxes) .> (Send order) : include
```
