https://www.fossil-scm.org/home/doc/trunk/www/whyusefossil.wiki

Benefits of Version Control

Immutable file and version identification

Simplified and unambiguous communication between developers
Detect accidental or surreptitious changes
Locate the origin of discovered files
Parallel development

Multiple developers on the same project
Single developer with multiple subprojects
Experimental features do not contaminate the main line
Development/Testing/Release branches
Incorporate external changes into the baseline
Historical record

Exactly reconstruct historical builds
Locate when and by whom faults were injected
Find when and why content was added or removed
Team members see the big picture
Research the history of project features or subsystems
Copyright and patent documentation
Regulatory compliance
Automatic replication and backup

Everyone always has the latest code
Failed disk-drives cause no loss of work
Avoid wasting time doing manual file copying
Avoid human errors during manual backups
Definitions

Project → a collection of computer files that serve some common purpose. Often the project is a software application and the individual files are source code together with makefiles, scripts, and "README.txt" files. Other examples of projects include books or manuals in which each chapter or section is held in a separate file.

Projects change and evolve. The whole purpose of version control is to track and manage that evolution.

Most projects contain many files, but it is possible to have a project consisting of just a single file.

Fossil requires that all the files for a project must be collected into a single directory hierarchy - a single folder possibly with layers of subfolders. Fossil is not a good choice for managing a project that has files scattered hither and yon all over the disk. In other words, Fossil only works for projects where the files are laid out such that they can be archived into a ZIP file or tarball.

Repository → (also called "repo") a single file that contains all historical versions of all files in a project. A repo is similar to a ZIP archive in that it is a single file that stores compressed versions of many other files. Files can be extracted from the repo and new files can be added to the repo, just as with a ZIP archive. But a repo has other capabilities above and beyond what a ZIP archive can do.

Fossil does not care what you name your repository files, though names ending with ".fossil" are recommended.

A single project typically has multiple, redundant repositories on separate machines.

All repositories stay synchronized with one another by exchanging information via HTTP or SSH.

All repos for a single project redundantly store all information about that project. So if any one repo is lost due to a disk crash, all content is preserved in the surviving repos.

The usual arrangement is one repository per user. And since most users these days have their own computer, that means one repository per computer. But this is not a requirement. It is ok to have multiple copies of the same repository on the same computer.

Fossil works fine with just a single copy of the repository. But in that case there is no redundancy. If that one repository file is lost due to a hardware malfunction, then there is no way to recover the project.

Best practice is to keep all repositories for a user in a single folder. Folders such as "~/Fossils" or "%USERPROFILE%\Fossils" are recommended. Fossil itself does not care where the repositories are stored. Nor does Fossil require repositories to be kept in the same folder. But it is easier to organize your work if all repositories are kept in the same place.

Check-out → a set of files that have been extracted from a repository and that represent a particular version or snapshot of the project.

Check-outs must be on the same computer as the repository from which they are extracted. This is just like with a ZIP archive: one must have the ZIP archive file on the local machine before extracting files from ZIP archive.

There can be multiple check-outs (in different folders) from the same repository.

The repository must be on the same computer as the check-out, but the relative locations of the repo and the check-out are arbitrary. The repository may be located inside the folder holding the check-out, but it certainly does not have to be and usually is not.

A special file exists in every check-out that tells Fossil from which repository the check-out was extracted, and which version of the project the check-out represents. This is the ".fslckout" file on unix systems or the "_FOSSIL_" file on Windows.

Check-in → another name for a particular version of the project. A check-in is a collection of files inside of a repository that represent a snapshot of the project for an instant in time. Check-ins exist only inside of the repository. This contrasts with a check-out which is a collection of files outside of the repository.

Every check-out knows the check-in from which it was derived. But check-outs might have been edited and so might not exactly match their associated check-in.

Check-ins are immutable. They can never be changed. But check-outs are collections of ordinary files on disk. The files of a check-out can be edited just like any other file.

A check-in can be thought of as an historical snapshot of a check-out.

"Check-in", "version", "snapshot", and "revision" are synonyms.

When used as a noun, the word "commit" is another synonym for "check-in". When used as a verb, the word "commit" means to create a new check-in.





Alternate Implementations
Though there is one Python implementation which is by far the most popular, there are some alternate implementations which are of particular interest to different audiences.

Known implementations include:

###CPython
This is the original and most-maintained implementation of Python, written in C. New language features generally appear here first.

###Jython
Python implemented in Java. This implementation can be used as a scripting language for Java applications, or can be used to create applications using the Java class libraries. It is also often used to create tests for Java libraries. More information can be found at the Jython website.

###Python for .NET
This implementation actually uses the CPython implementation, but is a managed .NET application and makes .NET libraries available. It was created by Brian Lloyd. For more information, see the Python for .NET home page.

###IronPython
An alternate Python for .NET. Unlike Python.NET, this is a complete Python implementation that generates IL, and compiles Python code directly to .NET assemblies. It was created by Jim Hugunin, the original creator of Jython. For more information, see the IronPython website.

###PyPy
An implementation of Python written completely in Python. It supports several advanced features not found in other implementations like stackless support and a Just in Time compiler. One of the goals of the project is to encourage experimentation with the language itself by making it easier to modify the interpreter (since it is written in Python). Additional information is available on the PyPy project’s home page.
Each of these implementations varies in some way from the language as documented in this manual, or introduces specific information beyond what’s covered in the standard Python documentation. Please refer to the implementation-specific documentation to determine what else you need to know about the specific implementation you’re using.
