set(libradosstriper_srcs
  libradosstriper.cc
  RadosStriperImpl.cc
  MultiAioCompletionImpl.cc)
add_library(radosstriper ${CEPH_SHARED} ${libradosstriper_srcs})
target_link_libraries(radosstriper librados cls_lock_client osdc common pthread ${CRYPTO_LIBS} ${EXTRALIBS})
set_target_properties(radosstriper PROPERTIES
  OUPUT_NAME radosstriper
  VERSION 1.0.0
  SOVERSION 1
  COMPILE_FLAGS "-fvisibility=hidden -fvisibility-inlines-hidden")

install(TARGETS radosstriper DESTINATION ${CMAKE_INSTALL_LIBDIR})
