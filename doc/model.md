Project model
=============

UML schema
----------

To see a UML diagram of the entities of the project, go to yuml.me and copy-paste the following entries:
```
[User]1<->*[PhoneNumber]
[User]*->1[Address]
[Address]*<-->1[Country]
```

Entities detailed
-----------------
**User:** A friendly application customer. Might be you or your Product Owner

**Address:** The physical place where a User lives. Several Users can live in a single Address

**Country:** The country where is located the Address. Allows Addresses to be split for the different nationalities.

**Phonenumber**: The number to contact Users. Users can have multiple PhoneNumbers. BEWARE : PhoneNumbers are NOT linked
to Countries.
