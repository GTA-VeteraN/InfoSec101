
# MicroCorruption Reverse Engineering WriteUp

Author: [Praveen Singh](https://github.com/GTA-VeteraN) 

`Cusco` - 25 Points

## Password( in Hex)

16 padding bytes and then `4644`.

`00112233445566778899aabbccddeeff4644`

## Walkthrough

1. In the `main` function there was just a single call of function `login` similar to the case of `Hanoi`.

2. In `login` this time there was no comparison.

3. There was a function call for `test_password_valid` which was designed to change the value of `r15` register as there was a comparison of that value in the `login` function.

4. In this problem the value of `r15` remained `0` for the inputs but the `login` needed the value of `r15` to be `non-zero`.

5. So there was nothing else in the code to examine, so I wrote some random input and got the line `insn address unaligned` in the debugger console and sp points to the memory location of one of the byte of input.

6. As in this case the input was stored at the memory location of stack pointer. ( before calling `getsn` the address of the storage of input was given that of the address of `sp` )

7. So this was the case of `Buffer Overflow` , so we just need to use this overflow to put the return address of `unlock_door` in perfect position.

8. So using breakpoint we found the memory location of sp `0x43fe` when it was returning to the main function. So we just need to put the return address of `unlock_door` there.

9. And the input buffer started at `0x43ee` so here also we need 16 padding bytes and then the address of `unlock_door` which was `0x4446` (we need to write 4644 in the input because of little endiadness) and that's all.