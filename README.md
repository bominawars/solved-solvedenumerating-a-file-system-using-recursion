Download Link: https://assignmentchef.com/product/solved-solvedenumerating-a-file-system-using-recursion
<br>
Module 4 Homework: Enumerating a File System Using RecursionFor this programming assignment you will write a recursive algorithm to display the contents of a directoryin a computer’s file system. You will also get a little experience using the API documentation forseveral components of the JDK library, including the File class. Additionally, you will get some exposureto a graphical user interface (GUI), which you may or may not have had in your previous Java work.The Explorer program that serves as the default file system browser for the Windows XP operating systemallows you to see the first-level contents of a given folder. It does not allow you to see the contents of anynested subfolders—you have to click on each subfolder, one at a time, to see the contents of these folders.Suppose you wanted to see the entire contents of a given folder; i.e., not just the first-level files andsubfolders, but everything that is contained in all the nested subfolders, regardless of how many nestedsubfolders there are.

You could write an algorithm that iterates through all the subfolders using a loop, but since you have knowway of knowing beforehand how many levels of nested subfolders there are, implementing an iterativealgorithm to do this would be tricky. This problem is perfectly suited for a recursive algorithm, however.Each subfolder constitutes a problem that is similar to the initial problem (i.e., the root-level folder), onlysmaller. Recursion can theoretically (though not practically) handle an infinite amount of nesting.Your goal for this assignment is to implement a recursive method that will enumerate the contents of achosen folder in a computer’s file system, and display the following information about all the files and subfoldersin the chosen folder:

1. absolute path name (i.e., the path name beginning with the drive letter or network share;e.g.: “C:My DocumentsmyFile.txt”)2. size, in kilobytes3. type (file or folder)4. the date and time on which the file or folder was last modifiedDownload FilesDownload the DirectoryLister.zip file. It contains 3 files you will need to use for this assignment:1. Driver.java2. GUI.java3. DirectoryLister.java

The only file you will need to modify for this assignment will be DirectoryLister.java. You will not need tocreate any additional classes for this assignment. You should be able to compile the project as it is. It willallow you to select a directory, but it won’t do anything else.How the Program Should WorkA screen capture of how the user interface appears when the program is first launched is shown below.This is what you should see if you compile and run the provided source files as they are, with no modifications.Clicking the “Browse…” button will bring up a JFileChooser dialog where you can select a folder fromthe file system. Once you have selected a folder, a table will be generated showing the name, size, type,and date last modified for every file and folder in the selected folder, as well as all nested subfolders. Withthe files you download in the directoryLister.zip file, selecting a folder will do nothing. You must completethe implementation to process the selected folder and display all the required information.

***********Please see screen shot***********

What you need to doAll you need to do for this assignment is complete the following 2 methods of the DirectoryListerclass. The method declarations have been provided for you. All you need to do is provide the implementations.You will need to understand how the GUI works, though in order to get your results to displayproperly.

