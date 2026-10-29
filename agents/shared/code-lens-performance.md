## Performance checklist

Look for N+1 queries and queries missing an index or a limit, work repeated inside loops or on every render, effects and handlers that run too often, unbounded lists, caches, queues or listeners, subscriptions, timers and event listeners that are never disposed, large synchronous work that blocks the event loop, the main thread or a request path, streams without backpressure, unnecessary I/O, and heavy new dependencies pulled into a client bundle.

Judge cost by realistic data sizes for the product, not worst-case theory. Treat a leak (an undisposed subscription, listener, timer or growing collection) as serious even when its per-call cost is small. Do not suggest memoization or caching unless you can name the repeated work it removes; micro-optimizations are not findings.
