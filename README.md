# VSD TCL Workshop

**TCL (Tool Command Language)** is a scripting language widely used in the VLSI industry to automate and control EDA (Electronic Design Automation) tools such as Synopsys Design Compiler, PrimeTime, Cadence Innovus, and Mentor QuestaSim. It is simple, extensible, and well-suited for embedding into software tools. Tcl is platform-independent and supports dynamic typing, making it easy to prototype and extend. In the VLSI flow, TCL scripts are used for tasks like synthesis, static timing analysis, floorplanning, place and route, and simulation — enabling users to automate tool commands, generate reports, apply constraints, streamline repetitive tasks and development of control scripts and testing frameworks.

TCL supports basic programming constructs like variables, conditionals, loops, procedures, and file I/O. Its main advantage lies in its ability to make EDA flows repeatable, customizable, and efficient, especially in large designs. Because most major tools support TCL as their command-line interface, it has become a standard for scripting and automation in VLSI design environments.

<details>

 <summary>Module 1: Introduction to TCL and VSDSYNTH Toolbox Usage</summary>

## Module 1: Introduction to TCL and VSDSYNTH Toolbox Usage

In this workshop, we are preforming a task that will build a user interface (TCL Box) that will take a csv file as an input and gives a timing datasheet as an output. We will learn each and every step involved in this process.

![Image](/assets/tclintro1.png)
![Image2](/assets/tclintro2.png)

In the top-down approach, our task is divided into many sub-tasks.

### Sub Task 1

Create a command (in our case, vsdsynth) and pass .csv files from UNIX shell to TCL script.

![Image3](/assets/tclintro3.png)

### Sub Task 2

Converting all inputs to format[1] and SDC format, then passing them to the synthesis tool 'Yosys'.

![Image4](/assets/tclintro4.png)

- Yosys tool cannot understand the csv file so we need to conbvert it into foramt[1].

![Image5](/assets/tclintro5.png)

- It is required to convert openMSP430_design_constraints.csv into the sdc format which can be passed to Yosys tool for synthesis.

![Image6](/assets/tclintro6.png)

- The converted sdc format looks as shown below.

![Image7](/assets/tclintro7.png)

### Sub Task 3

Convert format[1] and SDC to format[2] and pass them to the timing tool 'Opentimer'.

![Image8](/assets/tclintro8.png)

- You required this format[2] which can be understandable by Opentimer tool for STA.

### Sub Task 4

The final step is to generate an output report with the timing results.

![Image9](/assets/tclintro9.png)

### Sub Task 1 Create command and pass csv file from UNIX shell to TCL script

- When dealing with User Interface related feature, one should always care about all scenarios as shown.

![Image10](/assets/tclintro10.png)

Lets create a UNIX script **vsdsynth**.

1. To inform a Unix system that a file is a script, you can use a #! interpreter directive (also known as a shebang) at the beginning of the file and make the file executable.

- The shebang is a special line that tells the system which interpreter to use to execute the file. It consists of #! followed by the path to the interpreter. For example, #!/bin/bash specifies that the script should be interpreted by the bash shell.

- The system needs to recognize the file as an executable before it can run the script. You can use the chmod +x <script_file_name>, in our case **chmod -R 777 vsdsynth**, command to make the script file executable.

- After making the file executable, you can run it by typing ./<script_file_name>, in our case ./vsdsynth, in the terminal. This tells the system to execute the script using the interpreter specified in the shebang.

The command was created with the following instruction

First Scenario:

![Image11](/assets/tclintro11.png)

- Line 1: Used to indicating a UNIX script
- Lines 3-11: Used logo which gives brief info on what type of file is this and contact info.
- Line 13: Created a variable named "my_work_dir" and assign to it the absolute path of the current working directory.
- Lines 19-22: In this we are checking if user is provided a csv file as arguments with command vsdsynth. if not, then a info message is returned on the screen for the user.

![Image12](/assets/tclintro12.png)

Second and Third Scenarios:

![Image13](/assets/tclintro13.png)

- Line 24: When users passes a argument along with the command. Either it can be "-help" or .csv which does not exist. User will a get a Info in return on the screen.
- Line 25: Validates if user is requested for "-help" to understand more about the command.
- Line 43: Executes a Tcl script named "vsdsynth.tcl" using the Tcl shell interpreter (tclsh) and passes the first command-line argument to the script.

![Image14](/assets/tclintro14.png)

</details>

<details>

 <summary>Module 2: Variable Creation and Processing Constraints from CSV</summary>

## Module 2: Variable Creation and Processing Constraints from CSV

</details>
