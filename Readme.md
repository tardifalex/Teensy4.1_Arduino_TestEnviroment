# Cart Puller MCU firmware

This program is the property of AIS and is the codebase for the vehicles microcontroller. 

## Getting Started

1. VS Code is used for pin/chip configuration and code is generated for Arduino dev environment
2. VS code is used for software development

### Folder Structure

1. Inc/main.h Header for main.c module
2. Inc/config.h for all #define declerations
3. Inc/types.h for type delerations
4. Inc/includes.h for includes

### Hardware and Software environment

Current Hardware is STM32407
Current Development environment is STM IDE and can be found here: https://www.st.com/en/development-tools/stm32cubeide.html
Connecting to the STM may pose an issue if necessary download the following utility tool and upgrade the software on the STM: https://www.st.com/en/development-tools/stsw-link004.html


### Commits and Branch naming guidelines

1. When commiting:
- please be clear what your commit is doing. It should be clear from the commit message what has been done.

2. Branch naming: Please prefix the branch with a one of the following or with another prefix that best describes the purpose of the branch. 

- feat_description_Name: A new feature 
- fix_description_Name: A bug fix 
- docs_description_Name: Documentation only changes 
- style_description_Name: Changes that do not affect the meaning of the code (white-space, formatting, etc)
- perf_description_Name: A code change that improves performance 
- test_description_Name: Adding missing tests 

Example: fix_linearActuator_Misha

### Repo guidelines:

Below a rough workflow on how to work with branches:

0. Pull master. Always pull master so that you are creating a branch from the latest version of master
1. Create Branch.
2. Work on your branch and commit regularily at mini-milestones
    - you can discard changes on a file, which then destroys changes and goes back to last commit of that file
    - you can revert a commit: creates a new commit that undoes the previous commit
    - you can reset to a commit: dangerous operation that without a trace destroys everything up to the target commit
3. Push your branch as required.
4. Pull Master. Prior to merges pull master again
5. Test code rigorously
6. Create pull request on BitBucket
7. Have pull request reviewed and complete the pull request with the merge
  i) if merge conflict exists: 
    - pull master
    - checkout branch
    - merge master into branch
    - resolve conflict
    - commit and push branch
    - then merge pull request

NOTE:

  - never commit on master. Always work on your branch and then create pull request
  - never push to master. This is the most dangerous thing you could do. Pushing bugged code onto master makes your faulty code everyones problem. Always created a pull request. 
  - always pull master, before making new branch
  - always pull master, before merging



---------------------------------------------------------------------------------------------------------------------------------
### Naming guide line:

- This is a guideline and there are exceptions to every exmple below. But where applicable, please follow the naming convention below. 

1. variables: 
- NB: - variable naming has to be descriptive!!! variable name "data", "angle", "position", etc are not acceptable. 
      - Variables must not be vague! 
      - variables should include the full description of its location, function, type, etc
      - long variable names are no problem
      - int angle; int velocity;                                                // NOT acceptable
      - int steeringControlAngleEPAS8Bit; int vehivleVelocityMeterPerSecond     // is acceptable
- lower camel case
- Example: int thisIsMyVar;

2. #define:
- All capitals with underscore ('_') to seperate works
- Example: #define THIS_IS_A_HASH_DEFINE_CONSTANT 1

3. global constants:
- all caps with underscore ('_') as seperator
- but where possible rather use #define
- Example: const double TWO_PI = 6.28318531;

4. pointer variables:
- prefix the pointer with a 'p. First letter of the word after the 'p' is capital but rest of the work is lower case. 
- for several work pointers follow normal variabel naming after first word
- place the '*' on the side of the variable
- Example: char *pMyPointer

5. function:
- functions perform an action and should be named accordingly. Use words like: do, get, dump, read, write, Check, etc instead general names
    - use CheckForErrors() instead of ErrorCheck()
    - use DumpDataToFile() instead of DataFile()
    - use getData(), readData() instead of Data() and so on. 
- capital letter on the start of every new work
- no spaces, '_' or any other seperators

6. class:
- capital letter on the start of every new work
- no spaces and no '_' or any other seperators
- No ('_') is permitted
- Example: class ThisIsMyClass{}

6.1. class internal variables:
- private variables in a class should always have a underscore ('_') prefix
- This is often also done by prefixing internal variables with an 'm'. But the '_' is preferred as it makes internal variables clearer to read
- Example: double _private_variable;


7. types: (typedef struct, typedef enum, etc) 
- All types, classes, structs, enums, etc have the same naming convention
- Start with Capital on every new work but the rest of the words are small. 
- No spaces or underscores


8. file names:
- all small with underscore ('_') or Hyphen ('-') seperated
- NEVER use spaces in file names!
- Example: this-is-a-file0name
           this_is_a_different_file_name


NOTES:
- Try not to use 'String' declerations. They can cause an unstable memory stack and use up double the memory space if not cleaned up well. 
- If you have to use strings, alwats 'F' the strings


### Converting main.c to main.cpp

1. Make a copy of main.c file
2. Rename the copy to main.cpp
3. Right click on project folder and click "Options for Target..."
    i)Navigate to "Target" tab. Uncheck "Use MicroLib"
    ii)Navigate to C/C++ tab. Uncheck "C99Mode" and change "Optimization" t0 "level 0"
    iii) click ok
4. Right click on main.c and remove it from the project folder