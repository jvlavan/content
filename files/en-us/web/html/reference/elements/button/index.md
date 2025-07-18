---
title: "<button>: The Button element"
slug: Web/HTML/Reference/Elements/button
page-type: html-element
browser-compat: html.elements.button
---

{{HTMLSidebar}}

The **`<button>`** [HTML](/en-US/docs/Web/HTML) element is an interactive element activated by a user with a mouse, keyboard, finger, voice command, or other assistive technology. Once activated, it then performs an action, such as submitting a [form](/en-US/docs/Learn_web_development/Extensions/Forms) or opening a dialog.

By default, HTML buttons are presented in a style resembling the platform the {{Glossary("user agent")}} runs on, but you can change buttons' appearance with [CSS](/en-US/docs/Web/CSS).

{{InteractiveExample("HTML Demo: &lt;button&gt;", "tabbed-shorter")}}

```html interactive-example
<button class="favorite styled" type="button">Add to favorites</button>
```

```css interactive-example
.styled {
  border: 0;
  line-height: 2.5;
  padding: 0 20px;
  font-size: 1rem;
  text-align: center;
  color: #fff;
  text-shadow: 1px 1px 1px #000;
  border-radius: 10px;
  background-color: rgb(220 0 0);
  background-image: linear-gradient(
    to top left,
    rgb(0 0 0 / 0.2),
    rgb(0 0 0 / 0.2) 30%,
    rgb(0 0 0 / 0)
  );
  box-shadow:
    inset 2px 2px 3px rgb(255 255 255 / 0.6),
    inset -2px -2px 3px rgb(0 0 0 / 0.6);
}

.styled:hover {
  background-color: red;
}

.styled:active {
  box-shadow:
    inset -2px -2px 3px rgb(255 255 255 / 0.6),
    inset 2px 2px 3px rgb(0 0 0 / 0.6);
}
```

## Attributes

This element's attributes include the [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).

- `autofocus`
  - : This Boolean attribute specifies that the button should have input [focus](/en-US/docs/Web/API/HTMLElement/focus) when the page loads. **Only one element in a document can have this attribute.**

