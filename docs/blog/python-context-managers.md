# Python Context Managers — More Than Just File Handling

*February 25, 2026*

Most Python developers meet context managers through `with open(...)`. But they're one of the most elegant patterns in the language, and they deserve a closer look.

## The basics

A context manager is any object that implements `__enter__` and `__exit__`. The `with` statement calls these automatically:

```python
with open("data.txt") as f:
    content = f.read()
# file is closed here, even if an exception occurred
```

## Writing your own

The simplest approach is the `contextlib.contextmanager` decorator:

```python
from contextlib import contextmanager
import time

@contextmanager
def timer(label: str):
    start = time.perf_counter()
    try:
        yield
    finally:
        elapsed = time.perf_counter() - start
        print(f"{label}: {elapsed:.4f}s")
```

Usage:

```python
with timer("database query"):
    results = db.execute("SELECT * FROM users")
```

## A practical example: database transactions

```python
@contextmanager
def transaction(connection):
    cursor = connection.cursor()
    try:
        yield cursor
        connection.commit()
    except Exception:
        connection.rollback()
        raise
    finally:
        cursor.close()
```

This pattern guarantees that every transaction either commits or rolls back — no in-between state.

## Why this matters

Context managers encode a contract: *setup happens, your code runs, cleanup is guaranteed*. It's the kind of reliability you want baked into your codebase, not left to discipline.

The best abstractions don't just save keystrokes — they make entire categories of bugs impossible.
