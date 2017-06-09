cmake_minimum_required(VERSION 2.8)

project(leveldb)

include_directories(./)
include_directories(include)

set(LEVELDB_DIR ${CMAKE_SOURCE_DIR})
set(LEVELDB_DB_DIR ${LEVELDB_DIR}/db/)
set(SOURCES_LVLDB 
	${LEVELDB_DB_DIR}builder.cc
	${LEVELDB_DB_DIR}db_bench.cc
	${LEVELDB_DB_DIR}db_impl.cc
	${LEVELDB_DB_DIR}db_iter.cc
	${LEVELDB_DB_DIR}dbformat.cc
	${LEVELDB_DB_DIR}filename.cc
	${LEVELDB_DB_DIR}log_reader.cc
	${LEVELDB_DB_DIR}log_test.cc
	${LEVELDB_DB_DIR}log_writer.cc
	${LEVELDB_DB_DIR}memtable.cc
	${LEVELDB_DB_DIR}repair.cc
	${LEVELDB_DB_DIR}table_cache.cc
	${LEVELDB_DB_DIR}version_edit.cc
	${LEVELDB_DB_DIR}version_set.cc
	${LEVELDB_DB_DIR}write_batch.cc)
set(LEVELDB_UTIL_DIR ${LEVELDB_DIR}/util/)
set(SOURCES_LVLDB ${SOURCES_LVLDB}
	${LEVELDB_UTIL_DIR}arena.cc
	${LEVELDB_UTIL_DIR}cache.cc
	${LEVELDB_UTIL_DIR}coding.cc
	${LEVELDB_UTIL_DIR}comparator.cc
	${LEVELDB_UTIL_DIR}crc32c.cc
	${LEVELDB_UTIL_DIR}env.cc
	${LEVELDB_UTIL_DIR}env_boost.cc
	${LEVELDB_UTIL_DIR}hash.cc
	${LEVELDB_UTIL_DIR}histogram.cc
	${LEVELDB_UTIL_DIR}logging.cc
	${LEVELDB_UTIL_DIR}options.cc
	${LEVELDB_UTIL_DIR}status.cc
	${LEVELDB_UTIL_DIR}testharness.cc
	${LEVELDB_UTIL_DIR}testutil.cc
	${LEVELDB_UTIL_DIR}win_logger.cc)
set(LEVELDB_TABLE_DIR ${LEVELDB_DIR}/table/)
set(SOURCES_LVLDB ${SOURCES_LVLDB}
	${LEVELDB_TABLE_DIR}block.cc
	${LEVELDB_TABLE_DIR}block_builder.cc
	${LEVELDB_TABLE_DIR}format.cc
	${LEVELDB_TABLE_DIR}iterator.cc
	${LEVELDB_TABLE_DIR}merger.cc
	${LEVELDB_TABLE_DIR}table.cc
	${LEVELDB_TABLE_DIR}table_builder.cc
	${LEVELDB_TABLE_DIR}two_level_iterator.cc)
set(LEVELDB_PORT_DIR ${LEVELDB_DIR}/port/)
set(SOURCES_LVLDB ${SOURCES_LVLDB}
	${LEVELDB_PORT_DIR}port_win.cc)
if(MSVC)
	add_definitions(-DLEVELDB_PLATFORM_WIN32)
else()
	add_definitions(-DLEVELDB_PLATFORM_POSIX)
endif()

add_library(leveldb ${SOURCES_LVLDB})
