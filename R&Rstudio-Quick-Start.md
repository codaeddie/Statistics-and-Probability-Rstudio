# R & RStudio QuickStart Guide

# ⬇️ Download Link for book ⬇️

### **<u> </u>**[**<u><mark>PROBABILITY With Applications and R</mark></u>**](https://www.pdfdrive.com/probability-with-applications-and-r-e175263320.html)

!! **R & RStudio: What is the difference?**
!! First time users of **R **are often confused as to the difference between **R **and **RStudio**.
!! **RStudio** is actually an add-on to **R**: it takes the **R** software and adds to it a very user-friendly graphical interface. Thus, when one uses **RStudio**, they are still using the full version of **R **while also getting the benefit of greater functionality and usability due to an improved user interface. As a result, when using **R**, one should always use **RStudio**; working with **R **itself is very cumbersome.

* * *

## **Software summary **👀

-   **R **and **RStudio** are not two different versions of the same thing. One can't be substituted for the other.
-   In fact, they work together. **R **is a programming language for statistical calculation. And **RStudio** is an Integrated Development Environment (IDE) that helps you develop programs in **R**.
-   You _can_ use **R **without using** RStudio**, but you _can't_ use **RStudio** without using **R**, so **R **comes first.

## **Requirements \*\***☝️\*\* :

Since **RStudio** is an add-on to **R**, you must first download and install **R**. On your computer, you will see **R **and** RStudio** as separate installed programs. When using **R **for data analysis, you will always open and work in **RStudio**; you must leave **R **installed on the computer for **RStudio** to work, even though you will likely never open the **R **console\*\* \*\*itself.

## How-to guide 🐣

To install **R & RStudio **on your local computer follow these steps:

(it would be best to read through all the steps before you begin downloading)

### Step 1: Download the R installer

