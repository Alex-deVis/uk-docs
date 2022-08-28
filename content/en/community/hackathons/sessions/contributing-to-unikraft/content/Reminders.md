From earlier sessions we saw that we can add an external library as a dependency for an application by appending it to the `$LIBS` variable of the application's `Makefile`:

```
LIBS := $(UK_LIBS)/my_lib
```

Having done that, we can then select it in the menuconfig interface in order to be included in the build process.

Running an unikernel built for `kvm` can be done using the `qemu` command as follows:

```
$ qemu-system-x86_64 -kernel unikraft_unikernel -nographic
```

The `-nographic` argument redirects the output generated by the unikernel to the console.

In [Session 02: Behind the Scenes](content/en/docs/session/02-behind-scenes/index.md) we saw that there are two types of libraries:

* **internal**, which are generally part of the kernel / core (schedulers, file systems, etc.);
* **external**: which generally provide user space-level functionalities

The external libraries should be placed in the `$UK_LIBS` folder, which is by default `$UK_WORKDIR/libs`, and the applications should be placed in the `$UK_APPS` folder, which is by default `$UK_WORKDIR/apps`.