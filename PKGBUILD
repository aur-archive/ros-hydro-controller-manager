# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - The controller manager."
url='https://github.com/ros-controls/ros_control/wiki'

pkgname='ros-hydro-controller-manager'
pkgver='0.7.2'
_pkgver_patch=1
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-realtime-tools
  ros-hydro-catkin
  ros-hydro-controller-manager-msgs
  ros-hydro-hardware-interface
  ros-hydro-controller-interface
  ros-hydro-pluginlib)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-hydro-hardware-interface
  ros-hydro-pluginlib
  ros-hydro-controller-manager-msgs
  ros-hydro-controller-interface
  ros-hydro-realtime-tools)
depends=(${ros_depends[@]})

_tag=release/hydro/controller_manager/${pkgver}-${_pkgver_patch}
_dir=controller_manager
source=("${_dir}"::"git+https://github.com/ros-gbp/ros_control-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
