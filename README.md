# BT5 Menu

```
By boctulus
```

This Menus was adapted to FeatherIcons but it's mostly icon-library independent.

The AsideMenu class is pretty easy to use:

```
const menu_config = {
    "starts_expanded": false,
    "options_starts_expanded": false,  /* it has only effect if starts_expanded is true */
    "role": "current"
};

const menu_items = { 
    current:  [
        { 
          text: "Exam list", 
          link: "/dashboard/exam-list", 
          icon: "heart"
        },
        { text: "Fast reporting", link: "/dashboard/fast-reporting", icon: "zap" },
        { text: "Settings",  
          childs: [ 
            { text: "Item 1", link: "/dashboard/settings/item1", icon: "sliders" }, 
            { text: "Item 2", link: "/dashboard/settings/item2", icon: "sliders" }, 
            { text: "Item 3", link: "/dashboard/settings/item3", icon: "sliders" }
          ],
          icon: "sliders"
        },
        { text: "Info", link: "javascript:alert('System is operational')", icon: "info" }
    ],
};   

/*
    AsideMenu init
*/

const menu = new AsideMenu(menu_items, menu_config);
menu.init();        


// Feather icons
document.addEventListener('DOMContentLoaded', () => {            
    feather.replace();
});
```

The class is prepared to handle different user-role menus but it's discoraged to send other user-role menu-options different to the current for the logged user to avoid exposing possible not-fully protected urls.

```
const menu_config = {
    "starts_expanded": false,
    "options_starts_expanded": false,  /* it has only effect if starts_expanded is true */
    "role": "manager"
};

const menu_items = { 
    admin:  [
        { 
          text: "Exam list", 
          link: "/dashboard/exam-list", 
          icon: "heart"
        },
        { text: "Fast reporting", link: "/dashboard/fast-reporting", icon: "zap" },
        { text: "Settings",  
          childs: [ 
            { text: "Item 1", link: "/dashboard/settings/item1", icon: "sliders" }, 
            { text: "Item 2", link: "/dashboard/settings/item2", icon: "sliders" }, 
            { text: "Item 3", link: "/dashboard/settings/item3", icon: "sliders" }
          ],
          icon: "sliders"
        },
        { text: "Info", link: "javascript:alert('System is operational')", icon: "info" }
    ],

    // Other user-role's objects for rendering. E.g.
    manager: [
        { text: "Exam list", link: "/dashboard/exam-list", icon: "heart", /* "separator": true */ },
        { text: "Fast reporting", link: "/dashboard/fast-reporting", icon: "zap" },
        { text: "Info", link: "javascript:alert('System is operational')", icon: "info" }
    ]
};   
```

## Horizontal separator 

```
{ 
    text: "Exam list", 
    link: "/dashboard/exam-list", 
    icon: "heart", 
    "separator": true 
},
```

## Set HTML 

To set HTML in the place of the "angle" icon for instance to render another icon there is like this:

```
{ 
    text: "Exam list", 
    link: "/dashboard/exam-list", 
    icon: "heart", 
    html: "<i data-feather="circle"></i>"
},
```

## Set a counter

You can use method  .setCounter(), e.g.

```
menu.setCounter(5)
```

It solves problems like rounding to 99 when the number is bigger than that.