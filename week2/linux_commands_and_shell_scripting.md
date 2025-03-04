**🖥️ Shell and Shell Scripting Basics**

**What is a Shell?**

-   A **shell** is a command-line interpreter that allows users to
    interact with the operating system.

-   It takes user commands and executes them.

-   Examples of popular shells:

    -   **Bash (Bourne Again Shell)** -- Most commonly used in Linux.

    -   **Zsh (Z Shell)** -- A more advanced version of Bash.

    -   **Fish (Friendly Interactive Shell)** -- Focuses on ease of use.

**What is Shell Scripting?**

-   **Shell scripting** is writing a sequence of shell commands in a
    file and executing them as a script.

-   It automates repetitive tasks like backups, monitoring, and software
    installation.

✅ **Advantages of Shell Scripting:**

-   **Automation** -- Reduces manual work.

-   **Batch Processing** -- Execute multiple commands in a sequence.

-   **System Administration** -- Manage processes, files, and users.

-   **Custom Tools** -- Create utilities to perform specific tasks.

**🖥️ Basics of Shell Scripting**

**Writing a Shell Script**

1.  **Create a file**:

2.  vi myscript.sh

3.  **Add the shebang (#!) to specify the interpreter**:

4.  #!/bin/bash

5.  echo \"Hello, Shell Scripting!\"

6.  **Make it executable**:

7.  chmod +x myscript.sh

8.  **Run the script**:

9.  ./myscript.sh

**Variables in Shell Scripting**

-   **Defining Variables**:

-   name=\"tamanna\"

-   age=25

-   **Accessing Variables**:

-   echo \"Name: \$name, Age: \$age\"

-   **Reading User Input**:

-   read -p \"Enter your city: \" city

-   echo \"You live in \$city.\"

**Conditional Statements (If-Else)**

✅ **Syntax:**

if \[ condition \]; then

\# Code if condition is true

elif \[ another_condition \]; then

\# Code if another_condition is true

else

\# Code if none of the conditions are true

fi

✅ **Example: Check if a number is positive, negative, or zero**

#!/bin/bash

read -p \"Enter a number: \" num

if \[ \"\$num\" -gt 0 \]; then

echo \"Positive\"

elif \[ \"\$num\" -lt 0 \]; then

echo \"Negative\"

else

echo \"Zero\"

fi

**Loops in Shell Scripting**

✅ **For Loop:**

for i in {1..5}; do

echo \"Number: \$i\"

done

✅ **While Loop:**

i=1

while \[ \"\$i\" -le 5 \]; do

echo \"Count: \$i\"

((i++))

done

✅ **Until Loop (Runs until the condition becomes true):**

i=1

until \[ \"\$i\" -gt 5 \]; do

echo \"Until Count: \$i\"

((i++))

done

**📦 tar Command (Archiving & Compression)**

**What is tar?**

-   tar (**Tape Archive**) is used to **combine multiple files** into a
    single archive file.

-   It **does not compress** by default but can be combined with gzip or
    bzip2 for compression.

**Creating a Tar Archive (.tar)**

tar -cvf archive.tar file1 file2 folder/

-   **-c** → Create a new archive.

-   **-v** → Show progress (**verbose**).

-   **-f** → Specify the archive filename.

-   **Example Output:**

-   file1

-   file2

-   folder/

**Extracting a Tar Archive**

tar -xvf archive.tar

-   **-x** → Extract files from the archive.

-   **-v** → Show progress.

-   **-f** → Specify the archive file.

✅ **Extract to a specific folder**:

tar -xvf archive.tar -C /path/to/destination/

**4️⃣ Creating a Compressed Archive (.tar.gz or .tgz)**

tar -czvf archive.tar.gz file1 file2 folder/

-   **-z** → Compress using gzip.

-   **Example Output:** A compressed archive.tar.gz file.

✅ **Extracting .tar.gz files:**

tar -xzvf archive.tar.gz

**Creating a Highly Compressed Archive (.tar.bz2)**

tar -cjvf archive.tar.bz2 file1 file2 folder/

-   **-j** → Compress using bzip2 (better compression but slower).

✅ **Extracting .tar.bz2 files:**

tar -xjvf archive.tar.bz2

**Viewing Contents of a Tar Archive**

tar -tvf archive.tar

-   **-t** → List the files inside the archive **without extracting**.

**Adding Files to an Existing Tar Archive**

tar -rvf archive.tar newfile.txt

🚨 **Note:** This does **not** work for compressed archives (.tar.gz).

**Deleting a File from a Tar Archive**

tar \--delete -f archive.tar file1.txt

🚨 **Note:** You **cannot delete from compressed archives** (.tar.gz).

**9️⃣ Extracting a Single File from a Tar Archive**

tar -xvf archive.tar file1.txt

✅ **Extract Multiple Files:**

tar -xvf archive.tar file1.txt file2.txt

**🔍 Summary of tar Options**

  -----------------------------------------------------------------------
  **Action**             **Command**
  ---------------------- ------------------------------------------------
  **Create .tar**        tar -cvf archive.tar files

  **Create .tar.gz**     tar -czvf archive.tar.gz files

  **Create .tar.bz2**    tar -cjvf archive.tar.bz2 files

  **Extract .tar**       tar -xvf archive.tar

  **Extract .tar.gz**    tar -xzvf archive.tar.gz

  **List contents**      tar -tvf archive.tar

  **Add to archive**     tar -rvf archive.tar newfile.txt

  **Delete from          tar \--delete -f archive.tar file1.txt
  archive**              
  -----------------------------------------------------------------------

Hacker Rank problems\
1. Problem 1

<https://www.hackerrank.com/challenges/bash-tutorials-lets-echo/problem?isFullScreen=true>

![](media/image1.png){width="6.268055555555556in"
height="2.7840277777777778in"}

2\. Problem 2

<https://www.hackerrank.com/challenges/bash-tutorials---looping-and-skipping/problem?isFullScreen=true>

![](media/image2.png){width="6.268055555555556in"
height="2.7909722222222224in"}

3\. Problem 3

<https://www.hackerrank.com/challenges/bash-tutorials---a-personalized-echo/problem?isFullScreen=true>

![](media/image3.png){width="6.268055555555556in"
height="2.8006944444444444in"}

4\. Problem 4

<https://www.hackerrank.com/challenges/bash-tutorials---looping-with-numbers/problem?isFullScreen=true>

![](media/image4.png){width="6.268055555555556in"
height="2.826388888888889in"}

5\. Problem 5

<https://www.hackerrank.com/challenges/bash-tutorials---the-world-of-numbers/problem?isFullScreen=true>

![](media/image5.png){width="6.268055555555556in"
height="2.7930555555555556in"}

6\. Problem 6

<https://www.hackerrank.com/challenges/bash-tutorials---comparing-numbers/problem?isFullScreen=true>

![](media/image6.png){width="6.268055555555556in"
height="2.7840277777777778in"}

7\. Problem 7

<https://www.hackerrank.com/challenges/bash-tutorials---getting-started-with-conditionals/problem?isFullScreen=true>

![](media/image7.png){width="6.268055555555556in"
height="2.834722222222222in"}

8\. Problem 8

<https://www.hackerrank.com/challenges/bash-tutorials---compute-the-average/problem?isFullScreen=true>

![](media/image8.png){width="6.268055555555556in"
height="2.8006944444444444in"}