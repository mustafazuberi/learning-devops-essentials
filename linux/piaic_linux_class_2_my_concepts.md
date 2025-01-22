docker run -ti --rm ubuntu /bin/bash

Here, we are actually saying to go in the /bin directory and execute the bash file.

ls: In Linux, we can see the directories with the ls command. So, as we are in the Linux environment:

cd: If we want to go into any directory, we use cd bin, which means go into the bin directory.

When we run the command docker run -ti --rm ubuntu /bin/bash, our path will change. For example, if you open your Windows Command Prompt and run this command, your path will be C:\Users\admin>. But just after this command is run, your path changes to root@304b837c0837:/, which means we are now in Linux.

In the Linux file system, which is hierarchical, the base is the root. This means the starting point is root. Thus, the slash (/) in the command root@304b837c0837:/ indicates this root.

pwd is the command to check where we are right now (present working directory).

cd .. is used to go back one step.

The root is the superuser with administrative privileges. We have two users: the first is the superuser, which is root, and the other is ubuntu, whose home directory is /home/ubuntu.

Root User: The superuser with full administrative privileges and unrestricted access to the entire system. Home directory: /root.
Ubuntu User: A regular user with limited privileges but can use sudo to perform administrative tasks temporarily. Home directory: /home/ubuntu.

When you run the command docker run -ti --rm ubuntu /bin/bash, you are logged in as the root user by default inside the Docker container. This means you have all administrative privileges, and the prompt shows you're in the root of the filesystem (/). However, this / directory is not the same as the root user's home directory. To see the root user's personal files, you need to navigate to the /root directory using the command cd /root. In short, / is the root of the entire filesystem, while /root is the home directory specifically for the root user.

By default, when we first enter Linux from Windows with docker run -ti --rm ubuntu /bin/bash, it brings us to the root directory (/), but if I want to see the files of the root user, I need to go to the /root directory.

Here’s your text with grammar fixed:

/ is the root of the entire filesystem and is accessible to all users, but only root has full permissions to create, modify, or delete files directly in /.

If you create files in /, they will be owned by the root user because regular users (like ubuntu) do not have permission to write directly in /. In your case, since you're logged in as root by default in the Docker container, any files you create in / will belong to the root user.

If you were logged in as a regular user (e.g., ubuntu), you wouldn’t have permission to create files in / without using sudo or switching to root.

mkdir: This is used to create a directory. For example, if I am in the root user's home directory, which is /root, and run the command mkdir learning-linux, it will create the directory in that root user's home directory, which is /root.

touch: This is used to create a file. For example, if I am in a directory learning-linux, which is in the root user's home directory (/root), and run the command touch app.py, it will create a file named app.py.

echo: If we want to just print something, similar to console.log in JavaScript, we can use echo followed by the text we want to print. For example, echo Pakistan Zindabad will print Pakistan Zindabad below.

> : To write something into a file, we use the "redirect output operator" (>), and the result of this operation is called standard output. If we run the command echo Mustafa Zuberi > app.py, it means the output of echo Mustafa Zuberi (which is Mustafa Zuberi) will be redirected (written) into the file app.py.

cat: This command is used to read the contents of a file. For example, if we run cat app.py, it will show us the content of the file, which would be Mustafa Zuberi.

> > : To append text to a file, we use the append operator (>>). If we use echo New Text > app.py, it will overwrite the old text. However, if we use echo New Text >> app.py, it will append the text to the file rather than overwriting it.

2>: This command is called "redirect error message". It redirects the error message of the command before 2> to a file specified after 2>. For example, if we run ech Mustafa Zuberi 2> app.py, we will get an error because ech is misspelled; it should be echo. The error message will be written to the file app.py.

Docker's Main Purposes

Docker is used to run applications in an isolated environment, but it's not the only option for isolation.

Other Options for Isolated Environments:

Virtual Machines (VMs): Provide strong isolation by virtualizing entire operating systems, though they can be resource-intensive.
Linux Containers (LXC): Offer lightweight containerization similar to Docker but require more manual configuration.
Kubernetes: While not a direct alternative, it manages containerized applications and supports different container runtimes.
Systemd-nspawn: Provides a simple, lightweight containerization method integrated with systemd.
Vagrant: Allows for the creation of isolated VM environments and can be used with various VM providers.
Podman: Offers a Docker-compatible container management tool with rootless mode for enhanced security.
Firecracker: A virtualization technology designed for running microVMs, offering efficient isolation with lower overhead than traditional VMs.
Quick Boot Stamp: Docker starts quickly, whereas VMs take some time as they have separate operating systems.

ls -l: If we want to see directories and files with details, this command will help. It prints directories and files as list items. If an item starts with dr, it means it’s a directory. If it starts with a -, it means it’s a file. There are other details at the start of each list item, which represent privileges that we will study later.
