if(ESP_PLATFORM)
    set(SOURCES PCA9685.cpp)

    idf_component_register(
        SRCS ${SOURCES}
        INCLUDE_DIRS . 
        REQUIRES I2Cdev
    )
        
else(ESP_PLATFORM)
    add_library(PCA9685 PCA9685.cpp PCA9685.h)

    target_link_libraries(PCA9685 I2Cdev)
    target_include_directories(PCA9685 PUBLIC .)
endif(ESP_PLATFORM)
