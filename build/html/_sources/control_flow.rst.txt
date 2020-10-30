.. _Control Flow:

Kontrollfluss
=============

``if`` Statement
----------------

Einer der wichtigsten ``keywords`` zur Kontrolle des Programmflusses ist das ``if`` statement. Damit lässt sich der Code "branchen" (eine Verzweigung).

Ein ``if`` prüft eine "Aussage" auf deren Wahrheitsgehalt. Ist das Ergebnis "Wahr" (in Python ``True``), wird der Code ausgeführt:

.. code-block:: python
   :caption: Simple if

    n = 42
    if n == 42:
        print("You discovered the meaning of life!")

    # You discovered the meaning of life!

Man kann einen ``else`` Block hinzufügen, der nur ausgeführt wird, wenn die Aussage nicht zutrifft:

.. code-block:: python
   :caption: if/else

    n = 41
    if n == 42:
        print("You discovered the meaning of life!")
    else:
        print("Don't give up, you are close - I can feel it!")

    # You discovered the meaning of life!

Es gibt Szenarien, in denen man mehrere Aussagen überprüfen möchte. Dies kann man durch s.g. ``elif`` Blöcke realisieren (``else if``).
Der erste Block, dessen Auswertung ``True`` ergibt "gewinnt":

.. code-block:: python
   :caption: if/elif/else

    n = 10
    if n == 42:
        print("You discovered the meaning of life!")
    elif n == 41:
        print("Don't give up, you are close - I can feel it!")
    else:
        print("You are not ready yet, keep searching!")

    # You are not ready yet, keep searching!

Wir können auch überprüfen, ob eine Zahl kleiner oder größer ist (oder kleiner/größer gleich):

.. code-block:: python
   :caption: Bigger/Smaller

    import random

    n = random.randint(0, 20)
    if n > 10:
        print("Bigger than 10")
    elif n > 1:
        print("Bigger than 1, but smaller than 10")
    else:
        printf("Sorry, it's just a 1...")

Nicht nur Zahlen können verglichen werden, sondern auch Zeichenketten:

.. code-block:: python
   :caption: Compare strings

    something = "Hello World"
    if something == "Hello World":
        print("Yes, hello to you too!")

Taschenrechner
--------------

Programmieren wir zusammen einen kleinen Taschenrechner. Dieser soll zu jeder Zeit nur zwei Zahlen entgegen nehmen und diese addieren, subtrahieren, multiplizieren oder dividieren.

``for`` Schleife
----------------

Auf der letzten Seite haben wir das erste Mal Listen kennengelernt. Wir haben Elemente hinzugefügt, entfernt oder subsets erstellt. Wir können jedoch auch eine Liste "durchwandern" mithilfe einer Schleife:

.. code-block:: python
   :caption: for loops

    words = ["cat", "window", "python", "vhs"]
    for w in words:
        print(w, len(w))

    # cat 3
    # windows 6
    # python 3
    # vhs 3


Der Programmcode innerhalb des ``for`` blocks wird **nur** auf ein einzelnes Elemente angewendet. Wir können auch ohne große Mühe eine Liste an Zahlen in Python erzeugen (beginnend ab 0):

.. code-block:: python
   :caption: range

    for i in range(5):
        print(i)

    # 0
    # 1
    # 2
    # 3
    # 4

**Hinweis**: ``range`` "benimmt" sich wie eine Liste, ist jedoch keine. Alle Dinge, die sich in einer Schleife benutzen lassen (selbst wenn es keine Listen sind), nennt man ``iterable``.
Mehr dazu gerne auf Nachfrage.

Man kann sogar einen String in eine Schleife stecken:

.. code-block:: python
   :caption: String in a loop

    for c in "Hello World":
        print(c)

Um den Schlüssel (engl. key oder index) einer Liste zu erhalten, gibt es zwei Wege:

.. code-block:: python
   :caption: Index of list

    some_items = ["Where", "is", "the", "money", "Lebowski"]
    for i in len(some_items):
        print(i, some_items[i])

**Hinweis**: Diese Art, um an den Schlüssel zu kommen, ist nicht sehr "Pythonic". Es gibt elegantere Wege. Gerne mehr auf Nachfrage

**Hinweis**: Wenn man nur eine neue Liste erzeugen möchte, bietet sich eine s.g. List comprehension an. Gerne mehr auf Nachfrage.

