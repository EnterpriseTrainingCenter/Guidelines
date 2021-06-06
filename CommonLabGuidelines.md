# Common Guidelines for writing Labs

## Table of contents

* [File format](#file-format)
* [Structure](#structure)
* [Technicalities](#technicalities)
* [File structure](#structure)
* [Language](#language)
* [Formatting](#formatting)

## File format

Lab guides are written using Markdown. You can find a cheat sheet of the supported formatting symbols in the [markdown-here repository on Github][1]

Here is a summary of the most important symbols.

### Headers

````markdown
# Level 1
## Level 2
### Level 3
#### Level 4
````

### Empasis

Strong emphasis (bold) for screen elements or text to be entered.

````markdown
**Label**
````

Emphasis (italic), e. g. for notes.

````markdown
*Note:*
````

### Lists

#### Numbered lists with automatic numbering

````markdown
1. Step 1
1. Step 2
1. Step 3
````

results in

1. Step 1
1. Step 2
1. Step 3

#### Unordered lists

````markdown
* Element
* Element
* Element
````

#### Nested lists

````markdown
1. Step 1
1. Step 2
    * Element
    * Element
    * Element
1. Step 3
````

### Links

Reference list of links at the end of the file:

````markdown
[figure 1]: images/Lab01/figure01.png

[1]: http://slashdot.org
````

Using the referenced external link within the text:

````markdown
[Slashdot][1]
In the dialog enter something ([figure 1]).
````

Alternatively, you can also include hyperlinks in angled brackets.

````markdown
<http://slashdot.org>
````

### Images

Reference list of links at the end of the file:

````markdown
[figure 1]: images/Lab01/figure01.png
````

Embed a referenced image.

````markdown
![alternate text][figure 1]
````

### Code and Syntax Highlighting

Block of code are fenced by lines with three or four back ticks followed by an indicator of the language.

````markdown
    ````powershell
    Get-Process
    ````
````

### Tables

````markdown
Colons can be used to align columns.

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
````

### Blockquotes

````markdown
> What is the difference between A and B?
````

## Structure

1. The labs are numbered accoriding to course modules. So, the lab for module 4 ist Lab 4. If there are multiple labs for a module, the labs should have a suffix in form of a letter, e. g. Lab 4A, Lab 4B, Lab 4C.
1. A lab consists of one or more exercise. Exercises are dependent on each other and must be performed in the given order. An exercise is a part of the lab with a clear goal.

1. An exercise consists of one or more tasks. A task is a major step to fulfill the goals of the exercise.

1. Each task must be completed on a single computer or virtual machine. If the computer or virtual machine must be switched, a new task should be created.

1. Each lab starts with a headline in the form of

   **Lab x: Topic of the lab**

    The headline is a top level (level 1) headline.
1. After the level 1 headline, a bullet-point list of **Required VMs** preceeded with a level 2 headline of that name follows, if necessary. The VMs should be listed in alphabetical order.
1. The next level 2 headline is **Exercises**, followed by a numbered list of the exercises in the lab. The list should be a hyper-linked list to the exercise sections in the lab.
1. Each exercise starts with a level 3 headline **Introduction**. The text after the introduction should contain all information required to complete the lab without the detailed descriptions.
1. Within the introduction section, a level 4 headline **Tasks** follows, followed by a numbered list of the tasks in the exercise. The list should be a hyper-linked list to the task sections in the exercise.
1. After the introduction section, a level 3 headline in the form **Task x: Task description** follows for each task.
1. Each task should start with the sentence *Perform these steps on **VMName**, followed by a numbered list of steps to perform.
1. If a task contains several variations to perform the task, e. g. using Desktop Experience, Windows Admin Center, or PowerShell, use level 4 headlines to differentiate between the variations.

## Technicalities

1. Whenever possible, different ways for completing a task, should be given. E. g. for Windows Server, a version using *Desktop Experience* and a version using *PowerShell*. If the course also contains setup instructions for or a read-to-use Windows Admin Center instructions for completing the task with this tool should also be included.

1. If possible, a lab should not depend on other labs.

1. If possible, a lab should be non-desctructive. Computers used in the lab, should be able to be used in other labs.

1. If possible, the labs should be designed to be performed without any particular order.

## File structure

1. A lab repository should contain a at the root readme.md describing the course and give some usage and contribution guidelines.
1. The repository should contain a folder named **Instruction**.
1. The folder **Instructions**, can contain folders, depending on the course structure,
    * Demos
    * Exercises
    * Labs
1. Images must be saved in a separate **images** folder. Depending on usage of the images, the folder can be a sub folder of either folder, including root.
1. In the **images** folder, you may create a folder for the images of each demo, exercise, or lab, e. g. **Lab01**.
1. Lab instruction files should be named in the form **LAB_##-This_is_the_topic_of_the_lab.md**. The number should be written as double-digit with a leading zero, if applicable. Between the word **LAB** and the number, a underscore must be written. After the number, a dash follows. In the topic, spaces and interpunction are replaced with underscores, only dashes are allowed.
1. Image files should be numbered in the form **figure##.png**. The number should be double-digit at least with leading zeros. Optionally, after a dash, you may include a description of the image.

## Language

1. The steps should be written in imperative, clear and short language.
1. The sentences should be written in the form *\<Where\>, \<action\> \<object\>*, except for the first step, where you can leave out the \<Where\> part. If a previous step opens a window or an applicaton, the next step must start with *In **\<Window name\>**, do something*. For following steps in the same window, the window name does not need to written again.
   
   *Bad*
   1. Open **Server Manager**.
   1. Click **Manage**, **Add Roles and Features**.

   *Good*
   1. Open **Server Manager**.
   1. In **Server Manager**, in the menu bar, click **Manage**, **Add Roles and Features**.

1. If some action in a control has to be performed, first write the type of the control, then the label of the control.
    
    *Bad*
    1. In the **Servername** text box, enter **SRV1**.
    
    *Good*
    1. In **Servername**, enter **SRV1**.
    
    *Better*
    1. In text box **Servername**, enter **SRV1**.

1. For code blocks or commands entered in some shell, the task should describe what the code does. The code to be entered should be written in a code block directly after the step.

1. Explanations of special syntax structure in code blocks, not necessarily part of the lab, should be written as code comments

    *Bad*
    1. Enter the following command to list all available Windows features with a name that begins with **RSAT**. ? is an alias for Where-Object.

        ````powershell
        Get-WindowsFeature | ? Name -like 'RSAT*'
        ````

    *Good*
    1. Enter the following command to list all available Windows features with a name that begins with **RSAT**.

        ````powershell
        # ? is an alias for Where-Object
        Get-WindowsFeature | ? Name -like 'RSAT*'
        ````

1. The term *right-click* should not be used. In general right-click calls the context menu. Therefore, name the context-menu.

    *Bad*

    Right-click the user and click **Properties**.

    *Good*

    In the context-menu of the user, click **Properties**.

    or

    From the context-menu of the user, select **Properties**.

## Formatting

1. The numbered, hyper-linked lists of exercises and tasks, must be formatted in markdown reference style, e. g.

    ````markdown
    1. [Authoring an Unattend.xml file](#exercise-1-authoring-an-unattendxml-file)
    1. [Building a new Windows Server DVD](#exercise-2-building-a-new-windows-server-dvd)

    ````

    ````markdown
    1. [Install the Telnet Client by using Server Manager](#task-1-install-the-telnet-client-by-using-server-manager)
    1. [Install the Hyper-V Management Console from the RSAT Tools using PowerShell](#task-2-install-the-hyper-v-management-console-from-the-rsat-tools-using-powershell)

    ````

1. Labelled elements on the screen must be written **bold**. If the user has to enter text, this is also written **bold**.

    *Bad*

    ````markdown
    1. In Servername, enter SRV1.
    ````

    *Good*

    ````markdown
    1. In **Servername**, enter SRV1.
    ````

1. Tables can be used to provide a key/value list for long forms. In this case, the keys are the labels in the dialog or form and should be written **bold**. The values to enter or select, should be written normal, e. g.

    ````markdown
    | Field          | Value |
    | -------------- | ----  |
    | **First name** | John  |
    | **Last name**  | Doe   |
    ````

1. All image files used in the lab instruction, must be referenced at the end of the file. They should be numbered as figure #, e. g.

    ````markdown
    [figure 1]: images/Lab01/figure01.png
    [figure 2]: images/Lab01/figure02.png
    [figure 3]: images/Lab01/figure03.png
    [figure 4]: images/Lab01/figure04.png
    [figure 5]: images/Lab01/figure05.png
    ````

1. Within the tasks, images should be written as reference-style links, with , e. g.

    ````markdown
    1. On the **Select features** page, select **Telnet Client** ([figure 21]).
    ````

    Images must not be embedded into the steps of a task, however, if an image should show a state before or after a task, the image can be embedded using reference-style. They must include an alternate text, e. g. 

    ````markdown
    Note the scheduled tasks for **Storage Tier Management**.

    ![Scheduled tasks for storage Tiers Management: Storage Tiers Management Initialization, Storage Tiers Optimization][figure 9]
    ````

1. Code blocks must indicate the language used. For a list of supported languages, see the [highlights.js project on Github][2].

1. Questions, the students should answer during a lab, should be marked as blockquote, e. g.

    ````markdown
    > Do you see any difference?
    ````


[1]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
[2]: https://github.com/highlightjs/highlight.js/blob/main/SUPPORTED_LANGUAGES.md