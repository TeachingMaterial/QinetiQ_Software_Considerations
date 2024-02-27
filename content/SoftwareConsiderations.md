---
title: Software Considerations
description: Software Considerations slides
class: gaia
_class:
  - lead
  - invert
style: |
    #img-right{
      float: right;
    }s
    img[alt~="center"] {
      display: block;
      margin: 0 auto;
    }
    table {
      border-collapse: collapse;
      font-size: 24px;
    }
    table, th,tr, td {
      border: none!important;
      vertical-align: middle;
    }
    @import url('https://unpkg.com/tailwindcss@^2/dist/utilities.min.css');
size: 16:9
paginate: true
_paginate: false

page_number: true
marp: true
math: true
---

# Software Considerations

    Seb Blair BEng(H) PGCAP MIET MIEEE MIHEEM FHEA 

    28/02/2023
    
    

<!--footer: "![w:200](figures/uog_white.png) \n\tQinetiQ | ManPower "  -->

---

## Content

1. Introduction
2. Development
3. Structure
4. Evolution/control
5. Practice writing code

<!--footer: "![w:200](figures/uog_purple.png)" -->

---

## 1. Introduction

Brief overview of the software development process: 
- Waterfall  (Requirements Analysis, System Design, Implementation, Testing,  Deployment, Maintenance)

- Agile (Iterative Development, Customer Collaboration, Adaptive Planning, Cross-Functional Teams, Continuous improvement)

- DevOps (Automation, Continuous Integration/Delivery, Infrastructure as code, feedback)

---
## Importance of software considerations in military/critical development: C/C++

<table style="width:100%">
<tr>
<td style="width:50%">

- Performance, efficiency, and ability to access low-level system resources.
- real-time systems, embedded software, and applications that require direct hardware interaction
- Portability and extensive tooling support make it well-suited for developing software that must run on diverse platforms and environments

</td>
<td>

```cpp
#include <iostream>
#include <cmath>

// Function to calculate elevation angle
double calculate_elevation(double x, double y, double z) {
  // Calculate horizontal distance from origin
  double horizontal_distance = std::sqrt(x*x + y*y);
  
  // Calculate elevation angle (in radians)
  double elevation_radians = std::atan2(z, horizontal_distance);
  
  // Convert elevation angle to degrees
  double elevation_degrees = std::atan2(elevation_radians);
  
  return elevation_degrees;
}

int main() {
  // Example coordinates
  double x = 100;   // X-coordinate
  double y = 200;   // Y-coordinate
  double z = 50;    // Z-coordinate (altitude)

  // Calculate elevation angle
  double elevation_angle = calculate_elevation(x, y, z);
  std::cout << "Elevation angle: " << elevation_angle << " degrees" << std::endl;
  // Elevation angle: 12.604382648379183 degrees

  return 0;
}
```

</td>
</tr>
</table>

--- 

## Ada

<table style="width:100%">
<tr>
<td style="width:50%">

-  Developing large-scale, mission-critical software systems, making it well-suited for military applications
-  Strong typing, concurrency support, and built-in features for safety and reliability 
- Used in safety-critical systems such as avionics, missile guidance systems, and command and control software

</td>
<td>

```ada
with Ada.Text_IO;
with Ada.Numerics.Elementary_Functions;

procedure Elevation is
  X : Float := 100.0;   -- X-coordinate
  Y : Float := 200.0;   -- Y-coordinate
  Z : Float := 50.0;    -- Z-coordinate (altitude)
  
  Horizontal_Distance : constant Float := 
    Ada.Numerics.Elementary_Functions.Sqrt(X**2 + Y**2);
  Elevation_Radians    : constant Float := 
    Ada.Numerics.Elementary_Functions.Atan2(Z, Horizontal_Distance);
  Elevation_Degrees    : constant Float := (Elevation_Radians * (180.0 / 3.145));
begin
  Ada.Text_IO.Put_Line("Elevation angle: " & 
                        Float'Image(Elevation_Degrees) & 
                        " degrees");
end Elevation;
```


</td>
</tr>
</table>

---

## Java

<table style="width:100%">
<tr>
<td style="width:50%">

- Developing enterprise-level systems, web-based applications, and software that requires platform independence
- Extensive standard libraries and robust security features make it suitable for building large-scale, distributed systems that can run on diverse hardware platforms and operating systems.

</td>
<td>

