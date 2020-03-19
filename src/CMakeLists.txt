set(oxy_stork_SOURCE
        stork.cxx)

add_library(stork ${oxy_stork_SOURCE})

target_include_directories(stork
        PUBLIC ${oxy_stork_SOURCE_DIR}/include)