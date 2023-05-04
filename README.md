Download Link: https://assignmentchef.com/product/solved-cse-325-computer-project-3
<br>
<h1>Assignment Overview</h1>

<strong> </strong>

This assignment focuses on system-level programming in a Linux environment.  You will design and implement the C++ program which copies the contents of one file to another file, as described below.




It is worth 40 points (4% of course grade) and must be completed no later than 11:59 PM on Thursday, 1/30.




<h1>Assignment Deliverables</h1>




The deliverables for this assignment are the following files:




<strong>proj03.makefile</strong> – the makefile which produces <strong>proj03</strong> <strong>proj03.student.c</strong> – the source code file for your solution




Be sure to use the specified file names and to submit your files for grading via the CSE Handin system before the project deadline.




<h1>Assignment Specifications</h1>




<ol>

 <li>The purpose of the program is to copy the contents of one file (the source file) to another file (the destination file). The user will interact with the program through command-line arguments.</li>

</ol>




<ol>

 <li>The program will process the command line arguments from left to right.</li>

</ol>




<ol>

 <li>If an argument begins with the character ‘-‘, it will be processed as an option which controls the behavior of the program. Valid options are “-b”, “-t” and “-a” (defined below).</li>

</ol>




<ol>

 <li>If an argument does not begin with the character ‘-‘, it will be processed as a file name. Exactly two file names must be provided by the user, with the source file listed first and the destination file listed second.</li>

</ol>




<ol start="2">

 <li>The program will use the following functions to manage the files:</li>

</ol>




<strong>int open( const char *pathname, int flags, mode_t mode ); int close( int fd ); </strong>




<ol start="3">

 <li>The program will use the following functions to perform input and output operations on the files:</li>

</ol>




<strong>ssize_t read( int fd, void *buf, size_t count ); ssize_t write( int fd, const void *buf, size_t count );</strong>




The size of the buffers associated with those functions will be determined by the “-b” option.




<ol start="4">

 <li>The program will recognize the following options:</li>

</ol>




<ol>

 <li>The option “-b” will be followed by a separate command-line argument which indicates the size of the buffer (in bytes) to be used during the processing. The default buffer size will be 256 bytes.</li>

</ol>

<strong> </strong>

<ol>

 <li>The option “-t” will cause the program to truncate an existing destination file, and then copy the source file to the destination file.</li>

</ol>




<ol>

 <li>The option “-a” will cause the program to append the source file to the end of an existing destination file.</li>

</ol>




<ol>

 <li>If neither option “-t” nor option “-a” is selected by the user, the program will not modify a destination file which already exists when the program begins execution.</li>

</ol>




<ol>

 <li>The options “-t”, and “-a” will have no impact on a destination file which does not exist when the program begins execution (the program will always attempt to create a destination file which does not exist).</li>

</ol>




<ol start="5">

 <li>The program will minimize the number of calls to function “write”, within the constraints imposed by the size of the buffer.</li>

</ol>




<ol start="6">

 <li>The program will include appropriate logic to handle exceptional cases and errors.</li>

</ol>




<h1>Assignment Notes</h1>




<ol>

 <li>As stated above, your source code file will be named “proj03.student.c”; that source code file may contain C or C++ statements.</li>

</ol>




<ol start="2">

 <li>You must use “g++” to translate your source code file in the CSE Linux environment.</li>

</ol>




<ol start="3">

 <li>As stated above, the command-line arguments will be processed from left to right. For example, consider the following command line:</li>

</ol>




<strong>proj03 fileA -a fileB –b 128 </strong>




The program will use a buffer size of 128 bytes, and will append the contents of the source file (“fileA”) to the end of the destination file (“fileB”).




<ol start="4">

 <li>Each command-line argument is constructed as a low-level character string (array of type “char”, with a terminating null byte). If you prefer to process a command-line argument as a C++ string class object, you should consider converting the low-level character string.  For example:</li>

</ol>




<strong>string prog = string( argv[0] ); </strong>




<ol start="5">

 <li>Information about the four system calls you will use for the project is available in section 2 of the “man” utility:</li>

</ol>




<strong>man 2 open man 2 close man 2 read man 2 write </strong>

<strong> </strong>

<ol start="6">

 <li>The third argument to function “open” allows you to control the file permissions associated with a file which is being created. You would be wise to use “S_IRUSR | S_IWUSR” (or the equivalent) so that you can examine the contents of any new files which your program creates.  Otherwise, you will have to use the “chmod” command for each file to change the file permissions for each new file.</li>

</ol>


