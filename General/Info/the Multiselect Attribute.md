---
title: the Multiselect Attribute
parent: Info
nav_order: "3"
tags:
  - multiselect
  - faq
  - contribute
---

The Multiselelect attribute is a feature that comes alongside Ryle Radio. It allows a multiselect dropdown to be displayed in the inspector, much like a LayerMask, and a way to convert the int from that dropdown into a collection subset. 
Basically, it lets you select multiple things from a list in the inspector rather than just one :)

---
## What does it do?
The Multiselect attribute is a variable attribute introduced in Ryle Radio that acts as an extension to NaughtyAttributes, providing a LayerMask-style multi-select dropdown in the inspector. The options you choose on the dropdown are saved as a flag int, and can be converted at runtime to a subset of a collection you provide. 
In short- you can choose a number of options from a list (or array), then convert that number to a subset of the list.

## When should I use it?
Usually you only need the `NaughtyAttributes.Dropdown` attribute so that you can select an option from a list. If you need to select multiple options in the same place, though, you can use the Multiselect attribute. It effectively allows you to convert a dropdown like this:
To a dropdown like this:
It gets a fair bit of usage in Ryle Radio for components like Broadcasters, which can broadcast multiple tracks at once.

## How do I use it?
1. Create an int variable in your code.
2. Add `[Multiselect("_")]` to the line above this int variable, and replace the _ with the name of the list you want the dropdown to show.
3. When you need to access the options chosen in the dropdown, run `MultiselectAttribute.To<_>(name_of_int_variable, name_of_list_used_by_dropdown)`- the output of this method is your subset list.


```cs
string[] options = new string[4] { "awesome", "attribute", "thanks", "ryle-e" };

[Multiselect("options")]
private int flags1; // in the inspector, we set it to ["awesome", "thanks"]- the first and third options in the inspector. this int then becomes 0x0101

public void Convert()
{
	int flags2 = 0x1010; // equivalent to selecting the second and fourth options in the inspector

	List<string> converted1 = Multiselect.To<string>(flags1, options); // sets to ["awesome", "thanks"]

	List<string> converted2 = Multiselect.To<string>(flags2, options); // sets to ["attribute", "ryle-e"]
}
```