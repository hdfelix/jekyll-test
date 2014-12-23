---
---

Why not to use Ruby
- Speed (image processing)
- scaling
- most Gems are not thread safe
  ...

Common alternatives
- Node, good for
  . Quick, Non blocking I/O
  . Concurrency
  . chat app sweet spot
  Bad for
    . vertical scaling
    . cpu intensive
    . integraiton with other systems (a lot of ducktape)
    . not a nice language like Ruby

- Vert.x
    . "Node for the JVM"
    . Like node
      . concurrency - reacotr pattern
      . fast
      Better than node
      . CPU Intensive, JVM fast, threads (single threading models, JVM thread friendly)
      . Blocking IO or CPU intensive
        . worker verticles
        . vertical per CPU
        . Polyglot
          . official support in many languages
    . Core APIs

Tim Fox Introducing Vert.x 2.0 (Vert.x videos)
THis ain't your Dad's node (second video)

Jubilee
. Rack server w/vert.x 2.0 built in
  . now a Vert.x module for imporved performance and interaction wtih the vert.x ecosysem
 
Things to read up on:
1. what are verticals?
2. What is Rack programming (Sinatra, ...)
3. Gems (that run on JRuby)
4. Look into Redis

what is 'rackup'?
"Serious rubyists use jruby" (for scaling purposes, good to switch to jruby)

Having the parts do the parts well
. Rails
  . login, haml views, migrations, gems
  . jubilee/vert.x
    . websockets/concurrency
    event bus for communication into browser
    share memory quick asset
    timer TBI
Opal?



INDEXES
- The second pillar od database wisdom

Guyren Howe (guyren@relevantlogic.com)

mysql slower & less reliable than most server apps

What everyone knows about indexes
  Trade insert/update/delete time for query time
  Trade storage space for query time
  (don't have indexes you are not using; have the fewest/most effective you can)

Nonsense about dbs
. index all join columns
. index for every field you search
. indexes should be rebuilt indexes
. Most selective first
. Dynamic SQL is slow
. Faster computers execute queries faster

interactive latency (http://www.eecs.berkeley.edu/~rcs/research/interactive_latency.html)

SSDs work fast, but will fail unexpectedly in a short amount of time

Your DB is never fast enough

Queries - instructions to construct a program
  . balances random vs sequential I/O, CPU use, mermoy use, optimization is np hard

  AND queries most common in apps
  OR clause can usually be considred s combining the results of two or more AND queries
  Complex to give general advise

  BTree type indexes
  Phone Book Theory of Indexing
    Single index
    Comprehensive index (sorted by how often soemthing is searched)
    1. Prefer compound indexes over single indexes (it's a bit slower)
    2. Prefer selective predicates
    3. Consider a covering index
    4. Be subtle with compund index predicates
      . put covering fields you don't search on at the end
      . PUt a field to do range seraches on next
      . Put other fields you search on at the front in order of use and selectivity
      . Unless you're ealign with iff. serahes, may want to use multiple compunds indexes
    5. partial index
    6. Functional index
    Sorting
      . Need same predicates WHERE and ORDER BY
      . Index can be usd in either dirction but not both

  Partial Results: Limit n or FETCH FIRST n
  Need pipeline ORDER BY
  Paginating
  Clustering (Postgres)
    . based on existing index
    . Physically reorganize the heap in indsx order
    . Reduce seek time for blocks of records
    . On-off procedure; noew records not clustered
    . locks table for duration
  Use case:partitioning
    . use Postgres table inheritance
    . split table into numerous identical subtables (for a lot of data)

  JOINS
  (learn to use 'explain')
    3 Join Methods
      . Nested loop
        . Query 1 table; loop and query the other 
      . Hash Join
        . Avoid nested loop cost by making hash of one side
        . (don't do index joins when using this; waste of time)
        . Keep hash table as small as possible
        . Not for range joins; only equality
      . Merge Join
        . Query each talbe, sort
        . Useful for outer joins, indexes on multiple tables
        . less often used  sort is expensive

    Index data structures: BTree and hashes
      . BTree
        . Normal index type
        . equality and range seaches
      . Hash
        . faster for equality
        . (test though)
      . GIST (Postgres)
        . Variety of data types with comples operators eg spatial contains/ner/etc
        . hstore
      . SP_GIEST
        . Similar to GIST but beter for soem data types
      . GIN
        . more or less IGEST
        . 3x more space and 3x slower insert gives faster 3x search
     Dynamic SQL (Not in MySQL or Postgres)
      . Prepared statement or bind queries lets server cache query plan
      . SQL Server or Oracle
      . wave query plan time
      . Usually saves time but doesn't consider values
      . Uneven distributions suffer

    Statistics
 LEARN a rails web evelopment bootcamp (San Diego)

Postgres - HSTORE (no need for NoSQL)
9.4 will have JSON support

eager loading: n+1 problem
  . look at logs and learn to use explain to see what Rails is using
    . Based on this, design your indexing strategy

SDRuby
