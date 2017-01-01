# Build script written by Suici Doga <suiciwd(at)gmail(dot)com> <https://github.com/SuicSoft>

cmake_minimum_required(VERSION 3.4)
project(NovaRenderer)

# Download and extract Minecraft MCP

if (NOT EXISTS ${CMAKE_BINARY_DIR}/mcp/)
    file(MAKE_DIRECTORY ${CMAKE_BINARY_DIR}/mcp)

    message("Downloading MCP")

    file(DOWNLOAD
        http://www.modcoderpack.com/website/sites/default/files/releases/mcp931.zip
        ${CMAKE_BINARY_DIR}/mcp931.zip
    )

    message("Extracting MCP")

    # Extract MCP
    execute_process(COMMAND unzip ${CMAKE_BINARY_DIR}/mcp931.zip -d ${CMAKE_BINARY_DIR}/mcp/) # For Windoze we have to use a powershell command
else()
    message("MCP already downloaded")
endif()

# Decompile Minecraft
message("Decompiling Minecraft (this may take a long time)")

if(UNIX)
    execute_process(COMMAND ${CMAKE_BINARY_DIR}/mcp/decompile.sh WORKING_DIRECTORY ${CMAKE_BINARY_DIR}/mcp/) # Linux and Mac (I don't have Mac so this might not work on Mac)
elseif(WIN32)
    execute_process(COMMAND cmd //C ${CMAKE_BINARY_DIR}/mcp/decompile.bat )  # Windows (I will test on 10)
endif()

# Inject Nova into Minecraft