-   **R for Windows: ** [<u>Click Here</u>](https://cran.r-project.org/bin/windows/base/)
    -   Click the link on the top of the page that looks like this⬇️ ⬇️ :

![image.png](media_R%20&%20RStudio%20QuickStart%20Guide/image.png)

-   **R for Mac: ** [<u>Click Here</u>](https://cran.r-project.org/bin/macosx/)
    -   Pick the latest version
-   **R for Linux: **[ <u>Click Here</u>](https://cran.rstudio.com/)

![image.png](media_R%20&%20RStudio%20QuickStart%20Guide/02d0b5d2-e0ff-4a99-b975-fe71b543df6b_image.png)

> <mark>**\_ \_**</mark><mark>​Install R by opening the installer and following the steps. It's best to leave all the configuration settings as default and simply press next. Once R is finished, there is no need to launch the terminal unless you want to, you can proceed to Step 2.</mark>

### Step 2: Download the RStudio Installer

> **Installing RStudio:** [<u>Click Here</u>](https://www.rstudio.com/products/rstudio/download/)

-   Verify you have already installed **R **and that you can launch the **R **application
-   Download the **RStudio** Desktop installer from [<u>THIS LINK</u>](https://rstudio.com/products/rstudio/download/)
-   <mark>Scroll down until you see the download section as the image below. </mark><mark>⬇️</mark><mark>⬇️</mark><mark>⬇️</mark><mark> Then select the correct download for your OS:</mark>

![image.png](media_R%20&%20RStudio%20QuickStart%20Guide/afde8387-32e9-44b3-b1cd-4812ca7d47fd_image.png)

-   ​Install the **RStudio **IDE by opening the installer and following the steps
    -   <mark>⚠️</mark><mark> The instructions for the installer will eventually ask you where </mark>**<mark>R </mark>**<mark>itself has when been installed. Generally it defaults to the correct path on your system for </mark>**<mark>R, </mark>**<mark>though you may have to find where you have installed </mark>**<mark>R </mark>**<mark>and type the path into the </mark>**<mark>RStudio </mark>**<mark>installer manually.</mark><mark>⚠️</mark>
-   That's it! You can now run **RStudio **from your local computer.
-   Once you have everything installed, go ahead and launch the **RStudio **IDE
    -   Which should look like this <mark>⬇️</mark><mark>⬇️</mark><mark>⬇️</mark>

![image.png](media_R%20&%20RStudio%20QuickStart%20Guide/9f654686-c61d-4d4f-86ed-14e17a5e156c_image.png)

* * *

* * *

## **Getting Started \*\***💻\*\*

-   **R **is used both for software development and data analysis. We will operate somewhere between these two tasks. Our goal will be to analyze data 📊 , but we will also perform programming exercises that help illustrate certain concepts.

> <mark>Our main goal in the labs will follow this flow:</mark>

1.  Understand the basic tasks & data
2.  Review the Code Setup and run the sample code
3.  Complete the coding problem
4.  Analyze and explain what the results actually mean.

## RStudio IDE 🎰:

-   The **RStudio **interface is simple. You type R code into the bottom line of the **RStudio **console pane and then click Enter to run it. The code you type is called a _command_, because it will command your computer to do something for you. The line you type it into is called the _command line_.

## Console🧮:

![image.png](media_R%20&%20RStudio%20QuickStart%20Guide/88407b4d-3257-4eaa-9b23-37f3a7659c0a_image.png)

-   The large window on the left side is the **Console**.
-   You can think of this as the “calculator” for **RStudio**. This is were all of the input, calculations and output are contained. In fact, if you were to run R and not **RStudio**, this Console is the only window you would see; **RStudio** adds all of the other interface components that you see.

> When you type a command at the prompt and hit Enter, your computer executes the command and shows you the results. Then **RStudio **displays a fresh prompt for your next command. For example, if you type `1 + 1` and hit Enter, **RStudio **will display:

    > 1 + 1
    [1] 2
    >

Once you get the hang of the command line, you can easily do anything in **R** that you would do with a calculator. For example, you could do some basic arithmetic:

    2 * 3
    ## 6

    4 - 1
    ## 3

    6 / (4 - 1)
    ## 2

<mark>I’ve left out the </mark><mark>`>`</mark><mark>’s and </mark><mark>`[1]`</mark><mark>’s. This will make the code easier to copy and paste if you want to put it in your own console.</mark>

## RMD Files 📄

<mark>Included in the Lab assignment page on canvas are a set of .Rmd files which were used to create all of the content contained in them. Usually, </mark>**<mark>R</mark>**<mark> code scripts are saved as .R files. However, you will notice that all of these are saved as </mark><mark>**.RMD files**</mark><mark>. These are called </mark><mark>**R Markdown files**</mark><mark>. </mark>

**R Markdown** provides an unified authoring framework for data science, combining your code, its results, and your prose commentary. R Markdown documents are fully reproducible and support dozens of output formats, like PDFs, Word files, slideshows, and more.

-   Here are some Cheat sheets available for:
    -   [R Markdown](https://github.com/rstudio/cheatsheets/raw/main/rmarkdown-2.0.pdf)
    -   [R Markdown Reference ](https://www.rstudio.com/wp-content/uploads/2015/03/rmarkdown-reference.pdf?_ga=2.177196197.1620992394.1661131455-457990688.1650949177)
    -   [R Markdown CheatSheet](https://www.rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf)

# Create your first R Markdown

1.  To create a new R Markdown file, in R Studio select `File`>`New File`>`R Markdown`…
2.  Then, you will see a window pop-up titled “New R Markdown”. Here, you specify the type of file you wish to create... default output is HTML, and this is recommended.
3.  Finally, select `Ok` to create your new R Markdown file. You will see it appear as a tab in your R Studio session, similar to when a new script is created.

## Understanding the R Markdown editor 📐

When creating a new HTML-type R Markdown document, you should see the following window in your R Studio session:

![Markdown_ex.png](media_R%20&%20RStudio%20QuickStart%20Guide/Markdown_ex.png)

<mark>Here is where you edit and create the content of your R Markdown. A R Markdown has three main components: the </mark><mark>**Prelude**</mark><mark>, the </mark><mark>**Chunk**</mark><mark>, and the </mark><mark>**Non-chunk (in-line comment)**</mark><mark>, which are labeled in the above image for reference.</mark>

### Prelude:

In the Prelude, you specify settings and headers for your R Markdown. Some headers you can specify include the title, author, and date. The main setting you may alter is the **output** setting, which determines which file types are used when creating your document. You can specify multiple file types, or leave it as the single type you chose when creating your Markdown (HTML in the above example).

### Chunk:

A chunk is a specially marked part of your Markdown document where you place R code to have run.<mark> You will generally have multiple chunks throughout your Markdown which represent specific components of your analysis. </mark>

You can quickly insert chunks into your file with

-   The keyboard shortcut **Ctrl + Alt + I** (OS X: **Cmd + Option + I**)
-   The Green `**+C**`\*\* \*\*Add Chunk command in the editor toolbar:

![image.png](media_R%20&%20RStudio%20QuickStart%20Guide/64bfd3c6-ef45-45a8-8095-cea7259755d5_image.png)

-   or by typing the chunk delimiters \`\`\``{r}` and \`\`\`\`\`.

When you create your Markdown file and turn it into a document, these chunks are run in order and any output from them is shown in the document. A chunk is marked using {r name} to start, as in the following example:

![media_R%20&%20RStudio%20QuickStart%20Guide/R_Chunk.PNG](media_R%20&%20RStudio%20QuickStart%20Guide/R_Chunk.PNG)

You can see that the chunk is shaded in gray and adds in a few icons on the upper right of this shaded space.\*\* \*\*

**A chunk has a few components.**

1.  First, you must name your chunk, which allows you to easily refer to what the code in the chunk does and to facilitate the organization of your document. In the above example, “name” was used as the chunk’s name. ⚠️<mark> Note that each chunk must have a different name or else you will receive an error when the R Markdown file is compiled. </mark><mark>⚠️</mark>
2.  You can also specify a number of options for your chunk inside {r …}, where each option is placed in … and separated by a comma. Note that the chunk’s name is technically an option, so you must separate it from the other options using a comma. Some common options include:
3.  **echo**=TRUE or FALSE

If TRUE is selected, the actual code in the chunk appears in your document along with the results it produced. If FALSE is selected, the code does not appear and only the output does

1.  **warning**=TRUE or FALSE

If TRUE is selected (is by default), all outputted warnings from the code are included in the document. If FALSE is selected, these wanrings are not included.

1.  **include**=TRUE or FALSE

If TRUE is selected (is by default), the output from the code is included in the document. If FALSE is selected, the code is still run but the output is not included in the document. This can be useful if you use certain calculations from this chunk in later chunks and the actual output from this chunk is not of interest.

### Non-Chunk (in-line comment)

> The white space outside of your Prelude is where you place the non-R code components of your document. This space largely works like a Word document; you can place text, images, tables, etc. inside of it. This combination of R code, its results, and the Word document-like capabilities is what allows you to create a comprehensive report for your analysis within a single file. You can also format the text which appears in this space.

## Knit 📋 :

![image.png](media_R%20&%20RStudio%20QuickStart%20Guide/00c666f2-1d06-4aa7-b932-3e824a7fb936_image.png)

With your R Markdown file open in **R studio**, you create the corresponding document using the **Knit** button at the top. This will compile your **R Markdown** into the document file types that you specified in the Prelude. You will see the progress of the compilation as well as any errors or other messages created during the compilation process in the lower left-hand window of **R Studio**, in the **R Markdown** tab. Using Knit will be the best way of understand the capabilities of** R Markdown**, as well as how to use them.

* * *

<u>Here are some important resources when you are ready to jump into Lab 1</u> 📚📑📙

-   "Appendix A" in the book _Probability: With Applications and R_
-   [**An Introduction to R**](https://cran.r-project.org/doc/manuals/r-release/R-intro.html)
-   Cheat Sheets below ⬇️<mark> (double click to view & download)</mark>

# ✅ When you're ready

![RCheatSheet.png](media_R%20&%20RStudio%20QuickStart%20Guide/RCheatSheet.png)

          
