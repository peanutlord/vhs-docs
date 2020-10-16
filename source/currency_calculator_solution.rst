.. Currency Calculator Solution:

Währungsrechner Lösung
======================

.. code-block:: python

    quote = 1.95583
    euro = int(input("How much Euro do you want to exchange? "))

    # There are more elegant ways to format a string, please ask if you want to find out! :)
    print(euro, "€ are", euro * quote, "BGN")
