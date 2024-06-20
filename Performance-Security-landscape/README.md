# Scalabilty

ความสามารถในการขยายขนาด

1) Vertical scaling: adding more power to one single machine like adding more disc space to hold more memory.
`cons`: there's a limitation of how much powerful a single machine can be.

2) Horizontal scaling: adding more database and make all of them work as a single database
`cons`: is the more machine you add to a system the more complexity it adds.

# Sharding

The idea: splitting data into different machines and have a system of a routing system(we usually need to implement) that knows where each of the data located
![Sharding](Sharding.png)

# Replication

What happens if our machine that store user's data somehow breaks.

So we should replicate database and not just save in the same warehouse but save it somewhere else

There's two big strategies when it comes to replication

1) synchronous: when client make an update to database, the database isn't go to repsond to client until those changes are confirmed in all of other database.

Ensures real-time consistency between primary and secondary storage at the cost of higher latency and potential performance impact.

cons: slow

2) asynchronous: when client make an update to database. database will send message immediately and in the background it will update all of other database

Offers lower latency and better performance but with a trade-off in consistency, as there is a potential lag between the primary and replica data.

cons: If there's an error, we have just told our clinet is successfull so there's will issues occurs.

# Backups

Just like the name suggest backup all of data and store it somewhere else but the cost is very expensive


# Distributed v.s. Centralized databases

Distributed: กระจาย
Centralized: รวมศูนย์

`Centralized databases` is a database that kept in a single location on a given network or a database that are controlled by one organizations.

`Distributed databases` is a composed of multiple of database stored in multiple physical location but it can also mean databases that are controlled by different organizations.


Database can be centralized by your organization but distributed around the world

# Security

common security pratices:

    1) user can see only data that they authorized(สิทธ์การเข้าถึง) to see.

    2) prevent data corruption: make sure our database in safe location from outsied forces like weather and also technical glitches.