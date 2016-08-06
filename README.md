# .NET-File-Logger-Synced
Machine wide synced, non blocking file logger

    // The goal of this class:
    // Provide a way of logging which works from many concurrent threads AND PROCESSES (like IIS workers)

    // How to use:
    // 1. Rename m_sMutexName to something works for you code ("Global\" has to stay at the beginning!)
    // 2. Instantiate this calls preferrebly ONCE on the process level (you can create more, it should work fine but will waste threads and resources)
    // 3. Call the QueueLogToFile function in this class with FULL PATH and LogMsg string
    // 4. This class queues the request and writes out the logs after iMaxQCountBeforeForcedWrite in queue or iMaxSecondsBeforeForcedWrite or blForced is set

    // Known limitations:
    // Sync is done by the logging MUTEX name. Not by filename! (looks good enough for my usage)
    // File writes are organized in FIFO order not by file (could cause performance increase but would make the code more complex and hence this is an error logger that is bad IMHO, possible future improvement)