```java
public class Elevation {
  // Function to calculate elevation angle
  public static double calculateElevation(double x, double y, double z) {
    // Calculate horizontal distance from origin
    double horizontalDistance = Math.sqrt(x*x + y*y);
    
    // Calculate elevation angle (in radians)
    double elevationRadians = Math.atan2(z, horizontalDistance);
    
    // Convert elevation angle to degrees
    double elevationDegrees = Math.toDegrees(elevationRadians);
    
    return elevationDegrees;
  }

  public static void main(String[] args) {
    // Example coordinates
    double x = 100;   // X-coordinate
    double y = 200;   // Y-coordinate
    double z = 50;    // Z-coordinate (altitude)

    // Calculate elevation angle
    double elevationAngle = calculateElevation(x, y, z);
    System.out.println("Elevation angle: " + elevationAngle + " degrees");
  }
}
```

</td>
</tr>
</table>

---

## Python

<table style="width:100%">
<tr>
<td style="width:50%">

- Including rapid prototyping, data analysis, and scripting
- Simplicity, readability, and extensive ecosystem of libraries make it well-suited for quickly developing and deploying software solutions in military contexts.
- Data processing, simulation, and automation in defense applications.

</td>
<td>

```python
import math

# Function to calculate elevation angle
def calculate_elevation(x, y, z):
    # Calculate horizontal distance from origin
    horizontal_distance = math.sqrt(x**2 + y**2)
    
    # Calculate elevation angle (in radians)
    elevation_radians = math.atan2(z, horizontal_distance)
    
    # Convert elevation angle to degrees
    elevation_degrees = math.degrees(elevation_radians)
    
    return elevation_degrees

# Example coordinates
x = 100   # X-coordinate
y = 200   # Y-coordinate
z = 50    # Z-coordinate (altitude)

# Calculate elevation angle
elevation_angle = calculate_elevation(x, y, z)
print("Elevation angle:", elevation_angle, "degrees")
```

</td>
</tr>
</table>

--- 

## MATLAB

<table style="width:100%">
<tr>
<td style="width:50%">

- Modeling, simulation, and analysis tasks.
- High-level programming environment for numerical computation, data visualization, and algorithm development
- Developing and testing algorithms, control systems, and signal processing applications in defense-related domains such as radar, communications, and autonomous systems

</td>
<td>

```matlab
% Example coordinates
X = 100.0;   % X-coordinate
Y = 200.0;   % Y-coordinate
Z = 50.0;    % Z-coordinate (altitude)

% Calculate horizontal distance from origin
Horizontal_Distance = sqrt(X^2 + Y^2);

% Calculate elevation angle (in radians)
Elevation_Radians = atan2(Z, Horizontal_Distance);

% Convert elevation angle to degrees
Elevation_Degrees = rad2deg(Elevation_Radians);

% Display elevation angle
disp(['Elevation angle: ', num2str(Elevation_Degrees), ' degrees']);
```

</td>
</tr>
</table>

---

## Assembly 

<table style="width:100%">
<tr>
<td style="width:50%;  vertical-align: top;" >

- developing low-level system software, device drivers, and performance-critical code. 
- directly control hardware resources and optimize code for specific platforms and architectures

</td>
<td>

```asm
section .data
    x dd 100.0   ; X-coordinate
    y dd 200.0   ; Y-coordinate
    z dd 50.0    ; Z-coordinate (altitude)
    horizontal_distance dd 0.0
    elevation_radians dd 0.0
    elevation_degrees dd 0.0
... 
_start:
    ...
    ; Convert elevation radians to degrees
    fld dword [elevation_radians]
    fldpi
    fdiv
    fmul dword [180.0]
    fdiv dword [3.14159]
    fst dword [elevation_degrees]

    ; Print elevation angle
    mov eax, 4      ; system call number (sys_write)
    mov ebx, 1      ; file descriptor (stdout)
    mov ecx, msg    ; message to write
    mov edx, len    ; message length
    int 0x80        ; call kernel
    ...
```
</td>
</tr>
</table>

---

## 2. Development 

- Choosing the right IDE/Text Editor.
  - Discuss various options (e.g., Visual Studio, Code::Blocks, Sublime Text, etc.)
  - Consider features such as syntax highlighting, debugging capabilities, and project management tools.

---

## Visual Studio


![bg right:20% w:200](figures/Visual-Studio-Logo.png)

<div style="font-size:24px">

- **Features**: syntax highlighting, code completion, debugging capabilities, and built-in version control integration.

- **Languages**: Supports multiple programming languages, including C/C++, C#, and others.

- **Platform**: Available for Windows, macOS (via Visual Studio for Mac), and Linux (via Visual Studio Code).

- **Integration**: Seamlessly integrates with other Microsoft tools and services, such as **Azure DevOps** for project management and **GitHub** for version control.

