.. _REPL:

Interaktiver Modus
==================

REPL starten
------------

Python benutzt einen Interaktiven Modus, auch "REPL" genannt:

* **R** ead (Lesen)
* **E** valuate (Evaluieren)
* **P** rint (Ausgeben)
* **L** oop (Schleife)

Dieser Modus eignet sich besonders um schnelle Dinge "auszuprobieren". Wir werden
ihn benutzen, um erste Konzepte auszuprobieren.

Dazu öffnen wir die Windows Konsole und tippen ``python``. Folgendes dürfte erscheinen:

.. code-block:: bash

  7tvmb293:~ christopher.marchfel$ python
  Python 3.8.1 (default, Mar 13 2020, 18:48:53)
  [Clang 11.0.0 (clang-1100.0.33.17)] on darwin
  Type "help", "copyright", "credits" or "license" for more information.
  >>>

Kommentare
----------

Kommentare sind Zeichen, die von Python ignoriert werden. Sie beginnen mit ``#`` und gelten ab dem Zeichen bis zur Ende der Zeile.

.. code-block:: python

  # I want to print something
  print("Hello World")

  print("How are you?")  # I will also be ignored!


Erste Rechnungen
----------------

Wir können die REPL sofort als Taschenrechner benutzen:

.. code-block:: python

  >>> 2 + 2
  4
  >>> 50 - 5*6
  20
  >>> (50 - 5*6) / 4
  5.0
  >>> 8 / 5
  1.6
  >>> 5 ** 2  # Potenz
  25
  >>> 25 % 5  # Modulo
  0

Variablen
---------

Die Ergebnisse werden einfach nur gedruckt. Wir können diese jedoch auch zwischenspeichern zur weiteren Verarbeitung. Dafür weisen wir den Wert einer s.g. Variable zu:

.. code-block:: python

  >>> some_number = 2 + 2
  >>> some_number
  4


.. code-block:: python

  >>> width = 20
  >>> height = 5 * 9
  >>> width * height
  900

Ist eine Variable nicht definiert (d.h. ihr wurde keinen Wert zugewiesen), erzeugt ihre Benutzung ein Fehler:

.. code-block:: python

  >>> n
  Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
  NameError: name 'n' is not defined


Zeichenketten
-------------

Zeichenketten sind eine Abfolge von Zeichen (engl. characters, chars).

.. code-block:: python

  >>> print("Hello World")
  'Hello World'
  >>> print('Hello World')  # Note '
  'Hello World'

Zeichenketten werden von ``"`` oder ``'`` eingeschlossen. Möchten wir diese Zeichen innerhalb einer Zeichenkette verwenden, müssen diese vorher escaped werden:

.. code-block:: python

  >>> print("Let's use a \" in our test")
  Let's use a " in our test
  >>> print("And Hamlet spoke \"To be, or not to be, that is the question\"")
  And Hamlet spoke "To be, or not to be, that is the question"

``\`` kann durch ``\\`` benutzt werden

.. code-block:: python

  >>> print("\\")
  '\'

Bestimmte escape Zeichen werden benutzt um die Darstellung des Textes zu beeinflussen. Hier ist eine unvollständige Auflistung:

* ``\'`` - escape ``'``
* ``\"`` - escape ``"``
* ``\\`` - escape ``\``
* ``\n`` - newline
* ``\r\n`` - newline carriage return (Windows)
* ``\t`` - tab
* ``\b`` - backspace
* ``\0`` - 0 terminator (C/C++)

Um einen Zeilenumbruch zu erzeugen, müssen wir das escape Zeichen ``\n`` benutzen:

.. code-block:: python

  >>> print("Hello\nWorld")
  Hello
  World

Um alle escape Zeichen zu "deaktivieren" kann in Python ein s.g. "Raw String" erzeugt werden. Dieser zeichnet sich durch ein ``r`` vor den ``"`` aus.
**Hinweis**: Die REPL benutzt Raw Strings, daher muss man ``print`` benutzen um die Wirkung der escape Zeichen zu sehen:

.. code-block:: python

  >>> print(r"Hello\nWorld")
  Hello\nWorld
  >>> "Hello\nWorld"
  Hello\nWorld
  >>> print("Hello\nWorld")
  Hello
  World

Ich kann mehrere ``\n`` sehr einfach durch einen s.g. Multiline String abbilden

.. code-block:: python

  >>> some_string = """
  ...   Hello,
  ...   I am a very long string with a lot of newlines.
  ...   Don't believe me?
  ...   What are you reading right now?
  ...   """
  >>> print(some_string)

    Hello,
    I am a very long string with a lot of newlines.
    Don't believe me?
    What are you reading right now?

**Hinweis** ``0`` und ``"0"`` sind **nicht** das Gleiche! Das erste ist eine Ganzzahl, das andere eine Zeichenkette bzw. String