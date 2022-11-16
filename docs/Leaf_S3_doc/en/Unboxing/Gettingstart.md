# Hello World

We can start by outputting a "Hello World" text as the first step in understanding and learning MicroPython.

> The operations described in this article are based on Thonny IDE. You need to complete the configuration of Thonny IDE and establish a connection with the development board. [The construction of the Thonny IDE runtime environment can be referred to here](../Programming/Environment.md).

## Using REPL

**REPL** is the abbreviation of **Read-Eval-Print-Loop**, which is translated as **read-evaluation-output-loop**.

We can understand what it means by practical operation.

Connect the development board with the MicroPython firmware installed to the computer, run the Thonny IDE and configure it correctly, the following text will appear in the Shell window:

````
MicroPython v1.17 on 2022-01-09; ESP32S3 module with ESP32S3
Type "help()" for more information.
>>>
````

Pay attention to the `>>>` prompt on the last line, we can directly enter the formula or code after this, and press the `enter` key on the keyboard to immediately get the output result on the next line.

````python
>>> 1+2
3
>>> print("Hello World")
Hello World
>>>
````

Now it can be understood intuitively, it will read the information we input, perform operation evaluation, output the result, and then wait for our subsequent input, looping this process all the time, which is also **REPL** and translated as ** The reason for the ** of the interactive interpreter is that we can directly interact with the hardware by entering the code. There is no need to perform the compilation process in the middle as in the traditional C language. The information we input is transmitted to the chip without being compiled. Well, this is an important feature of the Python language, and MicroPython perfectly inherits it.

If you just use the MicroPython REPL, many software with serial port information sending and receiving functions can be operated. If you are interested, you can try various serial port tools, which can give a deeper understanding of the meaning of "there is no intermediate execution of the compilation process".

> Regarding the application of REPL, you can refer to [MicroPython documentation: REPL](https://docs.micropython.org/en/latest/reference/repl.html) for more detailed and comprehensive content

## Code editor

Of course, Thonny IDE can not only perform REPL operations, but as a python code editor, it still has its own functions.

Create a new file and enter the code in its edit field.

````python
print(1+2)
print("Hello World")
````

After editing the code, click **Save**, you can choose to save the file to the MicroPython device, which will directly transfer the data of the entire file to the flash. The file can be named `main.py`, the device will execute the program with this file name after every power-on or reset, and the other file name is only called by `main.py` or we in Thonny Executed when **Run** is clicked.

![](../assets/images/Quick_Start.png)

Now click **Run**, also without compiling, you will get the result immediately in the Shell.

````
3
Hello World
````

In addition, you can also try the REPL keyboard control shortcut **ctrl+D** software reset, you can see that the program is executed immediately after the reset and the information is printed out.