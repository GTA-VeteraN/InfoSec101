# MicroCorruption Reverse Engineering WriteUp

Author: [Praveen Singh](https://github.com/GTA-VeteraN) 

`Sydney` - 15 Points

## Password( in Hex)

`60606b244c5e5d76`

## Walkthrough

1. In the `main` function there were two function calls `get_password` , `check_password` .

2. In `check_password` there was a comparison of stored values with the input.

3. So again the password was hardcoded, i.e we just needed the values that were used for comparison.

4. Only catch was the use of `little endian` system.