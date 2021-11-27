# How to use ssh

## Connecting

    ssh -p number user@remote_adress

## Copy directories and files between local and remote server

Use `scp` command

    scp [OPTION] [user@]SRC_HOST:]file1 [user@]DEST_HOST:]file2

    scp -r local/directory user@server2:home/directory

    scp -P 9090 ./teste.txt user@server2:directory/teste.txt

    scp -i $chave user@127.000.000.000:path/to/file.csv  filename

---

I got to know all this content from this blog post <https://www.golinuxcloud.com/ssh-copy-folder-local-to-remote-server-linux>. Acessed in November 3th, 2020.
