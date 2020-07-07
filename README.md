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
Measure different types of users that exist and subdivide per Group or Region and what everelseyou can think of.
The output can be used to correct missing data or data that has been entered incorrectly.
The number of objects per type and the total as a whole. 
I use it heavenly in implementation that make heavy use LDAP repositories, for example NAC, Authentication and Web SSO systems.

Staple tools for example SED, AWK, UNIQ, SORT, CUT, PASTE, CSPLIT can be used to manipulate the date. The point is that it is consistent from the first to the last record.

Sample Mocked up ldapsearch Data ouput

# LDAPv3
# base <DC=TheCompany,DC=Corp,DC=YourCompnay,DC=com> with scope subtree
# filter: (objectclass=*)
# requesting: givenname uid sn cn cn:: l st mail
# with pagedResults control: size=1
# Sosa Angel,staffer,users,Technical,DC=TheCompany,YourCompnay,com

# version: 1

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
 
# search result
search: 9999999
result: 0 Success
# pagedresults: cookie=12345678
# extended LDIF
#

The result of the above after the datahas been processed by LAAC
# The header CSV rcord that names each collected fielf

"dn: ","uid: ","sn: ","cn: ","cn:: ","mail: ","l: "

# Sample Record Conversion = Please becareful of line wrap in the actual output there is never line wrap
"CN=SOSA, Angel,OU=uid,OU=users,ou=Technical,DC=TheCompnay,DC=YourCompany,DC=com","Angel Sosa","staffer","Sosa","QW5nZWwgU29zYQo","MyMail@mail.com","ny","ny"

# If you summons a field that is not present in a record the field would be empty "Sosa","","MyMail@mail.com"
"CN=SOSA, Angel,OU=uid,OU=users,ou=Technical,DC=TheCompnay,DC=YourCompany,DC=com","Angel Sosa","staffer","Sosa","","MyMail@mail.com","ny","ny"