- `command`
  - : Specifies the action to be performed on an element being controlled by a control `<button>`, specified via the `commandfor` attribute. The possible values are:
    - `"show-modal"`
      - : The button will show a {{htmlelement("dialog")}} as modal. If the dialog is already modal, no action will be taken. This is a declarative equivalent of calling the [`.showModal()`](/en-US/docs/Web/API/HTMLDialogElement/showModal) method on the dialog element.
    - `"close"`
      - : The button will close a {{htmlelement("dialog")}} element. If the dialog is already closed, no action will be taken. This is a declarative equivalent of calling the [`.close()`](/en-US/docs/Web/API/HTMLDialogElement/close) method on the dialog element.
    - `"request-close"`
      - : The button will request to close a {{htmlelement("dialog")}} element. If the dialog is already closed, no action will be taken. This is a declarative equivalent of calling the [`.requestClose()`](/en-US/docs/Web/API/HTMLDialogElement/requestClose) method on the dialog element.
    - `"show-popover"`
      - : The button will show a hidden popover. If you try to show an already showing popover, no action will be taken. See {{domxref("Popover API", "Popover API", "", "nocode")}} for more details. This is equivalent to [`popovertargetaction`](#popovertargetaction) with the value `"show"`. This is a declarative equivalent of calling the [`.showPopover()`](/en-US/docs/Web/API/HTMLElement/showPopover) method on the popover element.
    - `"hide-popover"`
      - : The button will hide a showing popover. If you try to hide an already hidden popover, no action will be taken. See {{domxref("Popover API", "Popover API", "", "nocode")}} for more details. This is equivalent to [`popovertargetaction`](#popovertargetaction) with the value `"hide"`. This is a declarative equivalent of calling the [`.hidePopover()`](/en-US/docs/Web/API/HTMLElement/hidePopover) method on the popover element.
    - `"toggle-popover"`
      - : The button will toggle a popover between showing and hidden. If the popover is hidden, it will be shown; if the popover is showing, it will be hidden. See {{domxref("Popover API", "Popover API", "", "nocode")}} for more details. This is equivalent to [`popovertargetaction`](#popovertargetaction) with the value `"toggle"`. This is a declarative equivalent of calling the [`.togglePopover()`](/en-US/docs/Web/API/HTMLElement/togglePopover) method on the popover element.
    - Custom values
      - : This attribute can represent custom values that are prefixed with a two hyphen characters (`--`). Buttons with a custom value will dispatch the {{domxref("CommandEvent")}} on the controlled element.

- `commandfor`
  - : Turns a `<button>` element into a command button, controlling the given interactive element; takes the ID of the element to control as its value. This is a more general version of [`popovertarget`](#popovertarget).
- [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled)
  - : This Boolean attribute prevents the user from interacting with the button: it cannot be pressed or focused.
- `form`
  - : The {{HTMLElement("form")}} element to associate the button with (its _form owner_). The value of this attribute must be the `id` of a `<form>` in the same document. (If this attribute is not set, the `<button>` is associated with its ancestor `<form>` element, if any.)

    This attribute lets you associate `<button>` elements to `<form>`s anywhere in the document, not just inside a `<form>`. It can also override an ancestor `<form>` element.

- `formaction`
  - : The URL that processes the information submitted by the button. Overrides the [`action`](/en-US/docs/Web/HTML/Reference/Elements/form#action) attribute of the button's form owner. Does nothing if there is no form owner.
- `formenctype`
  - : If the button is a submit button (it's inside/associated with a `<form>` and doesn't have `type="button"`), specifies how to encode the form data that is submitted. Possible values:
    - `application/x-www-form-urlencoded`: The default if the attribute is not used.
    - `multipart/form-data`: Used to submit {{HTMLElement("input")}} elements with their [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) attributes set to `file`.
    - `text/plain`: Specified as a debugging aid; shouldn't be used for real form submission.

    If this attribute is specified, it overrides the [`enctype`](/en-US/docs/Web/HTML/Reference/Elements/form#enctype) attribute of the button's form owner.

- `formmethod`
  - : If the button is a submit button (it's inside/associated with a `<form>` and doesn't have `type="button"`), this attribute specifies the [HTTP method](/en-US/docs/Web/HTTP/Reference/Methods) used to submit the form. Possible values:
    - `post`: The data from the form are included in the body of the HTTP request when sent to the server. Use when the form contains information that shouldn't be public, like login credentials.
    - `get`: The form data are appended to the form's `action` URL, with a `?` as a separator, and the resulting URL is sent to the server. Use this method when the form [has no side effects](/en-US/docs/Glossary/Idempotent), like search forms.
    - `dialog`: This method is used to indicate that the button closes the [dialog](/en-US/docs/Web/HTML/Reference/Elements/dialog) with which it is associated, and does not transmit the form data at all.

    If specified, this attribute overrides the [`method`](/en-US/docs/Web/HTML/Reference/Elements/form#method) attribute of the button's form owner.

- `formnovalidate`
  - : If the button is a submit button, this Boolean attribute specifies that the form is not to be [validated](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation) when it is submitted. If this attribute is specified, it overrides the [`novalidate`](/en-US/docs/Web/HTML/Reference/Elements/form#novalidate) attribute of the button's form owner.

    This attribute is also available on [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) and [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) elements.

- `formtarget`
  - : If the button is a submit button, this attribute is an author-defined name or standardized, underscore-prefixed keyword indicating where to display the response from submitting the form. This is the `name` of, or keyword for, a _browsing context_ (a tab, window, or {{HTMLElement("iframe")}}). If this attribute is specified, it overrides the [`target`](/en-US/docs/Web/HTML/Reference/Elements/form#target) attribute of the button's form owner. The following keywords have special meanings:
    - `_self`: Load the response into the same browsing context as the current one. This is the default if the attribute is not specified.
    - `_blank`: Load the response into a new unnamed browsing context — usually a new tab or window, depending on the user's browser settings.
    - `_parent`: Load the response into the parent browsing context of the current one. If there is no parent, this option behaves the same way as `_self`.
    - `_top`: Load the response into the top-level browsing context (that is, the browsing context that is an ancestor of the current one, and has no parent). If there is no parent, this option behaves the same way as `_self`.

- `name`
  - : The name of the button, submitted as a pair with the button's `value` as part of the form data, when that button is used to submit the form.

- `popovertarget`
  - : Turns a `<button>` element into a popover control button; takes the ID of the popover element to control as its value. Establishing a relationship between a popover and its invoker button using the `popovertarget` attribute has two additional useful effects:
    - The browser creates an implicit [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) and [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) relationship between popover and invoker, and places the popover in a logical position in the keyboard focus navigation order when shown. This makes the popover more accessible to keyboard and assistive technology (AT) users (see also [Popover accessibility features](/en-US/docs/Web/API/Popover_API/Using#popover_accessibility_features)).
    - The browser creates an implicit anchor reference between the two, making it very convenient to position popovers relative to their controls using [CSS anchor positioning](/en-US/docs/Web/CSS/CSS_anchor_positioning). See [Popover anchor positioning](/en-US/docs/Web/API/Popover_API/Using#popover_anchor_positioning) for more details.

- `popovertargetaction`
  - : Specifies the action to be performed on a popover element being controlled by a control `<button>`. Possible values are:
    - `"hide"`
      - : The button will hide a shown popover. If you try to hide an already hidden popover, no action will be taken.
    - `"show"`
      - : The button will show a hidden popover. If you try to show an already showing popover, no action will be taken.
    - `"toggle"`
      - : The button will toggle a popover between showing and hidden. If the popover is hidden, it will be shown; if the popover is showing, it will be hidden. If `popovertargetaction` is omitted, `"toggle"` is the default action that will be performed by the control button.

- `type`
  - : The default behavior of the button. Possible values are:
    - `submit`: The button submits the form data to the server. This is the default if the attribute is not specified for buttons associated with a `<form>`, or if the attribute is an empty or invalid value.
    - `reset`: The button resets all the controls to their initial values, like [\<input type="reset">](/en-US/docs/Web/HTML/Reference/Elements/input/reset). (This behavior tends to annoy users.)
    - `button`: The button has no default behavior, and does nothing when pressed by default. It can have client-side scripts listen to the element's events, which are triggered when the events occur.

- `value`
  - : Defines the value associated with the button's `name` when it's submitted with the form data. This value is passed to the server in params when the form is submitted using this button.

## Notes

A submit button with the attribute `formaction` set, but without an associated form does nothing. You have to set a form owner, either by wrapping it in a `<form>` or set the attribute `form` to the id of the form.

`<button>` elements are much easier to style than {{HTMLElement("input")}} elements. You can add inner HTML content (think `<i>`, `<br>`, or even `<img>`), and use {{Cssxref("::after")}} and {{Cssxref("::before")}} pseudo-elements for complex rendering.

If your buttons are not for submitting form data to a server, be sure to set their `type` attribute to `button`. Otherwise, they will try to submit form data and to load the (nonexistent) response, possibly destroying the current state of the document.

While `<button type="button">` has no default behavior, event handlers can be scripted to trigger behaviors. An activated button can perform programmable actions using [JavaScript](/en-US/docs/Learn_web_development/Core/Scripting), such as removing an item from a list.

By default, user agents style buttons as `display: flow-root`, which establishes a new [block formatting context](/en-US/docs/Web/CSS/CSS_display/Block_formatting_context) and centers the button's children both horizontally and vertically as long as they do not overflow. If the button is defined as a flex or grid container, the children will behave as flex or grid items. A button set to `display: inline` will be styled as if the value were set to `display: inline-block`.

## Accessibility

### Icon buttons

Buttons that only display an icon do not have an _{{glossary("accessible name")}}_. Accessible names provide information for assistive technology, such as screen readers, to access when they parse the document and generate [an accessibility tree](/en-US/docs/Learn_web_development/Core/Accessibility/What_is_accessibility#accessibility_apis). Assistive technology then uses the accessibility tree to navigate and manipulate page content.

To give an icon button an accessible name, put text in the `<button>` element that concisely describes the button's functionality.

#### Examples

```html
<button name="favorite">
  <svg fill="#000000" viewBox="0 0 42 42">
    <path
      d="M21,1c1.081,0,5.141,12.315,6.201,13.126s13.461,1.053,13.791,2.137 c0.34,1.087-9.561,8.938-9.961,10.252c-0.409,1.307,
      3.202,13.769,2.331,14.442c-0.879,0.673-11.05-6.79-12.361-6.79 c-1.311,0-11.481,7.463-12.36,6.79c-0.871-0.674,2.739-13.136,
      2.329-14.442c-0.399-1.313-10.3-9.165-9.96-10.252 c0.33-1.084,12.731-1.326,13.791-2.137S19.91,1,21,1z"></path>
  </svg>
  Add to favorites
</button>
```

##### Result

{{EmbedLiveSample('Icon buttons')}}

If you want to visually hide the button's text, an accessible way to do so is to use [a combination of CSS properties](https://www.a11yproject.com/posts/how-to-hide-content/) to remove it visually from the screen, but keep it parsable by assistive technology.

However, it is worth noting that leaving the button text visible can help people who may not be familiar with the icon's meaning or understand the button's purpose. This is especially important for people who are not technologically sophisticated or who may have different cultural interpretations of the icon the button uses.

- [What is an accessible name? | The Paciello Group](https://www.tpgi.com/what-is-an-accessible-name/)
- [MDN Understanding WCAG, Guideline 4.1 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Robust#guideline_4.1_—_compatible_maximize_compatibility_with_current_and_future_user_agents_including_assistive_technologies)
- [Understanding Success Criterion 4.1.2 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat-rsv.html)

### Size and Proximity

#### Size

Interactive elements such as buttons should have an area large enough to be easy to activate. This helps a variety of people, including people with motor control issues and people using non-precise forms of input such as a stylus or fingers. A minimum interactive size of 44×44 [CSS pixels](/en-US/docs/Glossary/CSS_pixel) is recommended.

- [Understanding Success Criterion 2.5.5: Target Size | W3C Understanding WCAG 2.1](https://www.w3.org/WAI/WCAG21/Understanding/target-size.html)
- [Target Size and 2.5.5 | Adrian Roselli](https://adrianroselli.com/2019/06/target-size-and-2-5-5.html)
- [Quick test: Large touch targets - The A11Y Project](https://www.a11yproject.com/posts/large-touch-targets/)

#### Proximity

Large amounts of interactive content — including buttons — placed in close visual proximity to each other should have space separating them. This spacing is beneficial for people who are experiencing motor control issues, who may accidentally activate the wrong interactive content.

Spacing may be created using CSS properties such as {{cssxref("margin")}}.

- [Hand tremors and the giant-button-problem - Axess Lab](https://axesslab.com/hand-tremors/)

### ARIA state information

To describe the state of a button the correct ARIA attribute to use is [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed) and not [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) or [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected). To find out more read the information about the [ARIA button role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role).

### Button styles

It is best not to override the default focus ring for elements that have focus. If the button styles are overridden, it is important to **ensure that the focus state has enough contrast** so that people experiencing low vision conditions can perceive it and people with cognitive differences will understand it.

The {{cssxref(":focus-visible")}} pseudo-class can be used to apply styles to an element that has {{cssxref(":focus")}} only when the user agent's heuristics determine that the focus should be highlighted, such as when a `<button>` receives keyboard focus. See [:focus vs :focus-visible](/en-US/docs/Web/CSS/:focus-visible#focus_vs_focus-visible) for more information.

Color contrast ratio is determined by comparing the luminosity of the button text and background color values to the background the button is placed on. To meet current [Web Content Accessibility Guidelines (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag/), a ratio of 4.5:1 is required for text content and 3:1 for large text. (Large text is defined as 18.66px and {{cssxref("font-weight", "bold")}} or larger, or 24px or larger.)

- [WebAIM: Color Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [MDN Understanding WCAG, Guideline 1.4 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [Understanding Success Criterion 1.4.3 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html)

### Clicking and focus

Whether clicking on a `<button>` or {{HTMLElement("input")}} button types causes it to (by default) become focused varies by browser and OS. Most browsers do give focus to a button being clicked, but [Safari does not, by design](https://webkit.org/b/22261#c68).

## Examples

```html
<button name="button">Press me</button>
```

{{ EmbedLiveSample('Example', 200, 64) }}

## Technical summary

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >Content categories</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >,
        <a
          href="/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content"
          >Interactive content</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#listed"
          >listed</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#labelable"
          >labelable</a
        >, and
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#submittable"
          >submittable</a
        >
        <a
          href="/en-US/docs/Web/HTML/Guides/Content_categories#form-associated_content"
          >form-associated</a
        >
        element, palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted content</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >Phrasing content</a
        >
        but there must be no
        <a
          href="/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content"
          >Interactive content</a
        >. If the <code>&lt;button&gt;</code> is the first child of a <a href="/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select">customizable select element</a>, then it may also
   contain zero or one {{htmlelement("selectedcontent")}} element.
      </td>
    </tr>
    <tr>
      <th scope="row">Tag omission</th>
      <td>None, both the starting and ending tag are mandatory.</td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>
        Any element that accepts
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td>
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role"
            >button</a
          ></code
        >
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role"><code>checkbox</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role"><code>combobox</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role"><code>link</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role"><code>menuitem</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role"><code>menuitemcheckbox</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role"><code>menuitemradio</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role"><code>option</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role"><code>radio</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role"><code>switch</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role"><code>tab</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>{{domxref("HTMLButtonElement")}}</td>
    </tr>
  </tbody>
</table>

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
