# HTB - Redeemer

- Platform: HackTheBox - StartingPoint
- OS: Kali Linux
- Difficulty: Very Easy
- Date: 25.11.2026

## Recon

Started with a TCP port scan using Nmap:

`nmap -sT <TARGET_IP> -p- -T5`

The scan revealed one open TCP port:

- `6379`/tcp open redis

## Enumeration

Connected to the Redis service using `redis-cli`:

`redis-cli -h <TARGET_IP> -p 6379`

Used the `INFO` command to gather server information and identified Redis version `5.0.7`.

The Keyspace section showed 4 keys in the database.

## Exploitation

Redis was accessible without authentication.

Used `KEYS *` to enumerate available keys and discovered a key named `flag`.

Retrieved its value using:

`GET flag`

Successfully obtained the flag.

## Key Takeaways

- Learned basic Redis enumeration.
- Practiced connecting to a Redis service using `redis-cli`.
- Learned how to retrieve stored values from Redis.
