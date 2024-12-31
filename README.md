<h2>Overview</h2>
PEStudio is a tool that performs static analysis and executable file properties without running the files.
It offers a variety of information about a file without putting users in danger of execution, which aids in identifying executables that seem suspect or harmful.
In the following lab, I  performed a static investigation on the suspicious binary file using this tool.



<h2>Malware file details</h2>

The following malware executable file has been obtained from malwarebazzar.
  *   Winrar600.exe

![image](https://github.com/user-attachments/assets/aa53c94d-794e-4533-b336-8b047dc7e9d0)


<h2>Analysing the binary </h2>

1. Checking the file properties

![image](https://github.com/user-attachments/assets/f1c73df3-519d-4fc0-bd19-26a0cd48e039)

 
*  The first byte shows 4D 5A ( hex) and MZ ( text)values. This confirms that the file is executable file. 
*  File has an entropy of 7.966 out of 8. This is an indication the file is most likely encrypted, obfuscated or packed. 
*  The executable was created using the 'Visual Studio 2013" tool.
*  Its subsystem property is "GUI" meaning it displays a window during  the operation.  
*  The executable was compiled on Dec 01 2020. 

2. Checking indicators
	
The indicator section highlights the interesting and suspicious data sorted based on their severity level.

![image](https://github.com/user-attachments/assets/f67ff376-3abf-4e17-8aa1-8b0b17c8d30d)


3. Checking VirusTotal rating 

![image](https://github.com/user-attachments/assets/670b27bb-862d-4dfd-af72-d8de3b8970d3)


			
4. Checking the libraries
	
The following libraries have been used. No flagged library exists for this executable. 

![image](https://github.com/user-attachments/assets/ca57026c-e498-44e4-bb05-88f9ef7f5f37)


5. Checking the imports
	
PEStudio has flagged the following imports as "suspicious". They require further investigation by researching  APIs commonly used by malware.  

![image](https://github.com/user-attachments/assets/4727fedb-70e5-498b-a035-70292877250f)


6. Checking the strings
   
*  The unusual file names, paths, IP addresses, commands appear  under  the strings section.
*  Checking the following string (winrarfxmappingfile.tmp)  on TI platforms-"Hybrid-Analysis Sandbox" confirms that it has been previously flagged as suspecious file.

![image](https://github.com/user-attachments/assets/a9316db0-026e-4d89-8c55-e7e5a6528e9f)


7. Checking overlay section
   
overlay contains additional files required for the binary to carry out tasks. Adversaries embed a portion of malicious code within this section to execute the sample.
it has entropy rating of 8 out of 8 which confirms it is obfuscated/packed.


![image](https://github.com/user-attachments/assets/0dfb5e5a-1ec6-485a-a86f-5deb805c7b75)





