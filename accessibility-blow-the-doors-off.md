# You're only supposed to blow the bloody doors off! (accessibility)

_Léonie Watson ~ The Paciello Group (TPG)_ **@LGWatson**

## Keyboard intercept chain

**Windows** - Screen Reader -> Browser

- Shorter keyboard shortcuts capable (smart handling of form fields).

**MacOS** - Browser -> Screen Reader

## Virtual/browse mode

Windows screen readers create a virtual copy of the browser contents.

## Javascript keyboard shortcut

Can interfere with common screenreader shortcuts on windows.

### Solution

- Make JS shortcuts an enhancement (not a primary function).
- Make the primary function usable.

## Platform controls

All are fully accessible with roles, attributes, state passed automatically to OS APIs.

Before OS Accessibility API's screenreaders attempted to parse visual output to determine accessibility information.

## HTML mapping support

Browser may support an element, but not accessibility support for it.

A browser amy support an element but not for screenreaders

http://www.html5accessibility.com/

It's possible to "polyfill" accessibility with ARIA

## ARIA: don't use it

Use native HTML wherever possible.

- Keyboard interaction.
- Focus management.
- Role, state, a property information.

## ARIA: don't break native semantics

```html
<button role="heading" aria-level="1">
    Contents
</button>
```

^^ Confused screen reader users.

## ARIA: make it work with the keyboard

When you create custom components it's your responsibility to make it work with the keyboard. Buttons should be focusable and work with the space and enter keys.

## Using the application role

```html
<body role="application">...</body>
```

Removes the screen reader from the keyboard intercept chain. Breaks all shortcuts. Only allows the tab key to work. Non-focusable content is no longer identifiable to a SR-user.

If using the application role you must provide all keyboard interaction yourself.

Many other roles trigger this mode automatically including:

- tablist
- grid
- menu and menubar
- toolbar

^^^ Guidence is providable for this type of thing. Use the ARIA authoring guide. Also Inclusive Design Pattern (book).

## Tabs

Should use roving tabindex, and listen for arrow key codes for navigating the tabs. Use aria-controls key (JAWS only).

## Accessibility Object Model (AOM)

JavaScript accessibility API in development for Chrome, Firefox, Safari.

### Phases

1. Modify accessibility node semantics.
2. Respond to events from screen readers.
3. Create virtual accessibility nodes.
4. Query the accessibility tree.

Would allow setting things in the accessibility tree without needing aria attributes in the HTML.