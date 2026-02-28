# Python Context Managers — Meer Dan Alleen Bestanden Openen

*25 februari 2026*

De meeste Python-developers leren context managers kennen via `with open(...)`. Maar het is een van de meest elegante patronen in de taal, en het verdient een nadere blik.

## De basis

Een context manager is elk object dat `__enter__` en `__exit__` implementeert. Het `with`-statement roept deze automatisch aan:

```python
with open("data.txt") as f:
    content = f.read()
# bestand is hier gesloten, zelfs als er een exception optrad
```

## Je eigen context manager schrijven

De eenvoudigste aanpak is de `contextlib.contextmanager` decorator:

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

Gebruik:

```python
with timer("database query"):
    results = db.execute("SELECT * FROM users")
```

## Een praktisch voorbeeld: database-transacties

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

Dit patroon garandeert dat elke transactie ofwel commit ofwel rollback doet — geen tussenstatus mogelijk.

## Waarom dit ertoe doet

Context managers leggen een contract vast: *setup gebeurt, jouw code draait, opruimen is gegarandeerd*. Het is het soort betrouwbaarheid dat je ingebakken wilt hebben in je codebase, niet overgelaten aan discipline.

De beste abstracties besparen niet alleen toetsaanslagen — ze maken hele categorieën bugs onmogelijk.
