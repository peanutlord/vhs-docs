.. _Data Types:

Datentypen
==========

Pythons Typesystem nennt sich "Duck Typing":

  “When I see a bird that walks like a duck and swims like a duck and quacks like a duck, I call that bird a duck.”

  „Wenn ich einen Vogel sehe, der wie eine Ente läuft, wie eine Ente schwimmt und wie eine Ente schnattert, dann nenne ich diesen Vogel eine Ente.“

  --  James Whitcomb Rileys

Wenn ich das erste Mal eine Variable einen Wert zuweise, erhält sie diesen Typen:

.. code-block:: python

  >>> a = 5
  >>> type(a)
  <class 'int'>
  >>> something = "Hello World"
  >>> type(something)
  <class 'str'>

Folgende primitive Datentypen existieren in Python:

+-------------------------+---------------------------------------------------------+
| Datentyp                | Mögliche Werte                                          |
+=========================+=========================================================+
+-------------------------+---------------------------------------------------------+
| NoneType                | None                                                    |
+-------------------------+---------------------------------------------------------+
| Integer (Ganze Zahl)    | -2147483648 bis 2147483647                              |
+-------------------------+---------------------------------------------------------+
| Float (Gleitkomma)      | 250738585072014e-308 1.7976931348623157e+308            |
+-------------------------+---------------------------------------------------------+
| String (Zeichenkette)   | "Hello World", "12345"                                  |
+-------------------------+---------------------------------------------------------+
| Boolean                 | True, False                                             |
+-------------------------+---------------------------------------------------------+

Es besteht die Möglichkeit einen Typen in einen anderen zu verwandeln (engl. casting):

.. code-block:: python

  >>> a_str = "5"
  >>> a_int = int(a_str)
  >>> type(a_int)
  <class 'int'>
  >>> print(a_int)
  5

.. code-block:: python

  >>> truthy = True
  >>> a_int = int(truthy)
  >>> type(a_int)
  <class 'int'>
  >>> print(a_int)
  1

**Hinweis** Nicht jeder Typ ist mit jedem kompatibel. Ich kann einen String mit ``"Hello World"`` nicht (ohne Umwege) in eine Ganzzahl verwandeln:

.. code-block:: python

  >>> something = "Hello World"
  >>> int(something)
  Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
  ValueError: invalid literal for int() with base 10: 'Hello World'