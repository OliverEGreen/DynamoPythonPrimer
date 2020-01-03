---
description: 'What''s up, Doc? Get to know these important handles you''ll use all the time!'
---

# 4.3 Doc, UIDoc, App, UIApp

#### Boilerplate Code

As seen in the chapter on [boilerplate code](../getting-started/boilerplate-setup-code.md), Revit boilerplate code often requires setting up handles to the Revit application and document \(doc, uidoc, app, uiapp\). 

But why is this?

#### Application and Document

This area of the API can seem a little confusing at first. Questions abound: can't Revit just work out which document \(i.e. model\) I'm in? Why do I have a Document and a UIDocument? Why do I refer to an Application - isn't the application Revit?  
  
These are good questions. Luckily, Revit's [API guidance](http://help.autodesk.com/view/RVT/2014/ENU/?guid=GUID-B5E019A8-02F1-49A2-9EB8-449FB99D1E7C) has a few answers for us: 

> The top level objects in the Revit Platform API are application and document. These are represented by the classes Application, UIApplication, Document and UIDocument.
>
> * **The application object refers to an individual Revit session**, providing access to documents, options, and other application-wide data and settings.
>   * Autodesk.Revit.UI.UIApplication - provides access to UI-level interfaces for the application, including the ability to add RibbonPanels to the user interface, and the ability to obtain the active document in the user interface.
>   * Autodesk.Revit.ApplicationServices.Application - provides access to all other application level properties.
> * **The document object is a single Revit project file** representing a building model. Revit can have multiple projects open and multiple views for one project.
>   * Autodesk.Revit.UI.UIDocument - provides access to UI-level interfaces for the document, such as the contents of the selection and the ability to prompt the user to make selections and pick points
>   * Autodesk.Revit.DB.Document - provides access to all other document level properties

To summarise this:

* You can have more than one Revit document open at a time \(including .rfa files\), so you need to specify which document you're targeting.
* You can also have more than one running instance of the Revit application, so you'll need to specify the application you're targeting. 
* The Document/UIDocument and Application/UIApplication splits are decisions made by the designers of the API. The UI classes generally refer to user-interface elements or those which require interaction \(such as prompting the user to select elements in the main Revit window.\)

The main thing to know is that the doc, uidoc, app and uiapp handles in our boilerplate code are indispensable for many operations involving editing a Revit document. For instance, want to delete something? You'll need to reference which  document you're deleting something from!

