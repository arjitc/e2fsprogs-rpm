# e2fsprogs-rpm
e2fsprogs RPM Builds


rpmbuild --bb e2fsprogs.spec


wget https://mirrors.edge.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/v1.47.0/e2fsprogs-1.47.0.tar.xz -O /root/rpmbuild/SOURCES/e2fsprogs-1.47.0.tar.xz
rpmbuild --bb e2fsprogs.spec
wget https://src.fedoraproject.org/rpms/e2fsprogs/raw/main/f/0001-remove-local-PATH.patch -O /root/rpmbuild/SOURCES/0001-remove-local-PATH.patch
rpmbuild --bb e2fsprogs.spec
yum install fuse-devel
yum install libblkid-devel libselinux-devel libsepol-devel libuuid-devel multilib-rpm-config
rpmbuild --bb e2fsprogs.spec
wget https://src.fedoraproject.org/rpms/e2fsprogs/raw/main/f/tytso-key.asc -O /root/rpmbuild/SOURCES/tytso-key.asc
rpmbuild --bb e2fsprogs.spec
wget https://mirrors.edge.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/v1.47.0/e2fsprogs-1.47.0.tar.sign -O /root/rpmbuild/SOURCES/e2fsprogs-1.47.0.tar.sign
rpmbuild --bb e2fsprogs.spec
nano e2fsprogs.spec
rpmbuild --bb e2fsprogs.spec

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
