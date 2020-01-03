---
description: Using Transactions is easy and you won't get very far without them!
---

# 4.8 Working With Transactions

#### Revit is a Database

In the [introduction](introduction-to-revits-api.md#introduction-to-revits-api), we covered how Revit is best thought of as a giant database program. Changes to this database need to be carefully ordered, the process needs to be managed and checked \(for validity against schemas and for legality against the design of Revit's API\). All of this is handled by Revit's native[ Transaction](https://apidocs.co/apps/revit/2019/308ebf8d-d96d-4643-cd1d-34fffcea53fd.htm) API.

Any code that is intended to change the Revit document's database needs to be 'wrapped in a transaction'.

#### Dynamo's TransactionManager

When coding directly for the Revit API \(either in a Macro or a C\# add-in\) we can simply start a new transaction by instantiating  a new object of the Transaction class using code and calling its Start\(\) method. However, in the Dynamo context, we'll need to handle this differently. 

The TransactionManager is a part of Dynamo's API that handles changes made to the Revit document's database from within the Dynamo application. We can start a transaction like so:

```python
#Boilerplate Code

#To open a new transaction, we need to use the TransactionManager class
#Which takes the current document's handle as an argument
TransactionManager.Instance.EnsureInTransaction(doc)

#The following method will close the transaction and confirm any changes
#made to the Revit document's database.
TransactionManager.Instance.TransactionTaskDone()
```

Between these two method calls, you'll need to put any code that's affecting the Revit document's database. This could be:

* Creating a new sheet
* Updating a parameter value
* Modifying an element's colour overrides

In short, editing the Revit document in \(nearly\) anyway requires an open transaction.

#### Structuring Transactions

It's worth knowing that it's possible to enable more advanced workflows by structuring edits to the database using Transactions, TransactionGroups and SubTransactions.

For more information, TheBuildingCoder blog has an excellent in-depth section on carrying out fancy transaction behaviours.[ Read more here](https://thebuildingcoder.typepad.com/blog/about-the-author.html#5.53).



