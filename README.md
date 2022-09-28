# Registration
This is a program about Registration and login credentials using file handling
import re

def solve(s):
    pat = "^[a-zA-Z]+@[a-zA-Z0-9]+\.[a-z]{1,3}$"
    if re.match(pat,s):
       return True
    else:
        print("invalid username")
        register()
        

def register():
    
    
    db=open('database.txt','r')
    u=[]
    username=input("create username:")
    solve(username)
    db=open("database.txt",'a')
    db.write(username)
    db.close()
    pass
def password():
    l, u, p, d = 0, 0, 0, 0
    password1=input("create password:" )
    password2=input("confirm password:")
    if len(password1)<=5 or len(password2)>=16:
        print("password length is too short or too long")
        register()
    elif password1 != password2:
        print("Passwords do not match,restart")
        register()
    elif password1==password2:
   
        for i in password1:
    
    		# counting lowercase alphabets
        	if (i.islower()):
        			l+=1		
        
        		# counting uppercase alphabets
        	if (i.isupper()):
        			u+=1		
        
        		# counting digits
        	if (i.isdigit()):
        			d+=1		
        
        		# counting the mentioned special characters
        	if(i=='@'or i=='$' or i=='_' or i=='!' or i=='#' or i=='%'):
        			p+=1		
    if (l>=1 and u>=1 and p>=1 and d>=1 and l+p+u+d==len(password1)):
        print("Valid Password")
        print("Success!")
    else:
        print("Invalid Password")
        register()
        password()
    db=open("database.txt",'a')
    db.write(password1)
    db.close()
    pass

def login():
    username=input("enter your username:")
    password1=input("enter your password1")
    success=False
    db=open("database.txt",'r')
    for i in db:
        a=username
        b=password1
        if (a==username and b==password1):
            success=True
            break
    db.close()
    if (success):
        print("login successful")
        access()
    else:
        print("Wrong credentials")
        print("retry")
        access()
    pass

def access():
    option=input("login or Register:")
    if (option=="Register"):
       print("Create a new account")
       register()
       password()
    else:
     if (option=="login"):
        login()
    pass
access()
login()
register()
password()        
