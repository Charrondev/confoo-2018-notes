# How I learned to stop worrying and love Regular Expressions

_Jordi Boggiano_ - __@seldaek__

## History

1956 - Regular languages and Regular Sets.

1968 - QED uses it to match patterns in text file.

1971 - Unix an ed.

1974 - g/re/p ed is Global search for regular expressions.

1986 - Perl gets regular expressions. Lots of new regex features.

1997 - PCRE (Perl Compatible Regular expressions), C lib, used by PHP.

2003 - Oxford English Dictionary accepts "grep" as a verb.

_At some point along the way the expressions are no longer regular (different from the mathematical proof)_

## Regex Components

- Pattern
  - Characters `You`
  - Meta-characters  `.*[]` etc. These characters can be escaped with a backslash.
  - Character Class `[abcd]` or `[a-z]`
    - ^ to negate.
    - Escaping not required.
  - Match ASCII code point `\x00` or use the actual character.
  - Match unicode code points `\x(25E6)` or use the actual character.
  - Subpattern/Capture Group `(ab)`
    - Named capture groups `(?P<YOUR_NAME>patt|ern)`.
  - Alteration `(ab|cd)`
    - Should start with most specific to least specific `(bobby|bob)` instead of `(bob|bobby)`
- Subject String
- Matches



## Quantifiers

- `?` 0 or 1
- `*` 0 -> infinity
- `+` 1 -> infinity
- `{3,7}` Arbitrary

### Eager Quantifier

` (aa)(1,2)`

`<em>.+</em>`

### Lazy Quantifier

`(aa)(1,2)?`

`<em>.+?</em>`

### Non-Possesive Quantifier

Match and do not give up matches

`trig+ger` -> `trigger` + `triggger`



### Possesive Quantifier

`trig++ger` -> Neither of the previos matches.



## Anchors

`^` Start of text (or start of line with `\m`)

`$` End of text or end of string with an extra newline at the end (or end of line with `\m`)

## Backreference to a subbpatterns

## Lookahead and Lookbehind

Let's match words surrounded by *

Naive approach `\*\w+\*`

If lost you can _\*keep\*_ a _\*secret\*_

With lookbehinds `(?<=\*)\w(?=\*)`

If lost you can \*_keep_\* a \*_secret_\*

## Conditionals

Just don't do it. Better to use the languages built in control statements.

## Add comment in a pattern

Use the \x modifier at the end

```js
/
[patt|ern] # This is a really complicated pattern
/x
```

## Missing in javascript

- Lookaheads/lookbehinds
- \m modifier

## Limitations

- Use regexes until you can't.
- Know you're domain variance and restrictions.

##Resources

regular-expressions.info

regex101.com