/*** Show the directory listing.* An error message is displayed if basePath does not represent a valid directory.** @param basePath the absolute path of a directory in the file system.*/public void showDirectoryContents(String basePath){// TODO}/*** Recursive method to enumerate the contents of a directory.** @param f directory to enumerate*/private void enumerateDirectory(File f){// TODO}

The value returned by the JFileChooser dialog is a string representing the absolute path of the selectedfolder. There are a few exceptional situations you should try to make sure are handled by validating theinput returned from the JFileChooser dialog:1. If the user clicks the “Cancel” button or the “Close” button on the JFileChooser dialog,without choosing a folder.2. If the user enters an invalid folder path directly into the textbox on the JFileChooserdialog, or modifies a path selected by clicking on a folder in the dialog’s file/folder view.3. It is possible, albeit , for a chosen folder to exist at the time of choosing it in theJFileChooser dialog, but not exist after the user clicks the “Open” button on the dialog.An example of how this could happen would be a concurrently running process that happensto delete or rename the chosen folder in between the time the folder was chosen, and the“Open” button is clicked.You may find that setting up a try-catch block to handle these situations is helpful. In any event, theprogram should not exit or crash when one of these situations occurs, but it should behave appropriately;e.g., by displaying a message using a JOptionPane dialog to inform the user what has occurred.If the chosen directory is valid, the enumerateDirectory method should be called, which should recursivelyenumerate the contents of the chosen folder. To get full credit for this part of the assignment, yourenumerateDirectory method must be recursive, and it should update the display with all the required information. You can use the updateListing method of the GUI class to do this. The argument for thismethod is a reference to a File object that represents the file or folder currently being processed.Relevant Classes in the Java API

• File• JOptionPane

The File class is an abstract representation of either a file or a folder in the file system. To create a Fileobject, you will probably want to use the constructor, File (String pathname), since this is the type ofinformation returned when the initial folder is chosen from the JFileChooser dialog. The File class providesmany useful methods, including ones to retrieve all the information you need to display for each fileor folder. I will leave it to you to read through the API docs to figure out which methods you need.The JOptionPane class is used to display a simple modal dialog box containing a message. It can alsodisplay things like warning icons to indicate the seriousness of the message. You don’t need to create aninstance of the JOptionPane class in order to use it. You can use one of the many static methods the JOptionPaneclass provides. For example, the following statement will display an error message that reads,“The specified filename is invalid!”:JOptionPane.showMessageDialog(null, “The specified filename is invalid! “, “Error”,JOptionPane.ERROR_MESSAGE);The first argument here refers to the parent component of the JOptionPane. Since we’re calling one of thestatic methods, we don’t need to specify a parent component, so we pass a null value. The second argumentis the error text that will be displayed in the main part of the message dialog. The third argumentspecifies the text that should appear in the title bar of the dialog. Finally, the fourth argument specifieswhich type of icon should be displayed along with the error message (warning, information, or error).Hints

1. Don’t make this project harder than it really is! I’ve given you a week to finish it, but youdon’t really have to do that much work—you only need to implement the two methods I’veindicated.2. You should not need to create any additional methods or classes. The user interface is builtfor you, so you do not have to create any additional UI components. You will need to understandhow the user interface works, though, so you can make your implementation communicatewith it.3. Your showDirectoryContents method needs to call your enumerateDirectory method, whichrequires a File object as a parameter, so at some point you will need to create a File objectin your showDirectoryContents method.4. Your enumerateDirectory method must be recursive, so you will need to determine what thebase case(s) are, and what the recursive case(s) are. If you think about how a computer’sfile system is structured, you should be able to figure this out pretty quickly.5. Test your program before you submit it! Make sure your test cases cover all the possiblescenarios:a. a non-existent folder (you can do this by typing an invalid path in the text box of theinterface, instead of choosing an existing directory)b. an empty folderc. a folder containing only one filed. a folder containing only one subfoldere. a folder containing multiple files (but no subfolders)f. a folder containing multiple, non-nested subfolders (but no files)g. a folder containing both files and subfolders (all folders are non-nested)h. a folder containing multiple, nested subfolders (but no files)i. a folder containing an arbitrary mix of files and subfolders (some nested, some nonnested)6. Don’t worry about exhaustively testing your program on a folder containg a huge number offiles and subfolders. While recursion is elegant, it can quickly eat up all the stack space inyour computer’s memory, and if this happens the program will crash. Test your program onfolders with moderate numbers of files and subfolders, and assume that if your programworks on those folders, it will work for all folders.7. If you have questions, please ask!

Rubric:showDirectoryContents methodcreates File object 1 pt.handles errors using JOptionPane 1 pt.calls enumerateDirectory method 3 pts.enumerateDirectory methoduses recursion, and recursion works properly 8 pts.displays absolute paths 2 pts.displays file/folder sizes 2 pts.displays type (file or folder) 2 pts.displays date last modified 2 pts.Testsnon-existent directory 1 pt.empty directory 1 pt.directory containing only one file 1 pt.directory containing only one subdirectory 1 pt.directory containing multiple files (but no subdirectories)1 pt.directory containing multiple, non-nested subdirectories(but no files)1 pt.directory containing both files and subdirectories(all directories are non-nested)1 pt.directory containing multiple, nested subdirectories(but no files)1 pt.directory containing an arbitrary mix of files andsubdirectories (some nested, some non-nested)1 pt.Total: 30 pointsWhat to submit:

A .zip file containing your Driver.java, GUI.java and DirectoryLister.java source files. Do not send meJCreator project or workspace files (the files ending in .jcp, .jcw, and .jcu), or your compiled.class files.