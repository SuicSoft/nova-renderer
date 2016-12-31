# Build script written by Suici Doga <suiciwd(at)gmail(dot)com> <https://github.com/SuicSoft>

cmake_minimum_required(VERSION 3.4)
project(NovaRenderer)

# Download and extract Minecraft MCP

file(MAKE_DIRECTORY ${CMAKE_BINARY_DIR}/mcp)

file(DOWNLOAD
    http://www.modcoderpack.com/website/sites/default/files/releases/mcp931.zip
    ${CMAKE_BINARY_DIR}/mcp931.zip
    SHOW_PROGRESS
)

# Extract MCP
execute_process(COMMAND unzip ${CMAKE_BINARY_DIR}/mcp931.zip -d ${CMAKE_BINARY_DIR}/mcp/)

