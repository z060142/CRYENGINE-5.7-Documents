# Accessing Files with CryPak

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306407
- Page ID: 23306407
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > File System > CryPak > Accessing Files with CryPak
- Parent: CryPak

## Content

### Overview

In this tutorial you will learn how file reading and writing works through **CryPak**.

After finishing this tutorial you will be capable of adding new files to your project, reading files from file system and pak archives and writing files to the file system.

### Preparation

Before you can start, you need a file which is going to be added to a pak archive. To keep it simple, create a text file named **ExampleText.txt** and write the following text into it:

Sample was read from pak archive

In the next step, create a new sub-folder called **Examples** inside ** GameSDK** and add the file into it: `<root>\GameSDK\Examples\ExampleText.txt`

Now, make use of 7za.exe which is located in `<root>\Tools` to create a new archive called Examples.pak inside GameSDK. This archive will contain ` Examples\ExampleText.txt` only. Alternatively, you can also use the [Obsolete PAK Manager](/docs/static/engines/cryengine-3/categories/1114113/pages/14290302).

```
..\Tools\7za.exe a -tzip -r -mx0 Examples.pak Examples
```

This tutorial demonstrates two different methods of loading files - either from a pak archive or directly from the file system.

To verify which file is loaded, the example makes use of the content inside the text file. Hence, change the current text inside `<root>\GameSDK\Examples\ExampleText.txt` to something different than before:

Sample was read from file system

Now, there are two different text files with the same destination path - one is stored directly in the file system, the other one is nested in the archive.

**CryPak** is able to find both instances depending on the ** pakPriority**.

The default pakPriority depends on the configuration settings of your build, but it can also manually be changed by assigning **0, 1, 2 or 3** to the cvar ** sys_PakPriority**.

```
enum EPakPriority
{
ePakPriorityFileFirst = 0,
ePakPriorityPakFirst  = 1,
ePakPriorityPakOnly   = 2,
ePakPriorityFileFirstModsOnly = 3,
};
```

About folder priorities
The main reason for adding the new pak file to the **GameSDK** folder in this example is because here it is guaranteed that all pak files are loaded.

**Pak loading order:**

- **GameSDK:** root\GameSDK\*.pak
- **Engine:** root\Engine\
- Engine.pak
- ShaderCache.pak
- ShaderCacheStartup.pak
- Shaders.pak
- ShadersBin.pak
- **Mods:** root\Mods\* MyMod*\GameSDK\*.pak (in case you are running the game with command argument **-mod "MyMod"**)

**Pak search order:**

- **Mods** (in case more than one mod folder has been added, they will be checked in reverse order as being added)
- **Engine**
- **GameSDK**

### Reading Files With CryPak

The module **CrySystem** initializes ** CryPak** and makes sure that pak files can be accessed.

Full-Source information
To be precise, this happens in **CSystem::Init** when the following functions are called:

- **InitFileSystem(startupParams.pGameStartup);**
- **InitFileSystem_LoadEngineFolders();**

This is good because it ensures that pak files can be accessed from the game code at anytime. A good spot to demonstrate that is at the beginning of **CGame::Init** inside ** Game.cpp**.

Let's write some lines of code to read the information of **ExampleText.txt**, which has been created above.

```
char* fileContent = NULL;
if (!ReadFromExampleFile(&fileContent))
{
CryWarning(VALIDATOR_MODULE_SYSTEM, VALIDATOR_WARNING, "ReadFromExampleFile() failed");
}
else
{
CryLogAlways("ExampleText contains %s", fileContent);
[...] // this line will be added later on
}
```

- **fileContent** is the space in memory which contains the message read from inside ** ExampleText.txt** if ** ReadFromExampleFile()** was successful.
- **ReadFromExampleFile()** is not implemented yet, but will handle reading the file and its content. Returns ** true** in case of success, otherwise ** false**.

```
bool ReadFromExampleFile(char** fileContent)
{
CCryFile file;
size_t fileSize = 0;
const char* filename = "examples/exampletext.txt";

[...]
}
```

- **file** of type ** CCryFile** can make use of ** CryPak** to access files directly from the files system or from inside a pak archive.
- **fileSize** is going to be used to define the end of the message since reading does not end by a null character '\0'.
- **filename** - which is case-insensitive - specifies the path of the file to be loaded.

```
char str[1024];
if (!file.Open(filename, "r"))
{
sprintf(str, "Can't open file, (%s)", filename);
CryWarning(VALIDATOR_MODULE_SYSTEM, VALIDATOR_WARNING, "%s", str);
return false;
}
```

- **Open()** will invoke that ** CryPak** searches the file specified by ** filename**.
- **File access mode "r"** specifies that a plain text file is going to be read. In case of reading a binary file use **"rb"**.

```
fileSize = file.GetLength();
if (fileSize <= 0)
{
sprintf(str, "File is empty, (%s)", filename);
CryWarning(VALIDATOR_MODULE_SYSTEM, VALIDATOR_WARNING, "%s", str);
return false;
}

char* content = new char[fileSize + 1];
content[fileSize] = '\0';

if (file.ReadRaw(content, fileSize) != fileSize)
{
delete[] content;
sprintf(str, "Can't read file, (%s)", filename);
CryWarning(VALIDATOR_MODULE_SYSTEM, VALIDATOR_WARNING, "%s", str);
return false;
}
```

- **content** is the local pointer to a char array in memory which gets initialized by the length returned by ** GetLength()** and an extra null character.
- **ReadRaw** fills **content** with the information read from the text file. In case of a failure, the allocated memory of **content** is freed.

```
file.Close();

*fileContent = content;
return true;
```

