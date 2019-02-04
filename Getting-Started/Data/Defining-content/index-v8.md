---
versionFrom: 8.0.0
---

# Defining content

*Here you'll find an explanation of how content is defined in v8.*

Before a piece of content can be created it needs to be defined. That is why, when opening a blank installation of Umbraco, it is not possible to create content in the __Content__ section. All content needs a blueprint that holds information about what kind of data can be stored on the content node, which editors are used, how it is organized, where in the structure it is allowed and so forth. This blueprint or definition is called a Document Type.

## What is a Document Type?
In its most basic form a document type is a form containing fieldsets (or groups) where you can apply rules about where the content can be created, which template(s) are allowed, backoffice icon and so forth.

Document Types can define entire pages or more limited content that can be reused on other nodes ie. a SEO group. This means that you are in complete control of what type of content can be created where.

### Properties
Each field on a Document Type is called a property. A property is given a name, an alias (used to output the properties content in a template) and an editor. The editor determines what type of data the property will store and the input method. There are a wide range of editors available out of the box (textstring, Rich text, media picker and so forth) and you can customize and add additional editors.

Some editors require configuration, a configured editor is saved as a Data Type and can be re-used for multiple properties and document types. These can be seen in the __Settings__ section under __Data Types__.

## Creating a Document Type
A Document Type is created in the settings section using the Document Type editor.

Go to the __Settings__ section in the backoffice. On the __Document Types__ node click the menu icon (•••) to bring up the context menu. Here choose __Document Type__. This will create a new Document Type with a template (can be found under __Templates__ in the __Settings__ sections) that will be assigned as the default template for the document type.

![Creating a Document Type](images/v8Screenshots/createDoctype.PNG)
_You can also choose to create a Document Type without a template and create folders to organize your Document Types._

You can also use compositions to create a new document type. Compositions allows you to inherit properties from other groups. When using a mixed setup, you can take advantage of nesting and use compositions by visiting the Structure group. A checklist like this should appear:

![Creating a Compositions](images/v8Screenshots/compositions.PNG)

The grayed out Document Type Composition Master is a parent to the particular Document Type we are looking at. By default, this means that this Document Type will inherit the properties from the Master Document Type and unless we move it to another location, this is how it will stay. The other document type that is checked is the Banner type. This means that the Document will also inherit the properties from the Banner Type into this Document Type.

### Defining the root node
First we're prompted to give the Document Type a name. This first Document Type will be the root node for our content, name it "Home".

![Naming a Document Type](images/v8Screenshots/homePage.PNG)
_Notice that the alias of the Document Type is automatically generated based on the name. If you want to change the alias simply click the "lock" icon._

Having a root node makes it easy to query content as you know everything will be under the root node.

To set an icon for the Document Type click the document icon in the top left corner. This will open the icon select dialog. Search for _Home_ and select the icon. This icon will be used in the content tree, choosing appropriate icons for your content nodes is a good way to give editors a better overview of the content tree.

![Choosing an icon for the Document Type](images/v8Screenshots/docTypeIcon.PNG)

Go to the __Permissions__ tab and tick the __Yes - allow content of this type in the root__ checkbox and save the Document Type by clicking save in the bottom right corner.

![Allow at root](images/v8Screenshots/docTypePermissions.PNG)

### Creating the root node
Now go to the __Content section__, click on the menu icon next to __Content__ and Select the Home Document Type. We'll name it "Home" and click the __Save and Publish__ button.

![First content created](images/v8Screenshots/createHomepage.PNG)

As we haven't created our own properties all we can see on the "Home" node is the Properties tab which contains the default properties that are available on all content in Umbraco.

Let's add some properties of our own.

### Groups and properties
Go to the __Settings section__, expand __Document Types__ by clicking the arrow to the left and select the __Home__ Document Type.

#### Adding groups
Before we start adding properties to the Document Type we need to create a group to hold the property.

Click __Add group__ and name the group "Content".

![Creating groups](images/v8Screenshots/createGroup.PNG)
_If you have multiple groups and/or properties you can order them with drag and drop or by entering a numeric sort order value. This is done by clicking __Reorder__._

#### Adding properties
Now that we have created a group we can start adding properties. Let's add a Rich Text editor to the Content group.

Click the __Add property__ link in the Content group. This opens the property settings dialog. Here you can set the meta data for each property (name, alias, description), choose which data type/property editor to use and add validation if needed.

Give the property a name, the name will be shown to the editor so make relevant and easy to understand. Notice the alias is automatically generated based on the name. We'll name this "Body Text".

![Adding a property](images/v8Screenshots/addproperty.PNG)

##### Keyboard Shortcuts
Keyboard shortcuts are available when you are working with the Document Type editor. To see which shortcuts are available simply click <kbd>ALT</kbd> + <kbd>SHIFT</kbd> + <kbd>K</kbd>.

##### Property editors
Clicking __Add editor__ will open the Select editor dialog. Here you can choose between all the __Available editors__ (this will create a new configuration) or __Reuse__ already configured editors. To make it easier to find what you need use the search field to filter by typing "Rich". Filtering will display configured properties first (under Reuse) and all available editors under that.

Select the __Rich Text editor__ under Available editors.

![Choosing the Rich Text editor](images/v8Screenshots/selectEditor.PNG)

This will let you configure the editor settings - the Rich Text editor for this property. Notice that the name of the Data Type (_Home - Body Text - Rich Text editor_) is based on the name of the Document Type, the name of the property and the property editor. Let's rename it to "Simple Rich Text editor" and only select the most necessary options.

* _bold_
* _italic_
* _alignLeft_
* _alignCenter_
* _link_
* _umbMediaPicker_

When you are happy with the settings click __Submit__.

Checking the __Mandatory__ checkbox makes the property mandatory and the content cannot be saved if no value is entered (into the Richtext editor in this case). You have the option to add additional validation by adding a regular expression in the __Validation__ field.

Submit the property and save the Document Type. If you go to the __Content section__ and click on the Home node you will now see the Content group with the Body Text property.

### Defining child nodes
Next up we'll create a simple text page Document Type that will be used for subpages on the site.

Go back to the __Settings section__ and create a new Document Type and name it "Text Page". Add a group called "Content"
and this time we'll add two properties. First make a property called summary using the __Textarea__ editor and secondly create a property called "Body Text" and reuse the __Simple Rich Text Editor__ Data Type.

### Creating child nodes
Before we can create a Text Page in the __Content__ section, we need to allow the Text Page Document Type to be created as a child node to the Home node. Select the Home Document Type and go to the __Permissions__ group. Click __Add child__ and select Text Page.

![Allowing child nodes](images/v8Screenshots/setPagePermissions.PNG)

Go to the __Content__ section and click the menu icon (•••) next to the *Home* node and select the Text page Document Type. We'll name the page "About us". We now have a very basic content structure.

![Basic content structure](images/v8Screenshots/createAboutUs.PNG)

Document Types are very flexible and can be used in a myriad of ways from defining a piece of reusable content or an entire page, to acting as a container or repository.
