# How to install

### Distro support

Tested working (as sane as I could test for) on:

* RHEL 6.3 x86_64
* CentOS 5.8 x86_64
* Fedora 17 x86_64
*  This spec is tested under el6 and el5 only.
However, Fedora15 or later work. maybe.

    $ wget http://nodejs.org/dist/v0.10.XX/node-v0.10.XX.tar.gz

#### RHEL/CentOS/SL/OL 6

    # yum install rpm-build rpmdevtools openssl-devel zlib-devel redhat-rpm-config
    # rpmdev-setuptree
    # spectool -g -R nodejs.spec
    # cp node-js.request_parse_error.patch ~/rpmbuild/SOURCES/
    # rpmbuild -ba nodejs.spec
    # yum install ~/rpmbuild/RPMS/x86_64/nodejs-0.X.X-X.el6.x86_64.rpm --nogpgcheck

#### RHEL/CentOS/SL/OL 5

when you try to build on el5, must enable the EPEL repository.

    # sudo rpm -ivh http://dl.fedoraproject.org/pub/epel/5/x86_64/epel-release-5-4.noarch.rpm
    # sudo yum install rpm-build rpmdevtools openssl-devel zlib-devel python26
    # mkdir ~/rpmbuild
    # cd ~/rpmbuild
    # rpmdev-setuptree
    # cp <git repo dir>/nodejs.spec ./SPECS/.
    # spectool -g -R SPECS/nodejs.spec
    # cp <git repo dir>/node-js.centos5.configure.patch ./SOURCES/.
    # rpmbuild --clean -ba ./SPECS/nodejs.spec
    # yum install ~/rpmbuild/RPMS/x86_64/nodejs-0.X.X-X.x86_64.rpm --nogpgcheck
