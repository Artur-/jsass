[![Build Status](https://img.shields.io/travis/bit3/jsass/master.svg?style=flat-square)](https://travis-ci.org/bit3/jsass)
[![Technical Dept](https://img.shields.io/sonar/https/sonarhub.io/io.bit3:jsass/tech_debt.svg?style=flat-square)](https://sonarhub.io/overview/debt?id=1)
[![Coverage](https://img.shields.io/sonar/https/sonarhub.io/io.bit3:jsass/coverage.svg?style=flat-square)](https://sonarhub.io/overview/coverage?id=1)
[![Duplications](https://img.shields.io/sonar/https/sonarhub.io/io.bit3:jsass/duplicated_lines_density.svg?label=duplications&style=flat-square)](https://sonarhub.io/overview/duplications?id=io.bit3%3Ajsass)
[![Violations](https://img.shields.io/sonar/https/sonarhub.io/io.bit3:jsass/violations.svg?style=flat-square)](https://sonarhub.io/component_issues/index?id=io.bit3%3Ajsass)
[![Dependency Status](https://www.versioneye.com/user/projects/56c9f52c18b2710403dfd158/badge.svg?style=flat-square)](https://www.versioneye.com/user/projects/56c9f52c18b2710403dfd158)
[![Gratipay](https://img.shields.io/gratipay/bit3.svg?style=flat-square)](https://gratipay.com/bit3/)
[![Documentation Status](https://readthedocs.org/projects/jsass/badge/?version=latest)](https://readthedocs.org/projects/jsass/?badge=latest)

Java sass compiler
==================

Feature complete java sass compiler using [libsass][libsass] version 3.3.6.

The most advantage of jsass is to hide the libsass complexity from the developer and provide a more java like way.

For complete documentation, see [jsass.rtfd.org][jsass-docs].

[libsass]: https://github.com/sass/libsass
[jsass-docs]: http://jsass.rtfd.org/

Example
-------

There is a [webapp example](example/webapp) containing a servlet sample implementation, to illustrate the way you
may integrate jsass into your webapp.

Changelog
---------

You can find the changelog in our documentation at [jsass.rtfd.org/en/latest/changelog.html][changelog]

[changelog]: http://jsass.readthedocs.org/en/latest/changelog.html

Compatibility
-------------

| Java             | Linux                                 | Windows                     | Mac          |
| ---------------- | ------------------------------------- | --------------------------- | ------------ |
| ![Java 7][java7] | ![CentOS 5 (x86_64)][centos5]         | ![Windows 32bit][windows32] | ![OS X][osx] |
| ![Java 8][java8] | ![CentOS 6 (x86_64)][centos6]         | ![Windows 64bit][windows64] |              |
|                  | ![CentOS 7 (x86_64)][centos7]         |                             |              |
|                  | ![ubuntu 12.04 (x86_64)][ubuntu12.04] |                             |              |
|                  | ![ubuntu 14.04 (x86_64)][ubuntu14.04] |                             |              |

A note to Windows: jsass may also work on Windows.
But at the moment there are no automated tests and the platform is not well tested!

[java7]: https://img.shields.io/badge/Java-7-red.svg?style=flat-square
[java8]: https://img.shields.io/badge/Java-8-green.svg?style=flat-square

[centos5]: https://img.shields.io/badge/CentOS-5%20%28x86_64%29-green.svg?style=flat-square
[centos6]: https://img.shields.io/badge/CentOS-6%20%28x86_64%29-green.svg?style=flat-square
[centos7]: https://img.shields.io/badge/CentOS-7%20%28x86_64%29-green.svg?style=flat-square
[ubuntu12.04]: https://img.shields.io/badge/ubuntu-12.04%20%28x86_64%29-green.svg?style=flat-square
[ubuntu14.04]: https://img.shields.io/badge/ubuntu-14.04%20%28x86_64%29-green.svg?style=flat-square

[windows32]: https://img.shields.io/badge/Windows-32bit_(broken)-red.svg?style=flat-square
[windows64]: https://img.shields.io/badge/Windows-64bit-yellow.svg?style=flat-square

[osx]: https://img.shields.io/badge/OS%20X-10+-green.svg?style=flat-square

Gradle tasks you should know
----------------------------

`gradle check` runs checkstyle, pmd, junit locally.

`gradle runDockerTests` runs junit tests on all docker containers.

`gradle buildNativeLibs` build the native libs, using our build docker container.

`gradle buildDocker` build latest version of all docker containers locally. This should only used for development purpose, the containers are available on Docker Hub!
 
Build scripts
-------------

*Our build scripts are mostly deprecated in favor of the gradle tasks!*

`./bin/make-libjsass-darwin.sh` build the native lib for OS X.
 
`./bin/make-libjsass-linux-x64.sh` build the native lib for Linux, using our build docker container. This is equivalent to `gradle buildDockerBuildLinux64 buildNativeLinux64Libs`!
 
`./bin/make-libjsass-windows-x32.sh` build the native lib for Windows, using our build docker container. This is equivalent to `gradle buildDockerBuildWindows32 buildNativeWindows32Libs`!
 
`./bin/make-libjsass-windows-x64.sh` build the native lib for Windows, using our build docker container. This is equivalent to `gradle buildDockerBuildWindows64 buildNativeWindows64Libs`!
 
How to make a release
---------------------

```bash
$ ./gradlew release
$ git checkout $(git describe --abbrev=0)
$ ./gradlew uploadArchives
$ git checkout master
$ git merge --no-ff $(git describe --abbrev=0 develop)
$ git push origin master
$ git checkout develop
```

Dont forget to release the artifact from [staging repository](https://oss.sonatype.org/#stagingRepositories)!

License
-------

MIT-License
