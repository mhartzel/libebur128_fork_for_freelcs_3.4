include_directories(SYSTEM ${GLIB20_INCLUDE_DIRS})
add_definitions(${GLIB20_CFLAGS_OTHER})

add_library(scanner-common parse_args.c nproc.c scanner-common.c)
target_link_libraries(scanner-common ebur128 #
                      ${GLIB20_LIBRARIES} ${GTHREAD20_LIBRARIES})

if(SNDFILE_FOUND AND NOT DISABLE_SNDFILE)
  include_directories(${SNDFILE_INCLUDE_DIRS})
  add_definitions(-DUSE_SNDFILE)
  target_link_libraries(scanner-common ${SNDFILE_LIBRARIES})
endif()
