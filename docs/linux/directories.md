# How to navigate in the Linux's directory system

## Listing

    ls
    ls .
    ls /directory

## Navigating

    cd /directory/sub_directory
    cd ..

Return to

    cd ~

## Copy, rename and moving

Basic of copying.

    cp [additional_option] source_file target_file

Additional options

    –v  verbose: shows the progress of multiple copied files
    –p  preserve: keeps the same attributes, like creation date and file permissions
    –f  force: force the copy by deleting an existing file first
    –i  interactive: prompts for confirmation, highly advised
    –R recursive: copies all files and subfolders in a directory
    –u update: copy only if source is newer than destination

To copy multiples files:

    cp my_file.txt my_file_2_.txt my_file_3_.txt /newer_directory

Or we can use the wildcard `*`

    cp /pictures/*.jpg /archive/pictures

To copy files among directories:

    cp directory_one/my_file.txt directory_two/
    cp directory_one/my_file.txt directory_two/rename_file.txt

To copy all the subdiretories and files

    cp -R /directory /newer_directory

Another option is to use the command `rsync` to copy files and diretories.

To move (or rename) files without copying:

    mv my_file.txt renamed_file.txt

## Removing

    rm