# CTF-Write-Up-2
CTF Codepath capture_Bolivia - 4.10 - Mimics
CTF-WriteUp-02

CTF Codepath capture_Bolivia - 4.10 - Mimics

note: The key to everything is the truth, no matter how wild it may be. 
You must go the length to find it. 

Step 1: I gathered a list of SQL Injections queries from an online search, combined the 
	queires and saved the list in a  .txt file. 

Step 2: I opened the website and put the listed admin name in the input field to 
	get the data in proxy(Burp Suite). 

Step 3: In the Proxy tab under HTTP history I identified the POST request and 
	transfered it to the Intruder tab.I cleared all the fields subject to intrusion 
	the proxy and added the target to the name field.

Step 5: I located the text file in my local drive and loaded it in the Payload Settings 
	section with a [Simple list] selected as the method of intrusion. 

Step 6: I examined the results of the intrusion queries search for a query length that 
	may have retrieved relevant data from the database. The query ["or"1"="1"#] 
	was able to get the data contained in the database and give further hint
	flag: *CTF{} <-- fill in the flag with the current database name!] to get the hidden flag.

Step 7: The Note says : The key to everything is the truth, no matter how wild it may be. 
	You must go the length to find it. This is an indication that the max_length of the input
	field is fixed and must be manipulated in the browser dev tool to enter a SQL Injection 
	longer than the fixed input length.

Step 8: Enter a SQL Injection Query to retrieve the Database name.
		>> "or"1"="1"UNION SELECT 1,2,3,4,5,database()#


