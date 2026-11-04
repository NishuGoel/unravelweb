---
title: "Failed to execute ‘removeChild’ on ‘Node’."
permalink: "/2022/10/22/failed-to-execute-removechild-on-node/"
tags: ["Javascript", "javascript", "react"]
layout: "post"
date: "2022-10-22"
---

{% raw %}
This error is frequently noticed on some projects. Though it seems to be something to do with DOM modification, there seems to be nothing obvious from code where this could be caused.

So, turns out there can be multiple reasons for this to occur:

1. Applying browser translation on non-wrapped elements.  
2. Conditionally rendering elements inside React Fragments.

### Applying browser translation on non-wrapped elements

Example: Listing labels *(string | JSX.element)* inside a third-party component.

```
<DropDownMenu
  id="create-menu"
  menuItems={items.map(item => ({
    name: item.key,
    label: i18n.t(item.slug), // This is where a non-wrapped element is getting translated causing the error
  })}
>

{...}

</DropDownMenu>
```

**Solution:**  
Passing label as a JSX element instead of a string.

```
<DropDownMenu
  id="create-menu"
  menuItems={items.map(item => ({
    name: item.key,
    label: <span>{i18n.t(item.slug)}</span>, // This is where a non-wrapped element is getting translated causing the error
  })}
>

{...}

</DropDownMenu>
```

### **Conditionally rendering elements inside React Fragments**

We use fragments in React to avoid adding extra nodes. These fragments when used conditionally, for example for a use case like:

```
<Fragment>
   {!isThisSituation ?  
        <span>Display this</span>
          :    
        <Icon
            color="secondary"
            fontSize={12}
            name="this-icon"
        />
    }
</Fragment>
```

result in React trying to remove the conditionally rendered node from the parent that is a `fragment`. However, we know Fragment doesn’t really act as an extra node.

**Solution**:

When conditionally rendering nodes, wrap the children inside a legit node.

```
<div>
   {!isThisSituation ?  
        <span>Display this</span>
          :    
        <Icon
            color="secondary"
            fontSize={12}
            name="this-icon"
        />
    }
</div>
```

Also throws the error for a scenario like this:

```
// throws the error if:

<div>
  {condition && 'text'} // solution: needs to be wrapped in an element
  <span>Some other text</span>
</div>

OR

<div>
  {condition && <span>Text</span>}
  Welcome // solution: needs to be wrapped in an element
</div>
```
{% endraw %}
