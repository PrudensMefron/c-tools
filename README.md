# This is a simple script with tools for C/C++ development conveniency.
The current `c-setup` file is a CLI script who can be used to easily setup `C` or `C++` projects, configure build systems, clang formatter and tidy, and basic folder structure.

It also provides a option for a `C/C++` project, in wich the main entry file will be a `main.cpp`.

The script uses mine own personal formater prefferences, so the `C` formating would be GNUish and the C++ would be Allman. You can easily modify this on the script file.

## Instalation
You will need:
- Git
- Bash shell

That works for Linux:
1. First, clone the repo with git:
```Bash
git clone https://github.com/PrudensMefron/c-tools.git c-tools
```

2. Second, you grant execution permission to the script:
```Bash
cd c-tools
chmod +x c-setup
```
3. Third, create a symlink of the the script to the bin folder:
```Bash
# Move to a bin folder
sudo ln -s "$(pwd)/c-setup" /usr/bin/c-setup
```

And then you can just type `c-setup my-project-name` to setup your project inside the dir `my-project-name/`.

## Uninstallation
Just remove the symlink first:
```Bash
sudo unlink /usr/bin/c-setup
```

And then delete the repo dir you cloned during installation.

## Suggestions or contributions?
Feel free to open an Issue or Pull Request.

Hope you find it useful.
