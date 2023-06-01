# e2fsprogs-rpm
Building e2fsprogs RPM for RHEL based operating systems (AlmaLinux/Rocky Linux 7/8/9)

### WARNING: ALL Tests are disabled/skipped in the spec file, use at your own risk!


| OS      | Works? |
| ----------- | ----------- |
| AlmaLinux 8 | Yes       |
| Rocky Linux | Yes        |
| Rocky Linux 9 | No       |
| AlmaLinux 9   | No       |

### Installing RPMTools

```
dnf install -y rpmdevtools rpmlint
```

Automatically create the folder tree

```
rpmdev-setuptree
```

eg

```
rpmbuild/
├── BUILD
├── RPMS
├── SOURCES
├── SPECS
└── SRPMS
```

Load the .spec file into the SPECS folder, for example:

```
wget https://raw.githubusercontent.com/arjitc/e2fsprogs-rpm/main/e2fsprogs.spec -O /root/rpmbuild/SPECS/e2fsprogs.spec
```


### Building The RPM

```
wget https://mirrors.edge.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/v1.47.0/e2fsprogs-1.47.0.tar.xz -O /root/rpmbuild/SOURCES/e2fsprogs-1.47.0.tar.xz
wget https://src.fedoraproject.org/rpms/e2fsprogs/raw/main/f/0001-remove-local-PATH.patch -O /root/rpmbuild/SOURCES/0001-remove-local-PATH.patch
wget https://src.fedoraproject.org/rpms/e2fsprogs/raw/main/f/tytso-key.asc -O /root/rpmbuild/SOURCES/tytso-key.asc
wget https://mirrors.edge.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/v1.47.0/e2fsprogs-1.47.0.tar.sign -O /root/rpmbuild/SOURCES/e2fsprogs-1.47.0.tar.sign
```

```
yum install fuse-devel
yum install libblkid-devel libselinux-devel libsepol-devel libuuid-devel multilib-rpm-config
```

```
rpmbuild --bb e2fsprogs.spec
```

```
rpm -Uvh /root/rpmbuild/RPMS/x86_64/libss-1.47.0-1.el8.x86_64.rpm /root/rpmbuild/RPMS/x86_64/libcom_err-1.47.0-1.el8.x86_64.rpm /root/rpmbuild/RPMS/x86_64/e2fsprogs-libs-1.47.0-1.el8.x86_64.rpm /root/rpmbuild/RPMS/x86_64/e2fsprogs-1.47.0-1.el8.x86_64.rpm
```

```
e2fsck -V
```

```
[root@vps ~]# e2fsck -V
e2fsck 1.47.0 (5-Feb-2023)
        Using EXT2FS Library version 1.47.0, 5-Feb-2023
[root@vps ~]#
```

### Sources/References

- https://src.fedoraproject.org/rpms/e2fsprogs/raw/main/f/e2fsprogs.spec
- https://blog.nillsf.com/index.php/2018/12/20/how-to-fix-e2fsck-get-a-newer-version-of-e2fsck/
- https://www.redhat.com/sysadmin/create-rpm-package
- https://src.fedoraproject.org/rpms/e2fsprogs/tree/main
- https://mirrors.edge.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/
- https://downloads.whamcloud.com/public/e2fsprogs/latest/el8/RPMS/x86_64/
- https://downloads.whamcloud.com/public/e2fsprogs/latest/el7/RPMS/x86_64/
- https://downloads.whamcloud.com/public/e2fsprogs/latest/el9/RPMS/x86_64/
