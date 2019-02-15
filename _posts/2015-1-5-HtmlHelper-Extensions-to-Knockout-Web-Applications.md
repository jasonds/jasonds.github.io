---
layout: post
title: HtmlHelper Extensions to Knockout Web Applications
categories: ASP.NET MVC
tags:
  - MVC
  - JavaScript
  - Knockout
---

If you have tried to couple Knockout with jQuery unobtrusive validation in an MVC Web Application before, you might have come across this familiar scenario: what is the best way to incorporate Knockout bindings while preserving the benefits of using HtmlHelper extension methods (e.g. getting unobtrusive validation attributes from data annotations, among others)?

One solution has proven useful - HtmlHelper extension methods for Knockout. Below, I first mention the benefits of this approach and then show examples of use:

## Benefits
1. Preserves the advantages of using HtmlHelper extension methods (the Knockout HtmlHelper extension methods each wrap their respective underlying HtmlHelper extension method).
2. Eliminates the need for manually including the "value" or "checked" binding in your markup.
3. Knockout code reusability and readability.

## Examples
Below are examples showing these benefits. I've created a test model Person which includes the required data annotation on a string property LastName.

1. If you want to include the Knockout value binding for LastName while preserving unobtrusive validation, you could make use of the optional htmlAttributes as shown in example 1.1. Note how Knockout is integrated by hand, where 'data_bind' is eventually replaced with 'data-bind':

2. HtmlHelper TextBoxFor with Knockout bindings added through optional HTML attributes:
```
@Html.TextBoxFor(x => x.LastName, new { data_bind = "value: LastName" })
```

_Rendered Markup_
```
<input data-bind="value: LastName" data-val="true" data-val-required="The LastName field is required." id="LastName" name="LastName" type="text" value="">
```

3. The prolific use of the value/checked binding was the inspiration for the Knockout HtmlHelper extensions. Below is an example of how the Knockout HtmlHelper extension for TextBoxFor simplifies this:
```
@Html.KoTextBoxFor(x => x.LastName)
```

_Rendered Markup_
```
<input data-bind="value: LastName" data-val="true" data-val-required="The LastName field is required." id="LastName" name="LastName" type="text" value="">
```

4. If you want to include additional bindings, you can do so with the optional "dataBindAttributes" parameter. Here is an example of the Knockout HtmlHelper extension for CheckBoxFor with an additional binding:
```
@Html.KoCheckBoxFor(x => x.HasPets, dataBindAttributes: new { enable = "HasPetsEnabled" })
```

_Rendered Markup_
```
<input data-bind="checked: HasPets, enable: HasPetsEnabled" data-val="true" data-val-required="The HasPets field is required." id="HasPets" name="HasPets" type="checkbox" value="true"> <input name="HasPets" type="hidden" value="false">
```

## Notes
1. These extension methods work under the assumption that your observables in your Knockout view model are named the same as your model's property (e.g. "LastName"). The extensions can be altered to support CamelCase Knockout bindings as well.
2. The HtmlFieldPrefix is removed when adding in the value/checked Knockout binding. Had we not done this and assuming we had the HtmlFieldPrefix set to "Person", example 1.2 above would have resulted as follows:
```
<input data-bind="value: Person.LastName" data-val="true" data-val-required="The LastName field is required." id="Person_LastName" name="Person.LastName" type="text" value="">
```
3. The furthest descended property from the supplied expression is chosen for the value/checked Knockout binding (e.g. x => x.Address.City would return just "City"). Had we not done this, the result would have been:
```
<input data-bind="value: Address.City" id="Address_City" name="Address.City" type="text" value="">
```
4. An optional "dataBindAttributes" parameter can be used for Knockout custom binding handlers and/or additional bindings as shown in example two. The value/checked binding is added by default for the respective input type.
5. There is an optional "addDefaultBinding" parameter which is set to true. This results in the value/checked binding being included. In the case of using Knockout custom binding handlers, this can be set to false, and the "dataBindAttributes" parameter can be used.
6. DropDownListFor was purposefully left off due to the variety of implementations that can be provided. I've been known to use select2 from time to time when it is appropriate and have a Knockout DropDownListFor extension that wires this up to a Knockout custom binding handler.

<a href = "https://sears.blob.core.windows.net/blog/2015/1/5/KoExtensions.cs">View extension method source</a>

Happy New Year,

Jason Sears