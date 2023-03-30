# CTF-Write-Up-2
CTF Codepath capture_Bolivia - 4.10 - Mimics

note: The key to everything is the truth, no matter how wild it may be. 
	You must go the length to find it. 

Step 1: I gathered a list of SQL Injections queries from an online search, combined the 
	queires and saved the list in a  .txt file. 

Step 2: I opened the website and put the listed admin name in the input field to 
	get the data in proxy(Burp Suite). 
![Screenshot (30)](https://user-images.githubusercontent.com/55906428/228715032-f5d8ea95-da8f-44c8-9225-caaf6db92698.png)

Step 3: In the Proxy tab under HTTP history I identified the POST request and 
	transfered it to the Intruder tab.I cleared all the fields subject to intrusion 
	the proxy and added the target to the name field.
	
![Screenshot (31)](https://user-images.githubusercontent.com/55906428/228715100-8b08c4e6-4c0d-48fb-a5b2-65e7bd07bc8f.png)

![Screenshot (32)](https://user-images.githubusercontent.com/55906428/228715124-ff2592dc-b5a2-44fc-b889-c2f8207239ca.png)

Step 5: I located the text file in my local drive and loaded it in the Payload Settings 
	section with a [Simple list] selected as the method of intrusion. 
	
	
![Screenshot (33)](https://user-images.githubusercontent.com/55906428/228715168-9adb26a0-f820-4710-a9ee-0ba85d419bca.png)

Step 6: I examined the results of the intrusion queries search for a query length that 
	may have retrieved relevant data from the database. The query ["or"1"="1"#] 
	was able to get the data contained in the database and give further hint
	flag: *CTF{} <-- fill in the flag with the current database name!] to get the hidden flag.
	
![Screenshot (34)](https://user-images.githubusercontent.com/55906428/228715205-c7947f28-87ce-4c71-9d33-80b39036ead7.png)

Step 7: The Note says : The key to everything is the truth, no matter how wild it may be. 
	You must go the length to find it. This is an indication that the max_length of the input
	field is fixed and must be manipulated in the browser dev tool to enter a SQL Injection 
	longer than the fixed input length.
	![Screenshot (35)](https://user-images.githubusercontent.com/55906428/228715312-d0cacdcd-ab6e-458e-a564-d7c09c66d996.png)

Step 8: Enter a SQL Injection Query to retrieve the Database name.
		>> "or"1"="1"UNION SELECT 1,2,3,4,5,database()#
		


![Screenshot (36)](https://user-images.githubusercontent.com/55906428/228715545-f8abc05a-9adf-4241-be39-2395b844eb15.png)

