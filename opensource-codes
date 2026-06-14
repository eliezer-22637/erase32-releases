@echo off

rem MAIN MENU
:MAIN
cls
echo ---------------------------------------
echo             Erase32 Tool
echo ---------------------------------------
echo Select operation
echo 1. Start erasing
echo 2. Check device info
echo 3. About this tool
echo 4. Exit

rem SELECTOR
set /p selector="select menu (1 to 3): "

rem MAIN MENU LOGICS
if "%selector%"=="1" goto ERASE_MENU
if "%selector%"=="2" goto CHECK_INFO
if "%selector%"=="3" goto ABOUT
if "%selector%"=="4" exit
echo ERROR: Input not valid!
goto MAIN

:ERASE_MENU
cls
echo PLEASE PREPARE YOUR ESP32
timeout /t 3 >nul
echo Guide: Press any key when you're ready
timeout /t 2 >nul
echo Press any key to start erasing
pause >nul

echo Guide: Ports can be seen by opening Device Manager ^> Ports (COM ^& LPT) ^> COM6 (May different
echo Example: COM6
set /p com_port="Please input your port: "
set baud_real=115200
echo Default baud rate: 115200
set /p user_input="Please input baud rate (write "skip" to use default baud rate) : "
if /i "%baud_rate%"=="skip" goto THE_PROCESS
if /i "%baud_rate%"=="" goto THE_PROCESS
echo ERROR : Input not valid!
goto ERASE_MENU

set baud_real=%user_input%
timeout /t 2 >nul

:THE_PROCESS
echo Starting operation...
call python -m esptool --port %com_port% --baud %baud_real% erase_flash
timeout /t 1 >nul
goto A

:A
echo 1. Go to main menu
echo 2. Exit
set /p selector="select menu : "
if "%selector%"=="1" goto MAIN
if "%selector%"=="2" exit
echo ERROR : Input not valid
goto A

:CHECK_INFO
cls
set /p com_port="Please input your port: "
python -m esptool --port %com_port% chip_id
timeout /t 10 >nul
echo 1. Go to main menu
echo 2. Exit
set /p selector="select menu : "
if "%selector%"=="1" goto MAIN
if "%selector%"=="2" exit
echo ERROR : Input not valid
goto CHECK_INFO

:ABOUT
cls
echo Erase32 Software
echo Hello, this is the owner of this software
echo So this piece of software is used for deleting ESP32 memories
echo I know deleting a software inside of ESP32 is easy
echo only using python -m esptool --port %com_port% erase_flash
echo But for you who was don't want writing that code, this is the right software
echo Also this software can be used to see com ports, microcontroler model, and all of the
echo microcontroler information
echo This software is open source
echo I'm putting the code in the GitHub
echo Thanks for using my software

timeout /t 10 >nul
echo 1. Go to main menu
echo 2. Exit
set /p selector="select menu : "
if "%selector%"=="1" goto MAIN
if "%selector%"=="2" exit
echo ERROR : Input not valid
goto ABOUT