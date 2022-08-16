# Rev-Bin
PClub secy task 2  
I used GHIDRA to decompile the given binary file.  
In the main function we see a `checkPassword` function which takes the input from stdin as an argument. If the checkPassword returns 1, then our password is correct.  
In the checkPassword function we see four functions that are being used: `process`,`prepare`,`format`,`checkRes`.
If the checkRes function returns 1, then the checkPassword function also returns 1.  
![image](https://user-images.githubusercontent.com/92073778/184889679-1820777e-86a5-4512-a65e-7fc9038fd444.png)  
The checkRes function takes an integer pointer named local_8c as an argument.  
![image](https://user-images.githubusercontent.com/92073778/184890269-45068a70-d118-43bd-bb2b-0873246590e0.png)  
We can see that the checkRes function compares the integers stored in the array pointed by local_8c to a 30 element array kept at &DAT_000120c0.  
I first change the datatype of DAT_000120c0 to 30 element integer array in GHIDRA and obtained the values stored there.  
![image](https://user-images.githubusercontent.com/92073778/184892627-b82b7d1e-3128-4bc2-8062-0183f6898bea.png)  
Now let's see what local_8c exactly is  
We analyze the function `process`   
![image](https://user-images.githubusercontent.com/92073778/184911371-7b58226e-e129-4c74-881f-e097597d58ce.png)  
local_8c is malloced 120 bytes (30 integers) and the 30 elements pointed by param_2 (which is &local88) are effectively copied to address pointed by local_8c  
local_8c points to the array [5,3,6,5,2,5,3,3,3,5,2,4,6,5,5,2,2,5,2,6,5,1,3,4,5,3,4,6,6,5] now.  
Lets see what happens in the function `format`  
![image](https://user-images.githubusercontent.com/92073778/184916227-65652474-5482-4922-af39-31f5c79be8bc.png)  
We will now reverse this operation to get the required input which will give the correct result.
When we execute the python code , it gives `ftp{PR0GR4MM1NGCLU8_11TK4NPUR}` which is the required password.


