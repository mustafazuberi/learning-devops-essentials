# Running Ubuntu on Local Machines

## Virtualization Concepts

We have hardware, just like we all have laptops. Hardware has three major components: CPU, memory, and storage. Memory includes runtime memory, and storage contains all data. In this setup, we have a Windows OS and other applications. Whenever an operation is required, we don't communicate directly with the CPU; instead, we use the operating system, which interacts with the CPU.

### Virtual Hardware

We can create a virtual hardware environment within our physical hardware. For example, if we have a laptop with 8 CPUs, 16 GB of RAM, and 100 GB of storage, we can partition this hardware into a virtual environment. This virtual environment will be smaller than the parent system.

In this case, we might allocate 4 GB of RAM and 10 GB of storage to the virtual environment, effectively creating a smaller "virtual laptop" within the physical laptop. We need to follow the same steps for this virtual environment as we do with the main system. This includes installing an operating system and other software, just as we would on the main laptop.

After setting up the OS in the virtual machine, we can install software and use it as needed.

# Virtualization Techniques

## Hypervisor-Based Virtualization

In virtualization, we use a hypervisor. The hypervisor's job is to create virtual machines.

## Containerization

Another technique of virtualization is using Docker Engine. In this technique, we don’t create virtual machines; instead, we create containers.

We can create as many containers as our hardware allows.

The tool used for virtual machines is the hypervisor, and for containerization, we use Docker Engine.

# Differences Between Virtualization and Containerization

## Virtualization

In virtualization, we have a dedicated space for virtual machines. For example, if we allocate 4 GB of RAM and 10 GB of storage to a VM, this space is dedicated to that VM and cannot be used by the main laptop because it is reserved for the VM.

## Containerization

In containerization, we don't have dedicated space. We can use the space dynamically, and when we are not using it, we don't lose that space because it is shared and not dedicated to that container.

### Operating System and Kernel

Another advantage is related to the operating system. For example, if we have a Windows operating system with its own load on our machine, using virtual machines requires installing another operating system, like Windows or Linux, which takes up additional space in the virtual machine.

In containerization, we can use only the part of the operating system that is needed and avoid using unnecessary parts. This introduces the concept of a shared kernel.

In an operating system, the kernel is an important component that handles almost all the load and is the main piece of software that processes everything.

### Virtualization vs. Containerization

- **Virtualization:**
  Hardware (OS) (Kernel) > Virtualization > Virtual Machine OS (Kernel) - Boot Time

  > Virtual Machine OS (Kernel) - Boot Time

- **Containerization:**
  Hardware (OS) (Kernel) -> Containerization > Container (Cutting Edge OS - Shared Kernel)
  > Container (Cutting Edge OS - Shared Kernel)

# Boot Time

## Boot Time in Virtualization

Whenever we turn on our laptop, it takes some time to load Windows. The system loads Windows into RAM and then starts up. This process takes some time. In virtualization, we have a separate VM within the hardware, and the VM has its own OS. Therefore, it takes more boot time for the VM.

## Boot Time in Containerization

Containerization takes very little time to start because we don't have a separate VM. We are using a cutting-edge OS that employs a shared kernel, which results in faster boot times.

# Installing Docker

For containerization, we need to install Docker. One of the requirements for this is WSL (Windows Subsystem for Linux).

# What is WSL?

As we have studied the concepts of virtualization and containerization, we need WSL (Windows Subsystem for Linux) for containerization. WSL helps us achieve Linux compatibility while working in Windows.

What WSL actually does is provide a lightweight Linux kernel and a Linux shell within Windows. This allows us to perform Linux operations within Windows without needing a virtual machine. Unlike VMs, where we install a hypervisor, a VM, and Windows in that VM—which is a lengthy process—WSL simplifies this by creating Linux compatibility within Windows.

# How to Use WSL

Windows has many tools, but not all are enabled by default. To enable some of them, you need to search for "Windows Features on or off." From there, you can enable various features.

By default, WSL is disabled in "Windows Features on or off." You need to enable "Windows Subsystem for Linux," which is turned off by default because most Windows users do not need it. However, developers need it, so Windows provides the option to enable it. Another feature to enable is the "Virtual Machine Platform."

The "Virtual Machine Platform" means that your hardware has virtualization capabilities, which are disabled by default. Virtualization allows you to create partitions and use them. By default, we are not allowed to use virtualization, so enabling this feature allows your hardware to create another hardware (VM) within itself.

Most hardware supports virtualization, but it must be enabled in the BIOS. Each laptop brand, such as HP or Dell, has a different method for enabling virtualization. You can search for a tutorial specific to your laptop to see how to enable virtualization.

# Docker Version

Running the command `docker version` on the command prompt will give the following result:

Client: Version: 27.0.3 API version: 1.46 Go version: go1.21.11 Git commit: 7d4bcd8 Built: Sat Jun 29 00:03:32 2024 OS/Arch: windows/amd64 Context: desktop-linux

Server: Docker Desktop 4.32.0 (157355) Engine: Version: 27.0.3 API version: 1.46 (minimum version 1.24) Go version: go1.21.11 Git commit: 662f78c Built: Sat Jun 29 00:02:50 2024 OS/Arch: linux/amd64 Experimental: false containerd: Version: 1.7.18 GitCommit: ae71819c4f5e67bb4d5ae76a6b735f29cc25774e runc: Version: 1.7.18 GitCommit: v1.1.13-0-g58aa920 docker-init: Version: 0.19.0 GitCommit: de40ad0

As we see here, the client OS is Windows and the server OS is Linux. This means that, behind the scenes, the Docker engine uses Linux. Therefore, while using Windows, we can still run Linux.

We can have an Ubuntu container and create this container in Docker with the following command:

In Docker, anything that can be run is called an "image." We will learn how to create images and can upload them to Docker Hub so others can use and learn from them.

# Run the Ubuntu Docker Image

Execute the following command to start an interactive terminal session in the Ubuntu container:

The explanation of this command is as follows:

- `docker` is the client that runs the command.
- `-it` stands for interactive mode, which means that the container I am going to create will allow interaction.
- `--rm` means that once you exit the container and there is no further use for it, the container will be automatically deleted.
- `ubuntu` is the image that we have already downloaded with `docker pull ubuntu`.
- `/bin/bash` is the executor/bash. In Linux, everything is CLI-based, so we use bash, which is a special program where we write commands, execute them, and get results.