---

## Code::Blocks
![bg right:20% w:250](figures/codeBlocks.png)

<div style="font-size:24px">

- **Features**: open-source, simplicity, and ease of use. It offers features such as syntax highlighting, code completion, and project management tools.
- **Languages**: Supports multiple programming languages, including C/C++.
- **Platform**: Available for Windows, macOS, and Linux.
- **Customization**: Highly customizable with support for plugins, allowing users to extend its functionality according to their needs.

</div>

---

## Sublime Text
![bg right:20% w:250](figures/sublime.png)

<div style="font-size:24px">

- **Features**: lightweight and fast text editor known for its speed and versatility. It offers features such as syntax highlighting, multiple selections, and a wide range of keyboard shortcuts.

- **Languages**: Supports multiple programming languages, including C/C++.

- **Platform**: Available for Windows, macOS, and Linux.

- **Extensibility**: Supports a rich ecosystem of plugins and packages, allowing users to enhance its functionality with additional features and customization options.

</div>

---

## Visual Studio Code (VS Code)/ Codium

![bg right:20% w:100 vertical](figures/VSCode.png)
![bg right:20% w:250](figures/VSCodium.png)

<div style="font-size:24px">

- **Features**: VS Code is a free, open-source code editor. It offers features such as syntax highlighting, code completion, debugging capabilities, and built-in version control integration.

- **Languages**: Supports multiple programming languages, including C/C++, C#, JavaScript, and others.

- **Platform**: Available for Windows, macOS, and Linux.

- **Extensions**: Extensively customizable with support for a wide range of extensions, allowing users to tailor it to their specific needs and preferences.

<!--
VScodium is a community-driven, MIT-licensed binary distribution of Microsoft’s editor VS Code that avoids telemetry and tracking

Not biased, but I spend much of my time here when I am not in the terminal
-->

---

## Setting Up Development Environment

<table style="width:100%" >
<tr>
<td style="width:50%;vertical-align: top;" >

- Installation of compilers (e.g., GCC for C/C++)

- Configuration of build systems (e.g., Makefiles, CMake)
  
- Integration with version control systems (e.g., Git)

</div>

</td>
<td>

```c
# Compiler
CXX := g++

# Compiler flags
CXXFLAGS := -std=c++11 -Wall -Wextra

# Source files
SRCS := main.cpp \
        elevation.cpp \
        uav.cpp

# Object files
OBJS := $(SRCS:.cpp=.o)

# Executable name
EXEC := elevation_calculator

# Rule to compile source files into object files
%.o: %.cpp
    $(CXX) $(CXXFLAGS) -c $< -o $@

# Rule to link object files into executable
$(EXEC): $(OBJS)
    $(CXX) $(CXXFLAGS) $(OBJS) -o $(EXEC)

# Clean rule
clean:
    rm -f $(OBJS) $(EXEC)
```

</td>
</tr>
</table>

<!--
- **CXX**: Specifies the C++ compiler (GNU g++ in this case).
- **CXXFLAGS**: Compiler flags, including C++ version (-std=c++11) and warnings (-Wall -Wextra).
- **SRCS**: List of source files (main.cpp).
- **OBJS**: List of object files derived from source files.
- **EXEC**: Name of the executable (elevation_calculator).
- The rule **%.o**: **%.cpp** compiles each source file (**\*.cpp**) into an object file (**\*.o**).
- The rule **\$(EXEC)**: **\$(OBJS)** links the object files into the executable.
- The clean rule removes object files and the executable.
-->

---
## Understanding Compilation Process

  - Overview of preprocessor, compiler, assembler, and linker stages

  - Common compilation flags and optimization techniques

![](figures/compiler_stages.png)

---
## Understanding Compilation Process
<div style="font-size:22px">

| Assembler|Interpreter| Compiler |
|-----|----|----|
|Translates high-level language into machine code| Translates high-level language into machine code|Translates high-level language into machine code|
|Uses the processors instruction set to convert|Translates source one line at a time| Translates all code at the same time|
|Runs quickly as converstion between two low languages is just relant on the processors instructions set|Needed every time you run the program| Only needed once to create the executable|
||Returns a list of errors found and on which lines| Will only inform you of the first error it finds|
||Runs more slowly as it is being translated every time the code runs|Once compiled it runs quickly but compiling can take a long time|

</div>

---

## 3. Structure

- Modular Programming
  - Importance of breaking code into manageable modules
  - Encapsulation and abstraction principles
  - Header files and source files organisation

---

## Data Structures and Algorithms
<div style="font-size:25px">

