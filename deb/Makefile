#
#  LIVE mongo-cxx-driver
#
#  Created by Zvonimir Buzanic.
#  2024-11-11
#
# after building mongo-cxx-driver copy this Makefile and debian directory to mongo-cxx-driver-r3.9.0/deb/
# cd mongo-cxx-driver-r3.9.0/deb/ then run "make deb"

VERSION=3.9.0.1
RELEASE=56da1f0

NAME=mongo-cxx-driver
ME=${NAME}-${VERSION}.${RELEASE}
ARCH:=${shell uname -m}
prefix?=/usr/local
libdir=${prefix}/lib
incdir=${prefix}/include
sharedir=${prefix}/share
bindir=${prefix}/bin
pkgdir=${libdir}/pkgconfig
INSTALL?=install -c
INSTALL_DATA=${INSTALL} -m 644
LIBLIVEINCL=-I..
COMMENT=Live Mongo C++ driver and library.

deb:
	rm -rf ${ME}
	mkdir -p ${ME}/${libdir} ${ME}/${pkgdir} ${ME}/${incdir}/libbson-1.0/bson/ ${ME}/${bindir}/ ${ME}/${incdir}/libmongoc-1.0/mongoc/ ${ME}/${sharedir} ${ME}/DEBIAN/
	mkdir -p ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/types/bson_value/ ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/exception/
	mkdir -p ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/builder/stream/ ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/builder/basic/
	mkdir -p ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/config/ ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/enums/
	mkdir -p ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/stdx/ ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/util/
	mkdir -p ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/array/ ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/string/
	mkdir -p ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/document/
	mkdir -p ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/exception/ ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/model/
	mkdir -p ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/config/ ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/gridfs/
	mkdir -p ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/events/ ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/options/gridfs/
	mkdir -p ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/result/gridfs/
	mkdir -p ${ME}/${sharedir}/mongo-c-driver/ ${ME}/${sharedir}/mongo-cxx-driver/
	${INSTALL} -m 775 debian/* ${ME}/DEBIAN/
	sed -i -e "s/%%VERSION%%/${VERSION}.${RELEASE}/g" ${ME}/DEBIAN/control
#libbson
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libbson/libbson-static-1.0.a ${ME}/${libdir}/libbson-static-1.0.a
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libbson/libbson-1.0.so.0.0.0 ${ME}/${libdir}/libbson-1.0.so.0.0.0
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libbson/libbson-1.0.so ${ME}/${libdir}/libbson-1.0.so
	ln -s ${ME}/${libdir}/libbson-1.0.so ${ME}/${libdir}/libbson-1.0.so.0
#pkgconfig libbson
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libbson/libbson-static-1.0.pc ${ME}/${pkgdir}/libbson-static-1.0.pc
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libbson/libbson-1.0.pc ${ME}/${pkgdir}/libbson-1.0.pc
#include libbson
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-src/src/libbson/src/bson/*.h ${ME}/${incdir}/libbson-1.0/bson/
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libbson/src/bson/*.h ${ME}/${incdir}/libbson-1.0/bson/
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-src/src/libbson/src/bson/forwarding/bson.h ${ME}/${incdir}/libbson-1.0/bson.h
#libmongoc
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libmongoc/mongoc-stat ${ME}/${bindir}/mongoc-stat
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libmongoc/libmongoc-1.0.so.0.0.0 ${ME}/${libdir}/libmongoc-1.0.so.0.0.0
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libmongoc/libmongoc-1.0.so ${ME}/${libdir}/libmongoc-1.0.so
	ln -s ${ME}/${libdir}/libmongoc-1.0.so ${ME}/${libdir}/libmongoc-1.0.so.0
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libmongoc/libmongoc-static-1.0.a ${ME}/${libdir}/libmongoc-static-1.0.a
#pkgconfig libmongoc
	${INSTALL} -m 755 /usr/local/lib/pkgconfig/libmongoc-1.0.pc ${ME}/${pkgdir}/libmongoc-1.0.pc
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libmongoc/libmongoc-static-1.0.pc ${ME}/${pkgdir}/libmongoc-static-1.0.pc
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libmongoc/src/libmongoc-ssl-1.0.pc ${ME}/${pkgdir}/libmongoc-ssl-1.0.pc
#include libmongoc
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-src/src/libmongoc/src/mongoc/*.h ${ME}/${incdir}/libmongoc-1.0/mongoc/
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/src/libmongoc/src/mongoc/*.h ${ME}/${incdir}/libmongoc-1.0/mongoc/
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-src/src/libmongoc/src/mongoc/forwarding/mongoc.h ${ME}/${incdir}/libmongoc-1.0/mongoc.h
#libbsoncxx
	${INSTALL} -m 755 ../build/src/bsoncxx/libbsoncxx.so.3.9.0 ${ME}/${libdir}/libbsoncxx.so.3.9.0
	${INSTALL} -m 755 ../build/src/bsoncxx/libbsoncxx.so ${ME}/${libdir}/libbsoncxx.so
	ln -s ${ME}/${libdir}/libbsoncxx.so ${ME}/${libdir}/libbsoncxx.so._noabi
#pkgconfig libbsoncxx
	${INSTALL} -m 755 ../build/src/bsoncxx/cmake/libbsoncxx.pc ${ME}/${pkgdir}/libbsoncxx.pc
#include libbsoncxx
	${INSTALL} -m 755 ../build/src/bsoncxx/lib/bsoncxx/v_noabi/bsoncxx/config/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/config/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/types/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/types/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/types/bson_value/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/types/bson_value/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/exception/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/exception/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/builder/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/builder/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/builder/stream/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/builder/stream/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/builder/basic/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/builder/basic/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/config/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/config/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/enums/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/enums/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/stdx/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/stdx/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/util/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/util/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/array/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/array/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/string/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/string/
	${INSTALL} -m 755 ../src/bsoncxx/include/bsoncxx/v_noabi/bsoncxx/document/*.hpp ${ME}/${incdir}/bsoncxx/v_noabi/bsoncxx/document/
#libmongocxx
	${INSTALL} -m 755 ../build/src/mongocxx/libmongocxx.so.3.9.0 ${ME}/${libdir}/libmongocxx.so.3.9.0
	${INSTALL} -m 755 ../build/src/mongocxx/libmongocxx.so ${ME}/${libdir}/libmongocxx.so
	ln -s ${ME}/${libdir}/libmongocxx.so ${ME}/${libdir}/libmongocxx.so._noabi
#pkgconfig libmongocxx
	${INSTALL} -m 755 ../build/src/mongocxx/cmake/libmongocxx.pc ${ME}/${pkgdir}/libmongocxx.pc
#include libmongocxx
	${INSTALL} -m 755 ../build/src/mongocxx/lib/mongocxx/v_noabi/mongocxx/config/*.hpp ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/config/
	${INSTALL} -m 755 ../src/mongocxx/include/mongocxx/v_noabi/mongocxx/result/gridfs/*.hpp ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/result/gridfs/
	${INSTALL} -m 755 ../src/mongocxx/include/mongocxx/v_noabi/mongocxx/*.hpp ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/
	${INSTALL} -m 755 ../src/mongocxx/include/mongocxx/v_noabi/mongocxx/exception/*.hpp ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/exception/
	${INSTALL} -m 755 ../src/mongocxx/include/mongocxx/v_noabi/mongocxx/model/*.hpp ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/model/
	${INSTALL} -m 755 ../src/mongocxx/include/mongocxx/v_noabi/mongocxx/config/*.hpp ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/config/
	${INSTALL} -m 755 ../src/mongocxx/include/mongocxx/v_noabi/mongocxx/gridfs/*.hpp ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/gridfs/
	${INSTALL} -m 755 ../src/mongocxx/include/mongocxx/v_noabi/mongocxx/events/*.hpp ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/events/
	${INSTALL} -m 755 ../src/mongocxx/include/mongocxx/v_noabi/mongocxx/options/*.hpp ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/options/
	${INSTALL} -m 755 ../src/mongocxx/include/mongocxx/v_noabi/mongocxx/options/gridfs/*.hpp ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/options/gridfs/
	${INSTALL} -m 755 ../src/mongocxx/include/mongocxx/v_noabi/mongocxx/result/*.hpp ${ME}/${incdir}/mongocxx/v_noabi/mongocxx/result/
#share
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-src/COPYING ${ME}/${sharedir}/mongo-c-driver/COPYING
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-src/NEWS ${ME}/${sharedir}/mongo-c-driver/NEWS
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-src/README.rst ${ME}/${sharedir}/mongo-c-driver/README.rst
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-src/THIRD_PARTY_NOTICES ${ME}/${sharedir}/mongo-c-driver/THIRD_PARTY_NOTICES
	${INSTALL} -m 755 ../build/_deps/mongo-c-driver-build/uninstall.sh ${ME}/${sharedir}/mongo-c-driver/uninstall.sh
	${INSTALL} -m 755 ../LICENSE ${ME}/${sharedir}/mongo-cxx-driver/LICENSE
	${INSTALL} -m 755 ../README.md ${ME}/${sharedir}/mongo-cxx-driver/README.md
	${INSTALL} -m 755 ../THIRD-PARTY-NOTICES ${ME}/${sharedir}/mongo-cxx-driver/THIRD_PARTY_NOTICES
	${INSTALL} -m 755 ../build/generate_uninstall/uninstall.sh ${ME}/${sharedir}/mongo-cxx-driver/uninstall.sh
	dpkg-deb --build ${ME}

clean:
	rm -rf ${ME} ${ME}.deb
