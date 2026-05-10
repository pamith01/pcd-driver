# Linux Character Driver

Built a Linux character device driver in C that registers 4 virtual devices with independent memory buffers, serial numbers, and access permissions, all managed through the kernel's VFS layer.

The driver supports:
🔹 Dynamic device number allocation via alloc_chrdev_region
🔹 Custom file_operations: open, read, write, lseek, release
🔹 Per-device permissions (read-only, write-only, read-write)
🔹 Private data binding using container_of() for clean device tracking
🔹 Proper sysfs integration with class_create and device_create
🔹 Safe error-path cleanup using goto labels

Tested by interacting with /dev/pcdev-1 through /dev/pcdev-4 directly from user space using standard system calls.

This project was a great first deep dive into how Linux abstracts hardware through the VFS, how character devices are registered and managed in kernel space, and the internals of file_operations dispatch. 