- **Arrays:** 
  - Suitable for sequential access, constant time access, and fixed-size collections.
  - Ideal for situations where the size is known beforehand and direct access is required.

- **Linked Lists:** 
  - Efficient for insertions and deletions at any position.
  - Suitable when dynamic size or frequent insertions/deletions are expected.

- **Trees:** 
  - Binary Trees: Ideal for hierarchical data structures.
  - Binary Search Trees (BST): Suitable for fast search, insertion, and deletion operations.

</div>

---

## Efficiency Considerations for Algorithm Design

- **Time Complexity:**
  - Measured in terms of the number of operations an algorithm performs in relation to the size of the input.
  - Examples:
    ```python
    # Python example
    def linear_search(arr, target):
        for i in range(len(arr)):
            if arr[i] == target:
                return i
        return -1
    ```

----
- **Space Complexity:**

  - Measure the amount of memory an algorithm uses in relation to the size of the input.
  - Examples:
    ```C
    // C/C++ example
    int factorial(int n) {
        if (n <= 1)
            return 1;
        else
            return n * factorial(n - 1);
    }
    ```

---

- **Efficiency Considerations:**

  - Choose data structures and algorithms that minimize time and space complexity for the problem at hand.
  - Consider trade-offs between time and space efficiency based on specific requirements.

---

## Principle of Locality 

Programs tend to use data and instructions with addresses near or equal to those they have used recently​

​Temporal Locality: Recently referenced items are likely to be referenced again in the near future​.

<div align=center>

![center](./figures/temp_local.png)

</div >

Spatial Locality: Items with nearby addresses tend to be referenced close together in time​

<div align=center>

![center](./figures/spatial_local.png)

</div>

---

## Locality Example

```c
int sum = 0;​
int a[5];
for ( int i = 0; i < n; i++ )​
{​
  sum += a[i];​
}
```
<div style="font-size:24px">

- Data
  - Access array elements `a[i]` in succession – Spatial Locality ​
  - Reference `sum` each iteration – Temporal Locality ​
- Instructions​
  - Reference instructions in sequence – Spatial Locality​
  - Cycle through loop repeatedly -  Temporal Locality​
  
</div>

---

## Stack and Heap

<div align=center>

![center w:800](./figures/heap_stack_books.png)

</div>

---

## Stack

<div style="font-size:29px">

- The stack segment is near the top of memory with a high address
>>
- Every time a function is called, the machine allocates some stack memory for it.
>>
- The allocation and deallocation of stack memory are automatically done
>>
- Stores variables used on the inside of a function (including the `main()` function). 
>>
- It’s a LIFO, “Last-In,-First-Out”, structure. Every time a function declares a new variable it is “pushed” onto the stack. 

</div>

---

## Stack

- The stack is managed by the CPU, there is no ability to modify it
>>
- Variables are allocated and freed automatically
>>
- The stack is not limitless – most have an upper bound
>>
- The stack grows and shrinks as variables are created and destroyed
>>
- Stack variables only exist whilst the function that created them exists

---

## Stack Overflow

![bg right:50% 100%](./figures/stackoverflow.png)

A stack overflow occurs if the call stack pointer exceeds the stack bound. The call stack may consist of a limited amount of address space, often determined at the start of the program.

---

## Heap

<div style="font-size:27px">

The heap is the diametrical opposite of the stack. 

- The heap is managed by the programmer,  ability to modify it is somewhat boundless
>>
- The heap is large and is usually limited by the physical memory available in an embedded environment and, in a PC it is stored within paging files on main memory (SSD)
>>
- This memory is not automatically managed – you have to explicitly allocate (using functions such as `malloc()`, `calloc()`, `realloc()`), and deallocate (`free()`) the memory. 
>>
- The heap requires pointers to access it

</div>

---

## 4. Code Reuse - a warning

- $2.96 $\equiv$ £2.35 billion
- 42 seconds
- One value
 
![bg right:60% 100%](./figures/ariane5.gif)

</div>

---

## Integer Overflow - Boeing 747:

The	software	counter	internal	to	the	generator	Control	units	(GCUs)	will	overflow	after	248	days	of continuous	power,	causing	that	GCU	to	go	into	failsafe	mode... resulting	in	a	loss	of	all	AC	
electrical	power	regardless	of	flight	phase

![bg right:50% 100%](./figures/boeing787.jpeg)

<div style="font-size:12px">

