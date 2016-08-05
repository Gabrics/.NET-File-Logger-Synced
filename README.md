# .NET-File-Logger-Synced
Machine wide synced file logger

    // The goal of this class:
    // Provide a way of logging which works from many concurrent threads AND PROCESSES (like IIS workers)
    // How to use:
    // 1. Instantiate this calls preferrebly ONCE process level
    // 2. Call the QueueLogToFile function in this class with FULL PATH and LogMsg string
    // 3. This class queues the request and writes out the logs after iMaxQCountBeforeForcedWrite in queue 
    //    or iMaxSecondsBeforeForcedWrite 
    // Known limitations:
    // Sync is done by the logging MUTEX name. Not by filename! (looks good enough for my usage)
