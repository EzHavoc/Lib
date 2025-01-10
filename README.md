1> CHANGING THE FILE OR FODLER OWNERSHIP 
1. Create a Folder 
2. Right Click on the Folder 
3. Click on the Properties
4. Click on Security
5. Click on the Advanced Option 
6. Click on Change
7. Click on Advanced 
8. Click on Find Now
9. Click on Ok
10. Click on Apply
11. Click on Ok

2> HOW TO PROTECT MS WORD OR PDF DOCUMENT WITH PASSWORD
1. Create a Word Document
2. Open the Document
3. Click on File (After this Click on Save As PDF){In case of a PDF}
4. Click on Info
5. Click on Encrypt With Password
6. Set the Password

3> SECURING ACCOUNTS USING STRONG PASSWORDS
import re
	def validate_password(password):
		if len(password)<8:
			return false
		if not re.search(r'[A-Z]',password):
			return false
		if not re.search(r'[a-z]',password):
			return false
		if not re.search(r'\d',password):
			return false
		if not re.search(r'[!@#$%^&*();'/.,<>?:"]',password):
			return false
		return True

	password=input("Input Your Password:")
	is_valid=validate_password(password)
		if is_valid:
			print("Strong Password")
		else:
			print("Password Does Not Meet The Requirements")
4> HOW TO ENCRYPT FILES IN WINDOWS
1. Create a Folder
2. Create a File in the  Folder 
3. Right Click on the Folder 
4. Click on the Properties
5. Click on Advanced 
6. Click on Encrypt the Contents to secure Data
7. Click on Ok
8. Click on Apply

1. Click on Start
2. Click on Family and Other Users
3. Click on Add Someone Else on the PC
4. Click on I dont have the Person's ID Info
5. Click on Continue without Microsoft Account 
6. Give Username
7. Give Password
Sign out from the Administrator ID
Sign in the Newly Created Account 
Access the Folder from the User directory 

5>HOW TO RECOVER PERMANENTLY DELETED FILES IN WINDOWS
1. Create a Folder
2. Create a file inside the Folder
3. Go to Control Panel
4. Go to File History 
5. Click on Run Now
6. Delete the File Permanently 
7. Click on Start
8. Search Restore File wth File History 
9. Open the Dekstop Folder
10. Click on Restore to Original Location
