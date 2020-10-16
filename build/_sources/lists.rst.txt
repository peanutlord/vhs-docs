.. .Listen:

Listen
------

Eine Liste ist eine (veränderbare) Sequenz, die typischerweise eine Sammlung von homogenen Daten beinhaltet:

.. code-block:: python
   :caption: Liste erzeugen

    lst = []

    # Alternative, but slower (yet sometimes required ;) ):
    lst = list()

    # Create a list with data already inside
    lst = [1, 2, 3]

    # You can freely chose your types, but it's not recommended
    lst = [1, 2, "Hello VHS!", 3, "Whats up?", 2.0]

    # List's are in the order you insert the values! They will not change
    lst = [1, 2, 5, 4, 3, 9, 7]
    print(lst)

Einzelne Elemente in einer Liste können über ihren Schlüssel ausgewählt werden. Dieser Schlüssel ist auch sequenziell, beginnend bei der ``0``:

.. code-block:: python
   :caption: Einzelne Elemente aus der Liste auswählen

    lst = ["Hello", "class", "how", "are", "you?"]
    print(lst[0])  # Hello
    print(lst[1])  # class
    # ...

Einem Schlüssel kann auch ein neuer Wert zugewiesen werden:

.. code-block:: python
   :caption: Einzelne Elemente aus der Liste überschreiben

    lst = ["Hello", "class", "how", "are", "you?"]
    lst[1] = "Robert"
    print(lst)

Listen können auch nach der Erzeugung erweitert oder sortiert werden:

.. code-block:: python
   :caption: List erweitern

    lst = [1, 2, 3]
    lst.append(4)
    lst.append(5)

    print(lst)  # [1, 2, 3, 4, 5]

    # We can also extend a list with another one
    lst.extend([6, 7, 8])

.. code-block:: python
   :caption: List sortieren

    lst = [1, 2, 5, 4, 3, 9, 7, 6, 8]
    lst.sort()

    print(lst)  # [1, 2, 3, 4, 5, 6, 7, 8, 9]

**Hinweis**: Die Befehle ``append``, ``extend`` und ``sort`` **mutieren** die Liste, d.h. sie verändert ihren Zustand (engl. mutable).

Um eine Liste zu kopieren, gibt es zwei Möglichkeiten:

.. code-block:: python
   :caption: List kopieren

    lst = [1, 2, 3]
    lst2 = lst.copy()

    # Alternative
    lst2 = lst[:]  # Note: odd syntax, we'll soon find out what it is


.. Let's see if we use this!
.. **Hinweis**: Dies hier ist **kein** kopieren, es erzeugt nur eine s.g. Referenz:

    .. code-block:: python
       :caption: List Referenz

        lst = [1, 2, 3]
        lst2 = lst

        lst.append(4)

        print(lst)  # [1, 2, 3, 4]
        print(lst2)  # [1, 2, 3, 4]

Python besitzt die Möglichkeit, Listen zu schneiden (engl. slicen). Damit können subsets von Listen erstellt werden, Elemente ersetzt oder gar ganz entfernt werden. Es wird jedes Mal eine neue Liste zurückgeliefert.

.. code-block:: python
   :caption: List subset

    lst = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    subset = lst[0:3]
    print(subset)  # [1, 2, 3]

    # We can also add the steps as third parameter:
    another_subset = lst[::2]  # Take every second item
    print(another_subset)  # [1, 3, 5, 7, 9]

    # Elemente entfernen
    letters = ["a", "b", "c", "d", "e", "f", "g"]
    letters[2:5] = []
    print(letters)  # ['a', 'b', 'f', 'g']

Um die Länger einer Liste herauszufinden, können wir einfach ``len`` benutzen:

.. code-block:: python
   :caption: List subset

    lst = [1, 2, 3]
    length = len(lst)
    print(length)  # 3

Wir können auch sehr einfach die Summe einer Liste kriegen (vorrausgesetzt, sie besteht nur aus ``int``s)

.. code-block:: python
   :caption: Sum

   lst = [1, 2, 3, 4, 5]
   print(sum(lst))

**Hinweis** Wir hatten bereits von "Zeichenketten" gesprochen. Diese sind eine Liste von Zeichen und verhalten sich auch manchmal so (``len`` ist benutzbar, können gesliced werden und durch Schleifen verarbeitet)

.. code-block:: python
   :caption: List subset

    something = "Hello World"
    print(something[:5])  # "Hello"

    length = len(something)
    print(length)

    # IMPORTANT! Strings are immutable, we cannot reassign keys!
    something[0] = "h"

    # TypeError: 'str' object does not support item assignment