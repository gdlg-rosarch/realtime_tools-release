# Script generated with Bloom
pkgdesc="ROS - Contains a set of tools that can be used from a hard realtime thread, without breaking the realtime behavior. The tools currently only provides the realtime publisher, which makes it possible to publish messages to a ROS topic from a realtime thread. We plan to add a basic implementation of a realtime buffer, to make it possible to get data from a (non-realtime) topic callback into the realtime loop. Once the lockfree buffer is created, the realtime publisher will start using it, which will result in major API changes for the realtime publisher (removal of all lock methods)."
url='http://ros.org/wiki/realtime_tools'

pkgname='ros-kinetic-realtime-tools'
pkgver='1.11.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-roscpp'
'ros-kinetic-rospy'
)

depends=('ros-kinetic-roscpp'
'ros-kinetic-rospy'
)

conflicts=()
replaces=()

_dir=realtime_tools
source=()
md5sums=()

prepare() {
    cp -R $startdir/realtime_tools $srcdir/realtime_tools
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

