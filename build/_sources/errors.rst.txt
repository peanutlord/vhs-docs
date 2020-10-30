.. _On Errors:

Fehler
======

Jeder Fehler in Python ist einen s.g. ``Exception``:

.. code-block:: python

    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    NameError: name 'name' is not defined

Eine ``Exception`` kann gefangen werden und behandelt:

.. code-block:: python

    try:
        # something will go wrong here!
        print(name)
    except NameError:
        print("Can't find the variable you are looking for")

Wir können den Fehler auch in einer Variable speichern und uns genauer anschauen:

.. code-block:: python

    try:
        # something will go wrong here!
        print(name)
    except NameError as err:
        print("Can't find the variable you are looking for")
        print(err)

Ein ``except`` kann auch mehrere Fehler auf einmal "fangen"

.. code-block:: python

    try:
        # something will go wrong here!
        print(name)
    except (NameError, TypeError):
        pass

Ein ``try`` ... ``except`` kann auch einen optionalen ``else`` Block bekommen, der ausgeführt wird wenn der "unsichere"
keine ``Exception`` getriggert hat. Damit kann man sicheren von unsicheren Code visuell trennen:

.. code-block:: python

    try:
        f = open("some_file", "r")
    except OSError:
        print("Can't open the file!")
    else:
        print("We have", len(f.readlines()), "lines")
        f.close()

Wir können auch selbst ``Exception`` s werfen:

.. code-block:: python

    try:
        raise NameError("Something is off")
    except NameError:
        print("An exception flew by")
        raise  # Just keep on throwing

Als letztes können wir einem ``try`` ... ``except`` Block auch einem ``finally`` hinzufügen. Dieser Teil wird **immer**
ausgeführt, egal ob wir einen Fehler oder nicht hatten. Dies wird u.a. gerne für das Aufräumen von Resourcen benutzt:


.. code-block:: python

    try:
        raise NameError("Something is off")
    except NameError:
        print("An exception flew by")
    finally:
        print("I get executed either way!")