[https://s3.amazonaws.com/public-inspection.federalregister.gov/2015-10066.pdf](https://s3.amazonaws.com/public-inspection.federalregister.gov/2015-10066.pdf)

<p>


---

## Scenario
 
Your wage is stored in a 16-bit number, but<div align=center> then some store this in as an 8-bit number due to a coding error...

<div align=center style="margin:50px 10px 20px 30px">

$$at
  \begin{aligned}

    16\ Bit : £45,141_{10} &= 1\ 1\ 0\ 1\ 1\ 0\ 1\ 0\ 1\ 0\ 1\ 1\ 0\ 1\ 0\ 1_2\\
    
    &\big\Downarrow\\

  \end{aligned}
$$

</div>

<details>
<summary>...</summary>

<div align=center style="margin:50px 10px 20px 30px">

$$
\begin{aligned}
    8\ Bit : £\hspace{2em}181_{10} &= \hspace{6em} 1\ 0\ 1\ 1\ 0\ 1\ 0 \ 1_2 \\

  \end{aligned}
$$

</details>

</div>

---

## Your turn

<p align=center>

|**$2^{14}$** | **$2^{13}$** | **$2^{12}$** |  **$2^{11}$** |**$2^{10}$** | **$2^{9}$** | **$2^{8}$** |  **$2^{7}$** |  **$2^{6}$** | **$2^{5}$** | **$2^{4}$**  | **$2^{3}$** | **$2^{2}$** | **$2^{1}$** | **$2^{0}$** |
|---------|---------|---------|---------|---------|---------|---------|----------|----------|---------|----------|---------|---------|---------|--------|
|  16384   |   8192   |   4096   |    2048 |  1024   |   512   |   256   |    128  |    64   |   32   |   16   |    8    |   4    |   2   |   1  | 

</p>

<div align=center style="margin:50px 10px 20px 30px">

$29,952$ to 11-bit value:

</div>


$$
  \begin{aligned}

    14\ Bit : 29,952_{10} &= 1\ 1\ 0\ 1\ 1\ 0\ 0\ 0\ 0\ 0\ 1\ 0\ 0\ 0\ 0_2\\

    &\big\Downarrow\\

  \end{aligned}
$$

<details>
<summary>Answer</summary>

$$
\begin{aligned}

    11\ Bit : \hspace{1em}1040_{10} &= \hspace{3em} 1\ 0\ 0\ 0\ 0\ 0\ 1\ 0\ 0\ 0\ 0_2 \\

  \end{aligned}
$$

</div>

---

## Code Reuse Ariane 4 -> Ariane 5: One line of Code

<div style="font-size:29px">

```ada
-- Vertical velocity as measured by sensor
L_M_BV_32 := TBD.T_ENTIER_32S ((1.0/C_M_LSB_BV) * G_M_INFO_DERIVE(T_ALG.E_BV));
-- Check, if measured vertical velocity bias can be
-- converted to a 16 bit int. If so, then convert
if L_M_BV_32 > 32767 then
P_M_DERIVE(T_ALG.E_BV) := 16#7FFF#;
elsif L_M_BV_32 < -32768 then
P_M_DERIVE(T_ALG.E_BV) := 16#8000#;
else
P_M_DERIVE(T_ALG.E_BV) := UC_16S_EN_16NS(TDB.T_ENTIER_16S(L_M_BV_32));
end if;
-- Horizontal velocity bias as measured by sensor
-- is converted to a 16 bit int without checking
P_M_DERIVE(T_ALG.E_BH) := UC_16S_EN_16NS (TDB.T_ENTIER_16S ((1.0/C_M_LSB_BH) *
G_M_INFO_DERIVE(T_ALG.E_BH)));
```

</div>

---

## Simplified: 

<div style="font-size:29px">

```ada
-- Vertical velocity as measured by sensor
L_M_BV_32 = ConvertTo32BitSigned((1.0 / C_M_LSB_BV) * GetSensorInfo(T_ALG.E_BV))

-- Check if measured vertical velocity bias can be converted to a 16-bit int
if L_M_BV_32 > 32767 then
    P_M_DERIVE[T_ALG.E_BV] = 32767
elsif L_M_BV_32 < -32768 then
    P_M_DERIVE[T_ALG.E_BV] = -32768
else
    P_M_DERIVE[T_ALG.E_BV] = ConvertTo16BitSigned(L_M_BV_32)
end if

-- Horizontal velocity bias as measured by sensor is
-- converted to a 16-bit int without checking
P_M_DERIVE[T_ALG.E_BH] = ConvertTo16BitSigned((1.0 / C_M_LSB_BH) * GetSensorInfo(T_ALG.E_BH))

```


---
## A fix...
  
<div style="font-size:22px" >

```c
int32_t L_M_BV_32 = (int32_t)((1.0 / C_M_LSB_BH) * G_M_INFO_DERIVE(T_ALG.E_BV));

if (L_M_BV_32 > 32767) {
    P_M_DERIVE[T_ALG.E_BV] = 0x7FFF;
} else if (L_M_BV_32 < -32768) {
    P_M_DERIVE[T_ALG.E_BV] = (int16_t)0x8000;
} else {
    P_M_DERIVE[T_ALG.E_BV] = UC_16S_EN_16NS((int16_t)L_M_BV_32);
}

int32_t L_M_BH_32 = (int32_t)((1.0 / C_M_LSB_BH) * G_M_INFO_DERIVE(T_ALG.E_BH));

if (L_M_BH_32 > 32767) {
    P_M_DERIVE[T_ALG.E_BH] = 0x7FFF;
} else if (L_M_BH_32 < -32768) {
    P_M_DERIVE[T_ALG.E_BH] = (int16_t)0x8000;
} else {
    P_M_DERIVE[T_ALG.E_BH] = UC_16S_EN_16NS((int16_t)L_M_BH_32);
}

```

</div>


---

## 4. Version Control

- Tracking and managing changes: 
  - Work faster and more reliably
  
- Keeps track of all code modifications:
  - Specialised Database (Repository)
  
- Solves Common Team Problems:
  - Conflicting concurrent work, 
  - incompatiabilities due to concurrent working, 
  - having unstable releases


---

## Common Benefits of VCS

<div style="font-size:26px">

**Historical information​** : Looking at the history of changes it is a lot easier to find where bugs have originated. Also, it might be easier to find the right team member best suited to fix an error.​

**Branching​**: Working concurrently on multiple issues, without interference.​ Working on different types of releases.​

**Merging​** : Making sure that team members' work does not interfere with each other.​

**Traceability​** : Team members work more fluently together.​

**Testing and Documentation​**: Comments for each change and its association help produce better documentation​. Creating tests is easier​.

</div>

---

## Types of VCS

<div style="font-size:26px">

- **Local**:
  - Creates a database on your hardware​
- **Centralised​**:
  - History of changes is kept in a single database on a central server.​
  - Clients need to constantly communicate with the database and receive a partial working copy.​

- **Distributed​**:
  - Single database in a central server that is also distributed among all clients​
  - Each client has a full working copy of the repository​

</div>

---

## Git Characteristics 

<div style="font-size:26px">

- A very popular VCS
- Performance
  - Better performance compared to competitors
  - Deals with the data in the file rather than the file properties
- Security
  - Designed to provide security
  - Uses SHA-256 encryption
- Flexibility
  - Non-linear development
  - Detailed log of information

</div>

![bg right:30% 80%](./figures/git.png)

---

## GitHub - What are its features?

- Web-based graphical user interface (GUI)
- Features
  - Can act as a project manager
  - Hosts Git repositories
  - Secure with keys
![bg right:40% 50%](./figures/githublogo.png)

---

## Fundemental Git Functions

All commands are prepended with `git`

- `fetch`, `pull`: Get a working copy of a repository

- `add`, `commit`, `push`: Record a change or changes in at least one of the files stored in the repository.

- `branch`: Create a copy of a repository to be worked independently.

- `merge`: Collates changes of two different copies of a repository.

- `log`: Records information of each change within a repository

---

## Git - Branching

![horizontal](./figures/gitBranching.png)

<div style="font-size:22px">

 - **Main**: The default development branch. Whenever you create a Git repository, a branch named "master" is created, and becomes the active branch. 

- **Develop**: This is another branch, which is a way to `edit/develop/test` code without changing the Master branch. T

- **Topic**: A regular Git branch that is used by a developer to identify a conceptual line of development. 

</div>

---

## Git Commands Explained

<div style="font-size:24px">

- `clone`​: Get a working copy of the repository​

- `fetch`: Update the working copy of the repository without copying or removing any files.​

- `pull`: Update the working copy of the repository by copying and removing any files necessary.​

- `commit`: Update the working copy with all changes​

- `push​`: to the main repository all changes that have been committed to the local working copy.​

- `branch​`: Creates a copy of the repository that can be worked independently from the main branch​

- `Merge`: Combine two copies of a repository.​ Conflicts may be present.​

</div>

---

## Git Repository Staging Area

<div style="font-size:26px">

As part of the version control features there is the **Staging Area**. ​This feature enables the developer to move files independently of each other `git add <filename>` to the repository. Of course, you can do this all in one go with `git commit -a​`

</div>

<div align=center>

![center w:1000](./figures/gitStagingArea.png)

</div>

--- 


## Git Flow Diagram

<div align=center>

![](./figures/gitFlowDiagram.png)

</div>

---

## Learning Git

[https://learngitbranching.js.org/​](https://learngitbranching.js.org)


![bg right:50% 100%](./figures/gitlearningbranch.png)

---

## Pull Requests and Code Reviews

<div style="font-size:26px">

- **Pull Requests (PRs):**
  - Mechanism for proposing changes to a repository.
  - Allow team members to review, comment, and discuss proposed changes before merging.
  
- **Code Reviews:**
  - Crucial for maintaining code quality and consistency.
  - Involve inspecting code changes to identify bugs, improvements, or potential issues.
  - Facilitate knowledge sharing and learning within the team.


</div>

---

## Continuous Integration and Automated Testing

<div style="font-size:26px">

- **Continuous Integration (CI):**
  - Practice of frequently integrating code changes into a shared repository.
  - Automated process of building and testing code upon each integration.
  - Ensures early detection of integration errors and conflicts.

- **Automated Testing:**
  - Writing tests to automatically verify the correctness of code changes.
  - Types of tests include unit tests, integration tests, and end-to-end tests.
  - Integrated into the CI pipeline to provide rapid feedback on code changes.

</div>

---

## Naming Conventions

<div class="grid grid-cols-2 gap-4">
<div style="font-size:22px">

- Lower case `lowercase`: `publicdomiansoftware`
  - elements and attributes

- Upper case `UPPERCASE`: `PUBLICDOMAINSOFTWARE`
  - Naming constants

- Camel Case `camelCase`: `publicDomainSoftware`
  - local variable names

- Pascal Case `PascalCase`: `PublicDomainSoftware` 

  </div>

<div style="font-size:22px">

- Snake Case `snake_case`: `public_domain_software`
  -  C/C++ standard library names

- Screaming Snake Case `SCREAMING_SNAKE_CASE`:  `PUBLIC_DOMAIN_SOFTWARE`
  - Naming Constants

- Kebab Case `kebab-case`: `public-domain-software`
  - class names, ids
  
- Screaming Kebab Case `SCREAMING-KEBAB-CASE`:  `PUBLIC-DOMAIN-SOFTWARE`
  - Macros
  
</div>
</div>

---

## VS C Convention


<div class="grid grid-cols-2 gap-4">
<div>


```c
#include <stdio.h>
// Macros
#define MAX(a, b) ((a) > (b) ? (a) : (b))
#define MIN(a, b) ((a) < (b) ? (a) : (b))

// Global variables
int globalVariableOne;
int globalVariableTwo;

// Function prototypes
void InitializeGlobals();
int AddNumbers(int a, int b);

int main() {
    // Local variables
    int localVariable;

    // Initialize global variables
    InitializeGlobals();

    // Assign values to local variables
    localVariable = AddNumbers(globalVariableOne, globalVariableTwo);

    // Using macros
    printf("Max: %d\n", Max(globalVariableOne, localVariable));
    printf("Min: %d\n", Min(globalVariableTwo, localVariable));

    return 0;
}
```

</div>

<div>

```c
...
// Function definitions
void InitializeGlobals() {
    globalVariableOne = 5;
    globalVariableTwo = 10;
}

int AddNumbers(int a, int b) {
    // This comment explains the function behavior
    return a + b;
}
```
</div>

---

## Other conventions

**GNU C:**
- Naming: Typically follows the lowercase with underscores for variables and functions (e.g., `my_variable`,` my_function()`).
- Indentation: Uses spaces for indentation (often 2 or 4 spaces).
- Brace Style: Opening braces are usually on the same line as the statement, following the Kernighan and Ritchie style.

**GCC (GNU Compiler Collection):**
- Similar to the GNU C conventions.
- It may include additional guidelines for contributing to the GCC codebase.

---

## Other conventions

**LLVM:**
- Naming: Uses camelCase for function names and lowercase with underscores for variable names (e.g., `myVariable`, `my_function()`).
- Indentation: Typically 2 spaces.
- Brace Style: Opening braces are on the same line.

**Microsoft Visual Studio C++:**
- Naming: Uses PascalCase for function and method names, and camelCase for variable names (e.g., `MyFunction()`, `myVariable`).
- Indentation: Typically 4 spaces.
- Brace Style: Opening braces are on the same line.

---
## Other conventions
**Google C++ Style Guide:**
- Naming: Uses camelCase for variable names, and underscores for function names (e.g., `myVariable`,` my_function()`).
- Indentation: Typically 2 spaces.
- Brace Style: Opening braces are on the same line.

**Mozilla C++ Coding Style:**
- Naming: Uses camelCase for variable names and function parameters, and PascalCase for function names (e.g., `myVariable`, `MyFunction()`).
- Indentation: Typically 2 spaces.
- Brace Style: Opening braces are on the same line.

---
## Other conventions
**Linux Kernel Coding Style:**
- Naming: Uses lowercase with underscores for variables and functions (e.g., `my_variable`, `my_function()`).
- Indentation: Typically 8 spaces.
- Brace Style: Opening braces are on the same line.

**Qt Coding Style:**
- Naming: Uses camelCase for variables and functions (e.g., `myVariable`, `myFunction()`).
- Indentation: Typically 4 spaces.
- Brace Style: Opening braces are on the same line.

--- 

## Documentation, 'doc as you go...'

**Why Documentation**

- **You**
  - put down the project and return to it much later
  - want people to use it and give you credit
- **Others**
  - would be encouraged to contribute
  - more easily use your code
- **Science / Engineering**
  - Advances
  - Open collaboration
  - Reproducibility and transparency
![bg right:30% 100% vertical](./figures/codefacebook.png)
![bg right:30% 100% vertical](./figures/codefacebook2.png)

---
## Tools for Documentation
- **Python**
  - Sphinx, Doctest, Numpydoc
- **C++**
  - BoostBook, QuickBook, GhostDoc
- **Java**
  - Javadoc
- **Doxygen**
  - r, C, C#, PHP, Java, Python, and Fortran.

![bg right:40% 80% vertical](./figures/doxygenlogo.jpeg)

---

## Divergence Dilemma

- As with all documentation code develops faster and is released, thus creating a divergence, as in code <-> documentation becomes out of sync.
![bg right:50% 75% ](./figures/sequential.png)
![bg right:50% 80% ](./figures/parallel.png)

<!--
Typically source code and documentation are not written in parallel but sequentially. 

First the source code is developed and later some documentation is added. Whenever bugs in the source code must be fixed or additional features are added, very often the documentation is not updated. 

Hence the documentation is no longer describing the current version of the source code, but still reflects the initial version of the software program.
-->

---

## Literate Programming
-  a computer program is given as an explanation of how it works in a natural language, such as English, interspersed (embedded) with snippets of macros and traditional source code, from which compilable source code can be generated.

![bg right:40% 80% vertical](./figures/doxygenlogo.jpeg)

---

## Doxygen syntax

<div class="grid grid-cols-2 gap-4">
<div>

```c
/**
 * @file calculator.c
 * @brief Simple calculator program with basic operations.
 */

#include <stdio.h>
/**
 * @brief Adds two numbers.
 * @param a The first operand.
 * @param b The second operand.
 * @return The sum of a and b.
 */
int add(int a, int b) {
    return a + b;
}
/**
 * @brief Subtracts two numbers.
 * @param a The first operand.
 * @param b The second operand.
 * @return The result of subtracting b from a.
 */
int subtract(int a, int b) {
    return a - b;
}
```

</div>

<div>

```c
/**
 * @brief Main function to demonstrate calculator operations.
 * @return 0 if successful, otherwise an error code.
 */
int main() {
    int num1, num2;
    
    printf("Enter two numbers: ");
    scanf("%d %d", &num1, &num2);

    printf("Sum: %d\n", add(num1, num2));
    printf("Difference: %d\n", subtract(num1, num2));

    return 0;
}

```
</div>

</div>

---

## Example output

<div class="grid grid-cols-2 gap-4">
<div>

![center w:950](./figures/doxygenOutput.png)

</div>

<div>

![center w:950](./figures/doxygenOutput2.png)

</div>

</div>

---

## Doxygen Configuration file

<div style="font-size:21px">

```sh
PM> doxygen.exe doxygenConfigFile
```

```
# Doxyfile for calculator.c

DOXYFILE_ENCODING      = UTF-8
PROJECT_NAME           = "Calculator Documentation"
PROJECT_NUMBER         = 1.0
PROJECT_BRIEF          = "A simple calculator program with basic operations."

OUTPUT_DIRECTORY       = ./docs
CREATE_SUBDIRS         = NO

INPUT                  = calculator.c
RECURSIVE              = NO

EXTRACT_ALL            = YES
...

GENERATE_LATEX         = NO
```

</div>

---

## 6. Conclusion

- Recap of key points covered in the lecture
- Encouragement for continuous learning and improvement in software development skills