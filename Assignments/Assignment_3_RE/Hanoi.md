
# MicroCorruption Reverse Engineering WriteUp

Author: [Praveen Singh](https://github.com/GTA-VeteraN) 

`Hanoi` - 20 Points

## Password( in Hex)

16 padding bytes and then `a0`.

`00112233445566778899aabbccddeeffa0`

## Walkthrough

1. In the `main` function there was just a single call of function `login`.

2. In `login` this time they just compared a single value at a particular memeory location that was within the scope of the input memory location.

3. And also there was a function call for `test_password_valid` which was designed to change the value of `r15` register as there was a comparison of that value in the `login` function.

4. In this problem the value of `r15` remained `0` for the inputs so there was no need to do anything for that. ( it was required to have the value of r15 register to be zero after the call of `test_password_valid`.)

5. After getting this we just needed the value at `0x2410` to be `a0` and our input memeory location started at `0x2400` i.e we just need `16` padding bytes before `a0` and that's it. 