cmake_minimum_required(VERSION 4.1)
project(quadcopter_simulation)

set(CMAKE_CXX_STANDARD 14)

include_directories(
        quadcopter_simulation
        external/eigen-5.0.1/eigen-5.0.1/
        external/irrlicht-1.8.5/irrlicht-1.8.5/include/
        external/irrlicht-1.8.5/irrlicht-1.8.5/lib/Win64-visualStudio/
)

add_executable(quadcopter_simulation
        quadcopter_simulation/accelerometer.cpp
        quadcopter_simulation/accelerometer.h
        quadcopter_simulation/barometer.cpp
        quadcopter_simulation/barometer.h
        quadcopter_simulation/complementaryFilter.cpp
        quadcopter_simulation/complementaryFilter.h
        quadcopter_simulation/config.h
        quadcopter_simulation/esc_motor.cpp
        quadcopter_simulation/esc_motor.h
        quadcopter_simulation/gyroscope.cpp
        quadcopter_simulation/gyroscope.h
        quadcopter_simulation/irr_coordinate_axes.h
        quadcopter_simulation/irr_event_receiver.h
        quadcopter_simulation/irr_keytimer.h
        quadcopter_simulation/irr_quadcopter_3D.cpp
        quadcopter_simulation/irr_quadcopter_3D.h
        quadcopter_simulation/irr_renderer.cpp
        quadcopter_simulation/irr_renderer.h
        quadcopter_simulation/magnetometer.cpp
        quadcopter_simulation/magnetometer.h
        quadcopter_simulation/main.cpp
        quadcopter_simulation/main_config.h
        quadcopter_simulation/mathHelp.h
        quadcopter_simulation/PID.cpp
        quadcopter_simulation/PID.h
        quadcopter_simulation/quadcopter.cpp
        quadcopter_simulation/quadcopter.h
        quadcopter_simulation/receiver.cpp
        quadcopter_simulation/receiver.h
        quadcopter_simulation/sensorFusion.cpp
        quadcopter_simulation/sensorFusion.h
        quadcopter_simulation/stabilizer.cpp
        quadcopter_simulation/stabilizer.h
        quadcopter_simulation/timer.cpp
        quadcopter_simulation/timer.h
        quadcopter_simulation/utils_diffequation.cpp
        quadcopter_simulation/utils_diffequation.h
        quadcopter_simulation/vectorTypes.h)

set(IRRLICHT_LIB_DIR
        ${CMAKE_CURRENT_SOURCE_DIR}/external/irrlicht-1.8.5/irrlicht-1.8.5/lib/Win64-visualStudio
)

find_library(IRRLICHT_LIB
        NAMES Irrlicht
        PATHS ${IRRLICHT_LIB_DIR}
        NO_DEFAULT_PATH
)

target_link_libraries(quadcopter_simulation PRIVATE
        ${IRRLICHT_LIB}
        opengl32
        gdi32
        user32
        winmm
        imm32
)