FizzBuzz
--------

Schreiben wir ein kleines Programm namnes FizzBuzz. Dieses wird gerne in Vorstellungsgesprächen verwendet.

Wir generieren eine Liste mit ``n`` Zahlen und durchwandern diese.
Ist die Zahl gleichzeitig durch 5 und 3 teilbar, schreiben wir das Wort "FizzBuzz". Ist die Zahl nur durch 5 teilbar, schreiben wir "Fizz" und diese nur durch 3 teilbar,
schreiben wir "Buzz".

Bei einer Liste mit 20 Zahlen, dürfte die Ausgabe wieviel aussehen::

    FizzBuzz
    Buzz
    Fizz
    Buzz
    Buzz
    Fizz
    Buzz
    FizzBuzz
    Buzz

Open or Senior
--------------

Schreiben noch ein weiteres, kleines Programm. Diesmal Golf:

Wir haben eine Liste von Spielern. Je nach Alter und Handicap sind diese "Senior" oder "Open".
Ein Spieler oder eine Spielerin, die über 55 ist und ein Handicap größer als 7 hat, gilt als "Senior". Andere als "Open".

Eine Liste mit folgenden Elementen::

    [[18, 20],[45, 2],[61, 12],[37, 6],[21, 21],[78, 9]]

dürfte diese Ausgabe erzeugen::

    ['Open', 'Open', 'Senior', 'Open', 'Open', 'Senior']

Ran an die Tastatur!

Wahrheitstabelle
^^^^^^^^^^^^^^^^

+-------+-------+------------------+
| A     | B     | Ergebnis         |
+=======+=======+==================+
| True  | False | False            |
+-------+-------+------------------+
| False | True  | False            |
+-------+-------+------------------+
| False | False | False            |
+-------+-------+------------------+
| True  | True  | True             |
+-------+-------+------------------+

+-------+-------+------------------+
| A     | B     | Ergebnis         |
+=======+=======+==================+
| True  | False | True             |
+-------+-------+------------------+
| False | True  | True             |
+-------+-------+------------------+
| True  | True  | True             |
+-------+-------+------------------+
| False | False | False            |
+-------+-------+------------------+

``while`` Schleife
------------------

Neben der ``for`` Schleife, welches jedes Elemente einer Liste durchläuft, existiert in Python noch eine zweite Art von Schleife: die ``while``.
Der Unterschied besteht darin, dass ``while`` so lange "läuft" wie eine Aussage "Wahr" ist (Python ``True``):

.. code-block:: python

    while True:
        print("I am running endless! Please press CTRL+C to exit")

**Wichtig** Innerhalb einer Endlosschleife müssen wir (in 99.99% der Fälle) eine Bedinging einbauen, die die Schleife beendet.
Es gibt (wenige) Ausnahmen wo dies nicht der Fall ist, zum Bsp. in einem Betriebssystem. Dort befindet sich der untersten Ebene
eine Schleife, die sich nie beendet (``while True``).

.. code-block:: python

    n = 0
    while n < 10:
        print(n)
        n = n + 1

Leere Elemente gelten als ``False`` (``None``, ``""``, ``[]``):

.. code-block:: python

    items = ["red", "green", "blue"]
    while items:
        print(items.pop())


``break`` und ``continue``
--------------------------

Wir haben die Möglichkeit Schleifen noch etwas detaillierter zu steuern. Mit ``break`` brechen wir aus einer Schleife auf:

.. code-block:: python

   n = 0
   while True:
      print(n)
      n = n + 1

      if n >= 10:
         break

.. code-block:: python

   import time

   times = [
       1577865600,  # 01/01/2020 @ 8:00am (UTC)
       1592233440,  # 06/15/2020 @ 3:04pm (UTC)
       1608840000,  # 12/24/2020 @ 8:00pm (UTC)
       1609459199   # 12/31/2020 @ 11:59pm (UTC)
   ]

   current_timestamp = int(time.time())
   for timestamp in times:
       if timestamp > current_timestamp:
           current_timestamp = timestamp
           break

   print(current_timestamp)  # 1608840000

``continue`` ermöglicht uns sofort mit der nächsten Iteration zu beginnen:

.. code-block:: python

   for num in range(2, 100):
      if num % 2 == 0:
         print("Found an even number", num)
         continue

      print("Found an odd number", num)