Finally, we close the file handle, make sure that the locally created data can be used outside the function by setting the **fileContent** pointer and **return true** since the reading was successful.

In our example the caller of **ReadFromExampleFile()** is responsible for freeing the heap memory which has been allocated to store the data from the text file. Add ** delete[] fileContent;** after the info has been used.

If you run the game now, you can check if reading worked by checking the **Game.log**.

#### Complete code (file reading)

```
char* fileContent = NULL;
if (!ReadFromExampleFile(&fileContent))
{
CryWarning(VALIDATOR_MODULE_SYSTEM, VALIDATOR_WARNING, "ReadFromExampleFile() failed");
}
else
{
CryLogAlways("ExampleText contains %s", fileContent);
delete[] fileContent;
}
```

```
bool ReadFromExampleFile(char** fileContent)
{
CCryFile file;
size_t fileSize = 0;
const char* filename = "examples/exampletext.txt";

char str[1024];
if (!file.Open(filename, "r"))
{
sprintf(str, "Can't open file, (%s)", filename);
CryWarning(VALIDATOR_MODULE_SYSTEM, VALIDATOR_WARNING, "%s", str);
return false;
}

fileSize = file.GetLength();
if (fileSize <= 0)
{
sprintf(str, "File is empty, (%s)", filename);
CryWarning(VALIDATOR_MODULE_SYSTEM, VALIDATOR_WARNING, "%s", str);
return false;
}

char* content = new char[fileSize + 1];
content[fileSize] = '\0';

if (file.ReadRaw(content, fileSize) != fileSize)
{
delete[] content;
sprintf(str, "Can't read file, (%s)", filename);
CryWarning(VALIDATOR_MODULE_SYSTEM, VALIDATOR_WARNING, "%s", str);
return false;
}

file.Close();

*fileContent = content;
return true;
}
```

### Writing Files With CryPak

**CCryFile::Write** always writes to the file system and never to pak archives. If you want to write files to a compressed or uncompressed archives is please skip this chapter.

Writing a file is similar as reading. First, let's call a function which will be implemented in the next step.

```
char* newContent = "File has been modified";
bool appendToFile = false;
if (!WriteToExampleFile(newContent, strlen(newContent), appendToFile))
{
CryWarning(VALIDATOR_MODULE_SYSTEM, VALIDATOR_WARNING, "WriteToExampleFile() failed");
}
else
{
CryLogAlways("Text has been written to file, %s", newContent);
}
```

- **WriteToExampleFile()** is going to do the writing logic and takes the following three parameters
- **newContent** contains the text which will be written to ** ExampleText.txt** on the file system.
- **strlen(newContent)** returns size of ** newContent**. Actually the number of bytes which shall be written.
- **appendToFile** specifies if ** newContent** shall be added (** true**) to the already existing one or if the file shall be wiped out first (** false**).

Respectively to file reading, the framework of **WriteToExampleFile()** looks like the following:

```
bool WriteToExampleFile(char* text, int bytes, bool appendToFile)
{
CCryFile file;
const char* filename = "examples/exampletext.txt";

assert(bytes > 0);
char* mode = NULL;
if (appendToFile)
mode = "a";
else
mode = "w";

char str[1024];
if (!file.Open(filename, mode))
{
sprintf(str, "Can't open file, (%s)", filename);
CryWarning(VALIDATOR_MODULE_SYSTEM, VALIDATOR_WARNING, "%s", str);
return false;
}

[...]

file.Close();
return true;
}
```

- **mode** specifies if the text shall be appended to the existing file or if it shall be wiped out first.**"w"** = write to clean file, **"a"** = append to existing file.

```
int bytesWritten = file.Write(text, bytes);
assert(bytesWritten == bytes);

if (bytesWritten == 0)
{
sprintf(str, "Can't write to file, (%s)", filename);
CryWarning(VALIDATOR_MODULE_SYSTEM, VALIDATOR_WARNING, "%s", str);
return false;
}
```

- **bytesWritten** tells how many bytes actually have been written by calling the ** Write()** function.

### Modifying Paks With CryArchive

The following tutorial explains how new pak files are generated at runtime. Furthermore, the example shows how files are added, updated and removed from the archive.

In the example code we are intentionally using the **USER** folder instead of ** GameSDK**. Pak files inside the USER folder are not loaded by default at startup whereas all the *.pak files inside GameSDK will be loaded and thus marked as **Read-Only**.

```
string pakFilename = PathUtil::AddSlash("%USER%") + "Examples.pak";
const char* filename = "Examples/ExampleText.txt";
char* text = "File has been modified by CryArchive";
unsigned length = strlen(text);

_smart_ptr<ICryArchive> pCryArchive = gEnv->pCryPak->OpenArchive(pakFilename.c_str(), ICryArchive::FLAGS_RELATIVE_PATHS_ONLY | ICryArchive::FLAGS_CREATE_NEW);
if (pCryArchive)
{
pCryArchive->UpdateFile(filename, text, length, ICryArchive::METHOD_STORE, 0);
}
```

- **UpdateFile()** modifies an existing file inside the pak archive or creates a new one if it does not exist.
- **ICryArchive::FLAGS_CREATE_NEW** will make sure the pak file is created from scratch every run. If you want to add files later on, you have to remove this flag.
- Removing files and folder from an archive is straightforward by using one of the commands **RemoveFile()**, ** RemoveDir()** or ** RemoveAll()** instead of ** UpdateFile()**.

[Preparation](#preparation)[Reading Files With CryPak](#reading-files-with-crypak)[Writing Files With CryPak](#writing-files-with-crypak)[Modifying Paks With CryArchive](#modifying-paks-with-cryarchive)
