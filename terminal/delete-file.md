In linux system, you can't delete a folder which start with '-' in folder name
because the `rm -rf <folder-name>` will be `rm -rf -folder_name` and an error
will be respond because of miss understanding arguments -folder_name.

In this case, you have to type this command:

`rm -rf -- *`

`--` means that you ignore arguments after it.
This command is useful when I have to delete rails .cache files manualy.
