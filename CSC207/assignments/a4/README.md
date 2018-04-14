
[code review resource](http://www.developer.com/tech/article.php/3579756)


Overall comment:

The class FileNode has quite many redundant parameters that is already
accessible from build in Java class File; perhaps consider extending File Class
instead to avoid redundant code. I feel that building tree should not be within
a FileNode class as it is a general static method that is perhaps better be
along on its own. The code lacks proper Javadoc and should be improved upon in
this respect. Some of the developer's comment seems to be more of a question
then an instruction. Some of the commented out code not used should be deleted.
Conceptionally, a PHOTO filetype could perhaps be replaced with a FileFilter
class that does performs a very similar function. Overall, the class did
successfully implemented what a FileNode is about so this is good.


Comments below are structured in this format
line#: comments
---------------
0: A comment on FileType. I think it is not the most wise to group PHOTO
    alongside with FILE and DIRECTORY, which are complement of each other.
    Think about how a PHOTO is still a FILE !

40: should comment capitalized enum variable instead

60: remember removing redundant //TODO: complete method

62: a CheckedException should be raised to handle the exception in case Child
    selected is either empty or not a DIRECTORY FileType. Perhaps prompt for
    another input

63: perhaps a recursive function that traverses the directory tree would handle
    the task of finding the child, descendent, and so forth


17 & 89 & 99: I would think that a String nom and getter and setter methods for it
    are redundant because we this information is accessible from the variable
    actual_file, which is a Java.io.File class. (i.e. actual_file.getName())


19: Again the FileType type denoting the file type of FileNode is redundant as
    it can be checked using the variable actual_file, which is a Java.io.File
    class. (i.e. actual_file.isFile() and actual_file.isDirectory()).

21 & 117 & 127: Again a FileNode denoting the parent of FileNode is redundant
    for the above reasoning. It is accessible from the variable actual_file
    (i.e. actual_file.getParentFile())

140: addChild requires two parameters whereas just one of them, specifically
    FileNode childNode is sufficient because file name is accessible from
    childNode

157: buildTree is not used anywhere else in the program so consider removing the
    method

157 & 178 & 215 & 282 & 293...: they are classes where proper Javadoc are not
    written. We should documnet Javadoc for every variable/method/class


179: think about cleaning up unused code in final submission

183 & 184 & 185: variable not indicative of / incorrectly imply what they store.
    Consider

186: there is break in java so consider using the default one

189: Consider split the file path based on the dot (.) and use substring method
    to get the last string in order to find the extension. Try not write code
    someone else has already wrote that is perhaps better, exhaustive, and more
    efficient


222: Consider using for(File f: ls) instead as a shorthand

225: This for if statement could largely be eliminated if FileType enum is
    properly set as mentioned previously


282: What the method functions does not match the function name. Consider rename
    to getParentAbsolutePath()...