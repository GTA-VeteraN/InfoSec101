# MicroCorruption Reverse Engineering WriteUp

Author: [Praveen Singh](https://github.com/GTA-VeteraN)

`New Orleans` - 10 Points

## Password( in Hex)

`5d5055655a6343`

## Walkthrough

1. In the `main` function there were three function calls `create_password` , `get_password` , `check_password` .

2. In `create_password` the password was hardcoded in the form of array.

3. `check_password` just compared each value of the array with the input.