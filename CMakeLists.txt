add_compile_options(-fopenmp)
include_directories(/usr/local/include/e2sim)
link_directories(/usr/local/lib)
link_libraries(e2sim)

build_lib(
    LIBNAME oran-interface
    SOURCE_FILES 
        model/oran-interface.cc
        model/asn1c-types.cc
        model/function-description.cc
        model/kpm-indication.cc
        model/kpm-function-description.cc
        model/ric-control-message.cc
        model/ric-control-function-description.cc
        helper/oran-interface-helper.cc
        helper/indication-message-helper.cc
        helper/lte-indication-message-helper.cc
        helper/mmwave-indication-message-helper.cc

    HEADER_FILES
        model/oran-interface.h
        model/asn1c-types.h
        model/function-description.h
        model/kpm-indication.h
        model/kpm-function-description.h
        model/ric-control-message.h
        model/ric-control-function-description.h
        helper/oran-interface-helper.h
        helper/indication-message-helper.h
        helper/lte-indication-message-helper.h
        helper/mmwave-indication-message-helper.h
    
    LIBRARIES_TO_LINK ${libcore} 
        ${E2SIM_LIBRARIES}

    TEST_SOURCES
        test/oran-interface-test-suite.cc
)