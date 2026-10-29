## Correctness checklist

Look for logic errors and wrong conditions, off-by-one mistakes, null and undefined handling, thrown errors and rejected promises that nothing handles, missing cancellation or timeouts, race conditions, resources that are not cleaned up on every path, broken state transitions, and behavior that does not match the request, the spec or the documented contract.

Judge each change with its surrounding code and its callers, not the diff alone. Only flag a bug you can explain with a concrete input or sequence that triggers it. A missing test alone is not proof of a bug.
