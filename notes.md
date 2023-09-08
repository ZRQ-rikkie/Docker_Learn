## Virtual Machine vs Container

**Virtual Machine:** An abstraction of a machine(physical hardware). Using hyperviser to run virtual machines.

![1694196763060](image/notes/1694196763060.png)

* Each VM needs a full-blown OS
* Slow to start
* Resourse intensive

**Container:** An isolated environment for running an application

* Allow running multiple apps in isolation
* Are lightweight
* Use OS of the host
* Start quickly
* Need less hardware resources

## Docer Architecture

**Container:**
A container is like a process
All container share the OS of the host (share the kernel of the host)
**Kernel:**
A kernel is the core of the OS, it manages applications and hardware resources.
Every OS has its own kernel/engine. Different Kernel has different APIs

![1694196113124](image/notes/1694196113124.png)

## Development Workflow

Dockerize an application

![1694197982572](image/notes/1694197982572.png)

Dockerfile is a file contains all the instruction that docker uses to package an application into an image.

Image:

* A cut-down OS
* A runtime environment (eg Node)
* Application files
* Third-party libraries
* Environment variables

Ask docker to start a **container** to use that **image**.

Container is a special process has its own file system provided by the image.

![1694199409529](image/notes/1694199409529.png)

## Linux Distributions

Ubuntu

```
docker run ubuntu

docker ps
<!-- show the latest running process(container) -->

docker ps -a
<!-- for all -->
```

