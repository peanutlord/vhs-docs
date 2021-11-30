.. _Defining Functions:

Funktionen
==========

Aufbau
------

    Don't repeat yourself (DRY)

Wie in einem guten Buch, sollte die gewünschte Information genau einmal auftauchen und nicht x Mal an x Stellen (gilt auch für Romane).
Besonders in der Programmierung ist das Wichtig. Wenn ich das Verhalten der Software ändern möchte, sollte ich genau einen Ort
anpassen müssen und nicht viele verschiedene Stellen.

.. code-block:: python

    def do_something():
        print("I was called")

    do_something()

Funktionen können natürlich beliebig oft gerufen werden:

.. code-block:: python

    do_something()
    do_something()
    do_something()

Funktionen können auch Ergebnisse an den Aufrufer zurückliefern. Diese können in Variablen gespeichert werden oder direkt an andere Funktionen weitergereicht werden, wie zum Bsp. ``print``

.. code-block:: python

    def do_something():
        return "Hoooray! I did something"

    something = do_something()
    print(something)

    # Or...
    print(do_something())

Funktionen können auch von außen s.g. "Argumente" erhalten um ihre Arbeit zu verrichten. Wir haben bereits solche Funktionen kennengelernt (zum Bsp. ``range``).
Normalerweise müssen Argumente in der Reihenfolge hineingegeben werden, wie diese aufgelistet sind:

.. code-block:: python

    def add(a, b):
        return a + b

    result = add(10, 10)
    print(result)

Aber auch hier gibt es die berühmte Ausnahme. Durch Angabe des Namens können wir Argumente in beliebiger Reihenfolge einsetzen:

.. code-block:: python

    add(b=10, a=2)

Funktionen können auch Variablen, die sich außerhalb befinden, "sehen" (Stichwort: Scoping). Wir können diese aber nicht (ohne Umwege) verändern.

.. code-block:: python

    EXP = 2
    def exp(a):
        return a ** EXP

    print(exp(2))
    print(exp(4))

Wir können die Argumente einer Funktion auch bereits mit Standardwerten belegen, die wir dann nicht immer übergeben müssen:

.. code-block:: python

    def power(base, exp = 2):
        return base ** exp

    print(power(4))
    print(power(4, 4))

.. code-block:: python

    def ask_ok(prompt, retries=4, reminder="Please try again"):
        while True:
            ok = input(prompt)
            if ok in ("y", "yes", "yes", "ok"):
                return True
            if ok in ("n", "no", "nop", "nope", "not ok")
                return False
            retries = retries - 1
            if retries < 0:
                raise ValueError("Retries exhausted")

            print(reminder)

Ein ``return`` beendet **immer** eine Funktion, egal an welcher Stelle (auch innerhalb von Endlosschleifen)

Wir können unseren Währungsrechner so umschreiben, dass verschiedene Währungen unterstützt mithilfe eines dictionaries (``dict``):

.. code-block:: python

    # Python dictionary, represented by key --> value
    currencies = {
        "BGN": 1.95583,
        "US": 1.18478,
        "YEN": 123.72
    }

    def exchange(currency, amount):
        if currency not in currencies:
            # raise ValueError(f"Unknown currency {currency}")
            return 0

        quote = currencies[currency]
        return quote * amount

    print(exchange("US", 100))
    print(exchange("BGN", 100))
    print(exchange("YEN", 100))

Funktionen können auch sich selbst aufrufen (rekursiver aufruf):

.. code-block:: python

    def fib(n):
        if n <= 1:
            return n
        else:
            return fib(n-1) + fib(n-2)

    for i in range(10):
        print(fib(i))

    # 0
    # 1
    # 1
    # 2
    # 3
    # 5
    # 8
    # 13
    # 21
    # 34

Packing und Unpacking
---------------------

Argumente müssen in der gleichen Anzahl und (wenn nicht der ``name`` benutzt wird) in der gleichen Reihenfolge angegeben werden.
Es existieren jedoch Situationen, in denen ich dem Benutzer einer Funktion erlauben will, unendlich viele Argumente zu übergeben:

.. code-block:: python

    def add_all(*nums):
        return sum(nums)

    add_all(1, 2, 3, 4, 5, 6, 7, 8, 9)

Man kann dies auch mit normalen Argumenten kombinieren:

.. code-block:: python

    def write_all(file, sep="\n", *lines):
        with open(file, "w") as f:
            f.write(sep.join(lines))

    write_all("foo.txt", "\n", "foo", "bar", "baz")

Die gleiche funktionalität gibt es mit Keyword Argumenten (Angabe des Namens + Wert):

.. code-block:: python

    def something(arg, **kwargs):
        print(kwargs)

    do_something("something", foo=bar, phrase="Hello World")

Oft findet man dieses Muster in Python code:

.. code-block:: python

    def something(a, b, *args, **kwargs):
        pass

Das ganze funktioniert auch in die "andere Richtung":

.. code-block:: python

    for i in range(0, 10):
        print(i)

    args = [0, 10]
    for i in range(*args):
        print(i)