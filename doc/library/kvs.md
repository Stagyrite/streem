# Key-value store

There are hashtable objects that work as a database.

## Operations

### kvs() - instantiate a new key-value store

Returns a new object of type 'kvs'.

### put() - assign a value to a key

One can assign a particular value to a string key.

### get() - find a value by key

Retrieves a value that is found by a given key.

```ruby
db = kvs()
db.put("race", "goblin")
race = db.get("race")
print(race)
# Output: goblin
```

