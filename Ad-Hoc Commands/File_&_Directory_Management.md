# 📁 File & Directory Management

### 1. Creating a Directory

```
  ansible all -m file -a "path=/tmp/mydir state=directory"
```
> **Note:** -a "path=/tmp/mydir state=directory" provides the arguments to the file module, where path is the directory path and **state=directory** indicates that the directory should be created.</br>

### 2. Removing a Directory

```
  ansible all -m file -a "path=/tmp/mydir state=absent"
```

### 3. Creating a File

```
  ansible all -m file -a "path=/tmp/myfile.txt state=touch"

  # create a file with content
  ansible all -m copy -a "dest=/tmp/myfile.txt content='This is the content of the file.'"
```

### 4. Deleting a File

```
  ansible all -m file -a "path=/tmp/myfile state=absent"
```

### 5. Copying a File

```
  ansible all -m copy -a "src=/local/path/to/file dest=/remote/path/to/file"
```

### 6. Changing a File Permissions

```
  ansible all -m file -a "path=/tmp/myfile mode=0644"
```

### 7. Changing a File Content

```
  ansible all -m copy -a "dest=/tmp/myfile content='This is the new content.'"
```

### 8. Appending Text to a File

```
  ansible all -m lineinfile -a "path=/tmp/myfile line='This is a new line to append.' state=present"
```

### 9. Moving/Renaming a File

```
  ansible all -m shell -a "mv /tmp/oldname /tmp/newname"
```

---
