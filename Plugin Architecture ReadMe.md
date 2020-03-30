# Plugin Architecture Guide

INK editor plugin architecture is divided into two APIs i.e. `core` and `draw`. Both APIs contains number of methods for Plugin Developer to use for performing different functionalities.


# Draw API `(draw)`

Draw API contains methods for developing UI/UX of the sidebar tab of plugin. Following are the available functionalities and their descriptions:

* [Create Form Element](#addFormElement) : `addFormElement`
* [Create an image banner](#addBanner) : `addBanner`
* [Insert horizontal divider](#addHorizontalDivider) : `addHorizontalDivider`
* [Insert a Label](#addLabel) : `addLabel`
* [Loading](#setLoading) : `setLoading`
* [Empty State](#addEmptyState) : `addEmptyState`
* [Button element](#addButton) : `addButton`  <!-- * [Expand/Collapse Element](#addExpandableList) : `addExpandableList` -->
* [User Profile Display](#addUserProfileDisplay) : `addUserProfileDisplay`
* [Style Container Element](#containerStyles) : `containerStyles`
* [Labeled Value](#labeledValue) : `labeledValue`
* [Custom Container](#customContainer) : `customContainer`
* [Clear the draw area](#clear) : `clear`

## <a id="addFormElement"></a>Create Form Element

Used to create form elements.

**Available in** : `draw`

**Method Name** : `addFormElement`

**Options** : 
```js
{ 
  type: "input" | "checkbox" | "dropDown" | "btn", 
  name : String, 
  defaultValue: String | Number, 
  options: Array, 
  styles: Object, 
  containerId: String,
}
```
`type` and `name` are mandatory fields.


**Example** : 
```js
draw.addFormElement({  //creates a dropdown element
  name: "Type of",
  type: "dropDown",
  options: [
    "new",
    "old",
    "semi-new",
    "semi-old",
    "genormous"
  ],
});
```
---
## <a id="addBanner"></a>Create an Image Banner

Used to create image banner.

**Available in** : `draw`

**Method Name** : `addBanner`

**Options** : 
```js
{ 
  src: String,
  styles: Object, 
  containerId: String,
}
```
`src` is mandatory field.

**Example** : 
```js
draw.addBanner({
  src: "https://picsum.photos/300/150",
  styles: {
    border: "2px solid #000",
  }
});
```
---
## <a id="addHorizontalDivider"></a>Insert Horizontal Divider

Adds a horizontal divider line.

**Available in** : `draw`

**Method Name** : `addHorizontalDivider`

**Options** : 
```js
{ 
  styles: Object, 
  containerId: String,
}
```
**Example** : 
```js
draw.addHorizontalDivider();
```

---
## <a id="addLabel"></a>Insert a Label

Adds a label.

**Available in** : `draw`

**Method Name** : `addLabel`

**Options** : 
```js
{ 
  text: String,
  styles: Object, 
  containerId: String,
}
```
`text` is mandatory field.

**Example** : 
```js
draw.addLabel({
 text: "Some text here",
});
```

---
## <a id="setLoading"></a>Loading

Adds a loader.

**Available in** : `draw`

**Method Name** : `setLoading`

**Options** : 
```js
{ 
  styles: Object, 
  status: Boolean,
}
```

**Example** : 
```js
draw.setLoading({ status: true });
```

---
## <a id="addEmptyState"></a>Empty State

Adds an Empty State.

**Available in** : `draw`

**Method Name** : `addEmptyState`

**Options** : 
```js
{ 
  text: String,
  styles: Object, 
  containerId: String,
}
```
`text` is mandatory field.

**Example** : 
```js
draw.addEmptyState({
  text: "Some text here!"
});
```
---
## <a id="addButton"></a>Button element

Adds a Button element.

**Available in** : `draw`

**Method Name** : `addButton`

**Options** : 
```js
{ 
  label: String,
  styles: Object, 
  clickEvent: String, 
  containerId: String,
}
```
`label` is mandatory field.

**Example** : 
```js
draw.addButton({
  label: "Button Text",
  styles: { fontWeight: "normal" },
  clickEvent: "clickHandler"
});
```
---
## <a id="addUserProfileDisplay"></a>User Profile Display

Component for user profile display

**Available in** : `draw`

**Method Name** : `addUserProfileDisplay`

**Options** : 
```js
{ 
  imageSrc: String,
  userTitle: String, 
  userEmail: String, 
  clickEvent: String, 
  closable: Boolean,
  containerId: String,
}
```
`imageSrc`, `userTitle` and `userEmail` are mandatory field.

**Example** : 
```js
draw.addUserProfileDisplay({
  imageSrc: "https://sample.com/23lksdjf.jpg",
  userTitle: "John Doe",
  userEmail: "abc@xyz.com",
  clickEvent: `clickHandler`,
  closable: true,
});
```
---
## <a id="containerStyles"></a>Style Container Element

This API is used to apply styles to root container or a custom container.

**Available in** : `draw`

**Method Name** : `containerStyles`

**Options** : 
```js
{ 
  styles: Object,
  containerId: String,
}
```
`styles` is mandatory field.

**Example** : 
```js
draw.containerStyles({
  styles: {
    fontWeight:'bold'
  },
});
```
---
## <a id="labeledValue"></a>Labeled Value

Component to display a labeled data.

**Available in** : `draw`

**Method Name** : `labeledValue`

**Options** : 
```js
{ 
  label: String,
  value: String,
  styles: Object,
  containerId: String,
}
```
`label` and `value` are mandatory field.

**Example** : 
```js
draw.labeledValue({
  label: 'Some Title:',
  value: "some data",
  styles: {
    marginTop: '10px',
  }
});
```
---

## <a id="customContainer"></a>Custom Container

This API is used to create a custom container with unique containerId which we can use later to populate this container.

**Available in** : `draw`

**Method Name** : `customContainer`

**Options** : 
```js
{ 
  containerId: String,
  styles: Object,
}
```
`containerId` is mandatory field.

**Example** : 
```js
draw.customContainer({
  containerId: 'content',
  styles: {
    display: 'flex',
  }
})
```
<!-- --- -->
<!-- ## <a id="addExpandableList"></a>Expand/Collapse Element

Adds a Button element.

**Available in** : `draw`

**Method Name** : `addExpandableList`

**Options** : 
```js
{ 
  title: String,
  fields: Array,
  group: String,
  btn: String, 
  clickEvent: String, 
}
```
`label` is mandatory field.

**Example** : 
```js
draw.addExpandableList({
  title: URL,
  fields: [
    { label: "Site Title:", value: name },
    { label: "Post Count:", value: post_count },
    { label: "Launch Status:", value: launch_status },
  ],
  containerId: 'content',
  btn: 'Create Post',
  clickEvent: ID,
  group: 'grouped-sites',
});
``` -->

---
## <a id="clear"></a>Clear

This API is used to clear the root container or the custom container if a containerId is provided.

**Available in** : `draw`

**Method Name** : `clear`

**Options** : 
```js
{ 
  containerId: String
}
```

**Example** : 
```js
draw.clear();

//OR

draw.clear({
  containerId: 'content'
});
```


# Core API `(core)`

Core API contains methods for the core functionalities exposed for plugin developer. Following are the available functionalities and their descriptions:

* [Change User Settings](#userSettings) : `userSettings`
* [Get User settings](#getUserSettings) : `getUserSettings`
* [Display a notification](#notify) : `notify`
* [Set Clipboard Text](#setClipboardText) : `setClipboardText`
* [Get Clipboard Text](#getClipboardText) : `getClipboardText`
* [Set Local Store](#setLocalStore) : `setLocalStore`
* [Get Local Store](#getLocalStore) : `getLocalStore`
* [Open Url](#openUrl) : `openUrl`
* [Get Article](#getArticle) : `getArticle`
* [Set Cloud Store](#setCloudStore) : `setCloudStore`
* [Get Cloud Store](#getCloudStore) : `getCloudStore`



## <a id="userSettings"></a>Change User Settings

Update current user editor settings.  

**Available in** : `core`

**Method Name** : `userSettings`

**Options** : 
```js
{ 
  colorblind: Boolean, 
  dyslexia: Boolean, 
  editorFocusMode: Boolean, 
  editorTwMode: Boolean, 
  theme: 1 | 2,   // 1 for light theme and 2 for dark theme
}
```

**Example** : 
```js
core.userSettings({
  colorblind: false, 
  dyslexia: false, 
  editorFocusMode: true, 
  editorTwMode: false, 
  theme: 1,   // 1 for dark theme and 2 for light theme
});
```
---
## <a id="getUserSettings"></a>Get User Settings

Retrieve current user editor settings and returns a promise.  

**Available in** : `core`

**Method Name** : `getUserSettings`

**Example** : 
```js
core.getUserSettings().then(settings=>{
  console.log("Current Editor Settings: ", settings);
});
```

---
## <a id="notify"></a>Notifications

Display a notification in editor.  

**Available in** : `core`

**Method Name** : `notify`

**Options** : 
```js
{ 
  title: String, 
  message: String, 
  status: "warn" | "error" | "success"
}
```

**Example** : 
```js
core.notify({
  title: "Task", 
  message: "Task Completed Successfully!", 
  status: "success",
});
```

---
## <a id="setClipboardText"></a> Set Clipboard Text

Copy text to clipboard.

**Available in** : `core`

**Method Name** : `setClipboardText`

**Options** : 
```js
{ 
  text: String, 
}
```

**Example** : 
```js
core.setClipboardText({
  text: "some text here!"
});
```
---
## <a id="getClipboardText"></a> Get Clipboard Text

Retrieve text from user's clipboard and it returns a promise.

**Available in** : `core`

**Method Name** : `getClipboardText`

**Example** : 
```js
core.getClipboardText().then(text=>{
  console.log(`Current Clipboard Text : ${text}`);
});
```

---
## <a id="setLocalStore"></a> Set Local Store

This API sets data in localstorage using specific plugin ID. So that plugin can only recieve its own data on retrieval. 

**Available in** : `core`

**Method Name** : `setLocalStore`

**Options** : 
```js
{ 
  any: any, 
  any: any, 
  any: any, 
}
```

**Example** : 
```js
core.setLocalStore({
  someData: "some data here!"
});
```

---
## <a id="getLocalStore"></a> Get Local Store

This API gets data from localstorage using specific plugin ID. 

**Available in** : `core`

**Method Name** : `getLocalStore`

**Example** : 
```js
core.getLocalStore().then(data=>{
  console.log("Plugin's Local Stored Data : ", data);
});
```

---
## <a id="openUrl"></a> Open Url
This API can be used for opening a url in desktop's default manner. (For example, mailto: URLs in the user's default mail agent).

**Available in** : `core`

**Method Name** : `openUrl`

**Options** : 
```js
{ 
  url: String
}
```

**Example** : 
```js
core.openUrl({
  url: "https://google.com",
});
```
---
## <a id="getArticle"></a> Get Article

This API retrieves article content from editor in html or markdown format. 

**Available in** : `core`

**Method Name** : `getArticle`

**Options** : 
```js
{ 
  type: "html" | "md"
}
```

**Example** : 
```js
core.getArticle({ type: "html" }).then(html => {
  console.log(`Article content in html format: ${html}`)
});
```
---
## <a id="setCloudStore"></a> Set Cloud Store

This API is used to save JSON data in the cloud storage available for every plugin. (limit: max 1mb JSON data);

**Available in** : `core`

**Method Name** : `setCloudStore`

**Options** : 
```js
{ 
  any: any, 
  any: any, 
  any: any, 
}
```

**Example** : 
```js
core.setCloudStore({ 
  someKey: "Some Data",
  anotherKey: "Some More Data",
});
```
---
## <a id="getCloudStore"></a> Get Cloud Store

This API is used to retrieve saved JSON data in the cloud storage.

**Available in** : `core`

**Method Name** : `getCloudStore`

**Example** : 
```js
core.getCloudStore().then(data => {
  console.log(`My cloud store data: `,data)
});
```
---

# Base Plugin Starter Code Setup

Folowing is the base starter code setup for plugin developer.


```js

class MyPlugin{

  constructor({ core, draw, id }) {  //Retrieve Main APIs (core and draw) from constructor
    
    this.id = id;
    this.draw = draw;
    this.core = core;
    this.init = this.init.bind(this);
 
  }

  init() {
    //This function will be called ones the plugin is integrated and ready!
    const { addBanner, addEmptyState } = this.draw;
    const { notify } = this.core;
    
    //creating the MyPlugin banner
    addBanner({
      src: "https://picsum.photos/300/150",
    });
    
    //showing empty state
    addEmptyState({
      text: "No Data Available!",
    });
    
    //notifying the successful loading
    notify({
       title: "MyPlugin", 
        message: "MyPlugin Loaded Successfully!", 
        status: "success",
    });
  }

}

module.exports = MyPlugin;
```


## `init()`
This function will be called when the plugin is loaded and ready. It should be the entry point for all the plugin logic. 
