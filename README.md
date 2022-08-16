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
I first change the datatype of DAT_000120c0 to i30 element array in GHIDRA and obtained the values stored there.  
![image](https://user-images.githubusercontent.com/92073778/184892627-b82b7d1e-3128-4bc2-8062-0183f6898bea.png)

