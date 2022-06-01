# UNDERSTANDING AWK-COMMAND

### Abstract

   Awk is an extremely versatile programming language for working on files. We will discuss some basics about Awk.
   
### Description
   
   #### What is Awk ?
      Awk is a scripting language used for manipulating data and generating reports. The awk command programming 
      language requires no compiling and allows the user to use variables, numeric functions, string functions,
      and logical operators.
   
   #### Why to learn Awk ?
      Awk is a utility that enables a programmer to write tiny but effective programs in the form of statements 
      that define text patterns that are to be searched for in each line of a document and the action that is to 
      be taken. when a match is found within a line. Awk is mostly used for pattern scanning and processing. 
      It searches one or more files to see if they contain lines that matches with the specified patterns and 
      then perform the associated  actions.
   
   #### What can we do with Awk ?
      
      1. AWK Operations: 
         (a) Scans a file line by line 
         (b) Splits each input line into fields 
         (c) Compares input line/fields to pattern 
         (d) Performs action(s) on matched lines 

      2. Useful For: 
         (a) Transform data files 
         (b) Produce formatted reports 

      3. Programming Constructs: 
         (a) Format output lines 
         (b) Arithmetic and string operations 
         (c) Conditionals and loops
         
   #### Syntax :
      awk options 'selection _criteria {action }' input-file > output-file
      
      ##### Options :
         -f program-file : Reads the AWK program source from the file 
                  program-file, instead of from the 
                  first command line argument.
         -F fs            : Use fs for the input field separator
   
      1. Default behavior of Awk: By default Awk prints every line of data from the specified file.
         $ awk '{print}' employee.txt
      2. Print the lines which match the given pattern.
         $ awk '/manager/ {print}' employee.txt
      3. Splitting a Line Into Fields : For each record i.e line, the awk command splits the record delimited by 
         whitespace character by default and stores it in the $n variables. If the line has 4 words, it will be 
         stored in $1, $2, $3 and $4 respectively. Also, $0 represents the whole line.
         $ awk '{print $1,$4}' employee.txt
         
   #### Built-In Variables In Awk

      Awk’s built-in variables include the field variables—$1, $2, $3, and so on ($0 is the entire line) — that 
      break a line of text into individual words or pieces called fields. 

      NR: NR command keeps a current count of the number of input records. Remember that records are usually lines.
          Awk command performs the pattern/action statements once for each record in a file. 
      NF: NF command keeps a count of the number of fields within the current input record. 
      FS: FS command contains the field separator character which is used to divide fields on the input line.
          The default is “white space” .
      
      Use of NR built-in variables:
         awk '{print NR,$0}' employee.txt
         # This command will display line mumber
         
      Use of NF built-in variables 
         awk '{print $1,$NF}' employee.txt
         # This command will display last field
         
      Another use of NR built-in variables  
         awk 'NR==3, NR==6 {print NR,$0}' employee.txt
         # This command will display line from 3 to 6
       
      To find the length of the longest line present in the file:
         awk '{ if (length($0) > max) max = length($0) } END { print max }' geeksforgeeks.txt
         
      To print the squares of first numbers from 1 to n say 6:  
         awk 'BEGIN { for(i=1;i<=6;i++) print "square of", i, "is",i*i; }' 
         square of 1 is 1
         square of 2 is 4
         square of 3 is 9
         square of 4 is 16
         square of 5 is 25
         square of 6 is 36
      
      To find all entries who contains Bangalore as substring in given column and for calculating the sum of given column:
         awk -F, 'index($3,"Bangalore") {print $18}' | awk '{s+=$1} END {print s}'
         # This command will print all runs made by rcb in all seasons

### Conclusion
   
   Awk is very useful command for working with tabular data, and for creating the reports from tabular data. We can split, 
   fetch and process the data from different columns using different features and functions provided in Awk.

### Reference
   
   * https://www.geeksforgeeks.org/awk-command-unixlinux-examples/#:~:text=Awk%20is%20a%20utility%20that,for%20pattern%20scanning%20and%20processing.
   
   * https://www.youtube.com/watch?v=fuj62vuHq5s
   
   * https://www.youtube.com/watch?v=1l8n3TRK-34
   
   * https://www.youtube.com/watch?v=d-HJmXNIvfc
