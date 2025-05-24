Both deadlock and livelock are concurrency issues in multi-threaded or distributed systems, but they have important differences:

## Deadlock

A **deadlock** occurs when two or more processes are blocked forever, each waiting for resources held by another process. It's a complete standstill where:

- Each process holds a resource while waiting for another
- None of the processes can proceed or release their resources
- The system effectively freezes

**Example:** Two threads each holding a lock while trying to acquire the other's lock:

- Thread A holds lock 1 and waits for lock 2
- Thread B holds lock 2 and waits for lock 1
- Neither can proceed, creating a permanent blockage

## Livelock

A **livelock** occurs when processes are actively changing state but making no progress. Unlike deadlock where processes are completely blocked, in livelock:

- Processes respond to each other
- They continuously change their states
- Despite activity, no meaningful progress occurs

**Example:** Two people meeting in a hallway who keep moving side to side in sync, each trying to let the other pass but inadvertently blocking each other.

## Key Differences

|Aspect|Deadlock|Livelock|
|---|---|---|
|Activity|Processes are blocked/waiting|Processes are actively running|
|Resource state|Resources remain held|Resources may be acquired and released|
|Detection|Often easier to detect|More difficult to detect due to activity|
|System state|Static, frozen|Dynamic, changing but not progressing|

Livelocks are sometimes described as a more subtle, "busy" form of deadlock where the system appears active but is still unable to make progress.