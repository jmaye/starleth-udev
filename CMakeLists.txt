cmake_minimum_required(VERSION 2.6)

include(ReMake)

remake_project(
  starleth-udev
  VERSION 0.1
  RELEASE alpha
  SUMMARY "A set of udev rules for the StarlETH robot."
  AUTHOR "Jerome Maye"
  CONTACT "jerome.maye@mavt.ethz.ch"
  HOME "http://github.com/jmaye/starleth-udev"
  LICENSE "GNU Lesser General Public License (LGPL)"
  PREFIX starleth-
  INSTALL /usr
  CONFIGURATION_DESTINATION /etc/udev
)

remake_add_directories(rules)

remake_pack_deb(
  ARCH all
  DEPENDS udev
  EXTRA debian/*
)

remake_distribute_deb(
  DISTRIBUTION lucid
  SECTION admin
  UPLOAD ppa:jmaye/starleth
  DEPENDS remake
  PASS STARLETH_UDEV_GIT_REVISION
)

remake_distribute_deb(
  DISTRIBUTION precise
  SECTION admin
  UPLOAD ppa:jmaye/starleth
  DEPENDS remake
  PASS STARLETH_UDEV_GIT_REVISION
)

remake_distribute_deb(
  DISTRIBUTION trusty
  SECTION admin
  UPLOAD ppa:jmaye/starleth
  DEPENDS remake
  PASS STARLETH_UDEV_GIT_REVISION
)
