# LDAP-Attribute-Accounting-COMPOSER:  

LAAC will convert ldapsearch output to CSV records.  
Displays attributes used in LDAP of your choosing or from the common per-programmed set of attributes.  
LAAC will count the number of occurrences per attribute.  
The length of the name of each attribute.  
Normalizes LDAP records by including each attribute. In other words each CSV record will have a common set of attributes.  
The attributes in each CSV record will be placed in the correct order. It doesn't matter if the attribute is missing or empty the attributes will be in the same order for every record in the set.  
For missing attributes LAAC will will create a place holder.  
LAAC will normalize the data with in the record by eliminating invalid text in pure text fields. LAAC will not alter BLOBS, binary fields or extended attribute fields, certificate fields and including :: base64 encoded fields.   
The result of running LAAC against a dump of your LDAP repository is that the data is cleaned up, uniform and ready to be digested by a variety of tools. LAAC can digest any number of vendor repository data that can export OpenLdap format.  
  
Most common use cases:  
  
LAAC really sets the stage for the data to be imported into a statistical tool.   
Create Contingency or Cross tabulation assessments.  
I use it at least twice a week to find changes with in LDAP directory and the number of changes.  
Profile the number of occurrences per attribute.  
Profile how and where attributes are used.  
Profile the effectiveness of a global a change across thousands of objects.  
Bench mark the accuracy against ERP systems pushes into LDAP.  
In packages like R you then have another world available to you. For example the number of individuals per department,  
Number of departments per City or State,  
Measure different types of users that exist and subdivide per Group or Region and what ever else you can think of.  
The output can be used to correct missing data or data that has been entered incorrectly.  
The number of objects per type and the total as a whole.  
I use it alot in implementation that make heavy use of LDAP repositories, for example NAC, Authentication and Web SSO systems.  
  
Staple tools for example SED, AWK, UNIQ, SORT, CUT, PASTE, CSPLIT can be used to manipulate the data. The point is that it is consistent from the first to the last record.  
  
Sample Mocked up ldapsearch Data ouput  
  
 LDAPv3  
 base <DC=TheCompany,DC=Corp,DC=YourCompnay,DC=com> with scope subtree  
 filter: (objectclass=*)  
 requesting: givenname uid sn cn cn:: l st mail  
 with pagedResults control: size=1  
 Sosa Angel,staffer,users,Technical,DC=TheCompany,YourCompnay,com  
  
 version: 1  
  
 dn: uid=staffer,ou=users,ou=Technical,DC=TheCompany,DC=YourCompnay,DC=com  
 objectClass: top  
 objectClass: person  
 objectClass: Network Type  
 objectClass: employee  
 givenName: Angel  
 uid: staffer  
 sn: Sosa  
 cn: Angel Sosa  
 cn:: QW5nZWwgU29zYQo=  
 mail: MyMail@mail.com  
 l: ny  
 st: ny  
   
search result  
search: 9999999  
result: 0 Success  
pagedresults: cookie=12345678  
extended LDIF  
  
  
The result of the above after the datahas been processed by LAAC  
  
The header CSV rcord that names each collected field  
  
"dn: ","uid: ","sn: ","cn: ","cn:: ","mail: ","l: " 

 Sample Record Conversion = Please becareful of line wrap in the actual output there is never line wrap  
 
"CN=SOSA, Angel,OU=uid,OU=users,ou=Technical,DC=TheCompnay,DC=YourCompany,DC=com","Angel Sosa","staffer","Sosa","QW5nZWwgU29zYQo","MyMail@mail.com","ny","ny"

 If you summons a field that is not present in a record the field would be empty "Sosa","","MyMail@mail.com"

"CN=SOSA, Angel,OU=uid,OU=users,ou=Technical,DC=TheCompnay,DC=YourCompany,DC=com","Angel Sosa","staffer","Sosa","","MyMail@mail.com","ny","ny"

Visual output is below:
root@xtended-Inspiron-13-7359:~/Download/Projects/C++/Strings/35# clear;./strings_${rev}_combined  -a ../answer_file_lf_v1.ajs
Sat May  1 18:33:18 2021

   Answer File = 1, -a, ../answer_file_lf_v1.ajs, 1, 1, Desired Value = 25
   Answer File Containg Parameters And Values = 1, 25, -a, ../answer_file_lf_v1.ajs

   Parameters And Values Supplied = -g guided -f ../ad_11_modified.log -o ./del_35_combined_v1_a.csv -v null -b 50000000 -a ../answer_file_lf_v1.ajs -n no_prompt -p ../attribute_many_v1.ajs

   Option Format = 3,  Outer Counter = 17, Inner Counter = 17

   V1 =   0, = 3 ./strings_35_combined
   V1 =   1, = 3 -g
   V1 =   2, = 3 guided
   V1 =   3, = 3 -f
   V1 =   4, = 3 ../ad_11_modified.log
   V1 =   5, = 3 -o
   V1 =   6, = 3 ./del_35_combined_v1_a.csv
   V1 =   7, = 3 -v
   V1 =   8, = 3 null
   V1 =   9, = 3 -b
   V1 =  10, = 3 50000000
   V1 =  11, = 3 -a
   V1 =  12, = 3 ../answer_file_lf_v1.ajs
   V1 =  13, = 3 -n
   V1 =  14, = 3 no_prompt
   V1 =  15, = 3 -p
   V1 =  16, = 3 ../attribute_many_v1.ajs

   Rendered Analysis On ../ad_11_modified.log, File Analysis = DN: Count = 85,681, File Size = 660,237,352, DN: Furthest Apart = 3,250,012, Original Buffer Size = 50,000,000
   Source File = ../ad_11_modified.log, Pos = 660,237,352, Divisor = 13, Buffer Size = 50,000,000, Quotient = 50,787,488, Remainder = 8

   Using Named Attribute File
   Number Of Attributes To Process = 13


  Attribute Name = businessCategory:    , Attribute Length = 18   , Total Number Of Occurrence =    13,032
  Attribute Name = c:                   , Attribute Length = 3    , Total Number Of Occurrence =    12,018
  Attribute Name = co:                  , Attribute Length = 4    , Total Number Of Occurrence =    10,448
  Attribute Name = department:          , Attribute Length = 12   , Total Number Of Occurrence =    13,595
  Attribute Name = directReports:       , Attribute Length = 15   , Total Number Of Occurrence =     7,807
  Attribute Name = dn:                  , Attribute Length = 4    , Total Number Of Occurrence =    85,682
  Attribute Name = employeeNumber:      , Attribute Length = 16   , Total Number Of Occurrence =    13,205
  Attribute Name = employeeType:        , Attribute Length = 14   , Total Number Of Occurrence =    13,125
  Attribute Name = l:                   , Attribute Length = 3    , Total Number Of Occurrence =    13,959
  Attribute Name = manager:             , Attribute Length = 9    , Total Number Of Occurrence =     7,785
  Attribute Name = memberOf:            , Attribute Length = 10   , Total Number Of Occurrence =   413,096
  Attribute Name = name:                , Attribute Length = 6    , Total Number Of Occurrence =    66,264
  Attribute Name = objectCategory:      , Attribute Length = 16   , Total Number Of Occurrence =    66,162

 Total Runtime In Seconds = 99, End Time = Sat May  1 18:34:57 2021, Total Number Of Attributes = 13
