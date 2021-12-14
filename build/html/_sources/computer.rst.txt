.. _The Computer:

Der Computer
============

* Eine Rechenanlage, die sequentiell Befehle abarbeitet
* Ein Betriebssystem hat mehrere "Schichten". Höhere Schichten sind weiter weg von der Hardware. Zur Kommunikation mit der Hardware müssen die Befehle also nach unten durchgereicht werden

  * Python arbeitet auf den höheren Schichten. Das erklärt auch warum es langsamer ist - es gibt mehr "handoffs" an andere

* Es gibt Hardwarenahe Sprachen, zum Bsp Assembly, und Hardwareferne Sprachen, wie C/C++, Rust, Java. Auch Python zählt zu letzerem


Beispiel für ein ``Hello World`` in ``ASM``

.. code-block:: nasm

  ; Befehl zum Assemblen: nasm -felf hello.s
  ;                  && ld -o hello hello.o
      section data
  hello db  "Hello World!",0xa
  len   equ $-hello

      section text
      global  _start
  _start:
      mov eax, 4 ; write(stdout, hello, len)
      mov ebx, 1
      mov ecx, hello
      mov edx, len
      int 80h

      mov eax, 1 ; exit(0)
      mov ebx, 0
      int 80h

Das Gleiche in Java

.. code-block:: java

  public class HelloWorld
  {
      public static void main(String[] args)
      {
          System.out.println("Hello World!");
      }
  }

Und in Python:

.. code-block:: python

  print("Hello World")