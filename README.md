# Codespaces , Linux Distros, Python , SQL

## 1. Codespaces on Github
- Gives access to VSCode editor and underlying virtual machine
## 2. Shell scripts
- .sh scripts
- Run by : 
    ```
    chmod +x hello.sh 
    ./hello.sh
    ``` 
- where chmod changes access permission to make file executable and ./hello.sh helps us to run the executable binary
- Can also do `bash hello.sh`.

### i) Multiline scripts
- To execute multiline scripts, use EOF command.
- EOF command used in here document 
- Here documents helps us to directly pass multiple lines of text directly into command.
- EOF MUST be used at start and end of string.
- EOF can be any unique string, not necessarily EOF.
- See eof.sh.

## Linux

- Virtual Machines for Codespaces run on Images.
- Images are created using [Github Runner Image](https://github.com/actions/runner-images)
- We will use an Ubuntu image.


Doubts:
- Do we need !bin/sh??
- How does Github actions relate to this?
