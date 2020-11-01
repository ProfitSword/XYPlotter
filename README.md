# XYPlotter

Software for an Arduino CNC machine, built for UGA's ELEE 4230 course in fall 2020.

## Overview

**!!! THIS SECTION IS CURRENTLY UNDER CONSTRUCTION !!!**

## Changelog
- **27 October 2020**:
  - This is commit hash `a7348b9` and what I consider to be the starting point of this code. All following changelog entries start from here.

- **31 October 2020**:
  - `command.hpp`
    - The data type of `Command::numParameters` has been changed from `size_t` to `int` to allow this size to take a value of -1 for error checking purposes.
    - The data type of `Command::parameters` has been changed from `int[]` to `long int[]` to fit the return type of functions used to gather its values, namely `strtol()` from the `string.h` header of the C library.
  - `serial_util.hpp` and `serial_util.cpp`
    - All functions defined in `serial_util.hpp` have been implemented in `serial_util.cpp`.
    - `SerialUtil::getMessage()` is now void and accepts a `char*` as an output parameter. This is done so that programmers are not forced to delete memory returned by the function.
  - `command_parser.hpp` and `command_parser.cpp`
    - All functions defined in `command_parser.hpp` have been implemented in `command_parser.cpp`.
    - `CommandParser::getRawData()` has been renamed to `CommandParser::getProcessedData()` for semantic reasons. `CommandParser` doesn't need to get raw data when `SerialUtil::getMessage()` already does. It just takes the raw data and transforms it into usable data.
    - `CommandParser::getProcessedData()` is now `void` and accepts a `char*` as an output parameter for the same reason that `SerialUtil::getMessage()` was changed.
  - `xy_plotter_controller.cpp`
    -  `XYPlotterController::initializePlotter()` has been given a basic implementation.