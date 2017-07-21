# Custom \[Data\] Objects \(CDO\)

![](/assets/CDO main.PNG)

Ah, the ever elusive CDO. It's a fancy term for a [table](https://en.wikipedia.org/wiki/Table_%28database%29) that allows contacts to have a one to many relationship. You can generally think of the Contact database as one table - it has the field headers \(name, email, address, etc\) and a list of the records, all on one page. You're not referencing from another table, say, what their phone number is; it's all on that one table for that record. The issue with this is, it restricts the type of data you can have per record.  In keeping with good [relational database](https://en.wikipedia.org/wiki/Relational_database) [design](https://en.wikipedia.org/wiki/Database_normalization), you should not have multivalue fields[^1] within your tables.

For example, a classic issue is purchases associated with each contact, because each contact can have multiple \(more than one\) purchases. You wouldn't have one field named **Item Purchased** and then have the following as the value: **Widget 1, Widget 2, Widget 3, Widget 4**. That makes it difficult to query, update, aggregate, and impossible to add any additional information to the specific widget that they bought. Say you'd like to know what day they purchased Widget 2. Where are you going to store that?

Custom Objects to the rescue! Within Eloqua, you can create the schema for any additional tables \(Objects\) that you want to link to a contact. Now you can store that purchase data in their own respective records, and link those back to the single contact.

[^1]: [Atomicity](https://en.wikipedia.org/wiki/First_normal_form)

