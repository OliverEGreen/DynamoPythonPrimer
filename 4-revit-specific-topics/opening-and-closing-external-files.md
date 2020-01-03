---
description: Opening and closing files 'headlessly' unlocked some powerful workflows
---

# 4.9 Opening & Closing External Files

**Batch Processing Revit Files**

One of the most powerful aspects of Revit’s API is the ability to open, close, edit and save documents in an automated way. Best of all, we can achieve this 'headlessly', which means opening the Revit [document's database](introduction-to-revits-api.md#introduction-to-revits-api) without any GUI component. Generally speaking, working with documents in this way is perhaps 20-30 times faster than if a user were doing so - this means we can build custom behaviours that involve rapidly batch processing many files.

#### Targeting Many Documents

In a nutshell, batch-processing files means we'll undertake the same series of behaviours on a list of document objects, looping through each one in turn. In rough terms, this means the following:

1. Create a list of Revit FilePath objects, based on the file paths of your target documents.
2. Iterate through this list.
3. Use the Revit API's Open\(\) method to open the file and create a handle for this open document.
4. Open a transaction which targets our newly-opened document via its handle.
5. Make various API calls as desired, depending on what you want to do.
6. Close the Transaction we opened in step 4
7. Close the document, saving it if desired.

#### Worked Example

Let's say I have a folder of Revit Family \(.rfa\) files and I want to open each one in turn and report back the number of dimensions in that file.

In practice, this looks like:

```python
#Boilerplate Code


```

  


