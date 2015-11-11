---
layout:     post
title:      "Title Case for French titles"
subtitle:   "Capital and lowercase letters in French titles"
date:       2015-11-10 22:48:55
author:     "Benoit VALLON"
header-img: "/img/2015-11-10-titlecase-for-french-titles/post-titlecase-for-french-titles.jpg"
comments:   true
categories: projects
tags:       [npm, library, tool, titlecase, french]
---

# What is Title Case?

Basically it is using "Capital and Lowercase Letters in Titles". This means only using capital letters for the principal words. Articles, conjunctions, and prepositions do not get capital letters unless they start the title. For example:

- The Last of the Mohicans

## In English

There are quite a few nice libraries to Title Case a text in English. This [implementation by John Resig](http://ejohn.org/blog/title-capitalization-in-javascript) is one of them and works well. In English, the first word in the title and all subsequent "important" words (everything except articles, conjunctions, and prepositions) are capitalized.

## In French

The capitalization of titles in French and English is quite a bit different. The rules are more complicated in French, so complicated, in fact, that even *Le Petit Robert* (the quintessential French dictionary) and *Le Bon Usage* (the French grammar bible) can't seem to agree on how to capitalize titles.

It is clear that either there is no standard system or that the standard is not well known.

# Why did I create the package?

As a consequence of what I previously wrote, I haven't found any existing package to Title Case french titles. So, I decided to write one for a friend's project and as a French person I tried to apply the rules that I have most commonly seen.

You can find the package here on [npm](https://www.npmjs.com/package/titlecase-french) and the code source here on [Github](https://github.com/benoitvallon/titlecase-french).


# The Title Case for French package

## Basic usage

You just need to require the package and call the `convert('mon texte de démonstration')` function.

```js
var titleCaseFrench = require('titlecase-french');

var myText = titleCaseFrench.convert('mon texte de démonstration');
console.log(myText); // => Mon Texte de Démonstration
```

## More complex examples

The package also provides APIs to add or remove lowercase words and even work on the special uppercase letters as "À,Ç". You can have a full description of what it does on [Github - TitleCase for French](https://github.com/benoitvallon/titlecase-french).

```js
var titleCaseFrench = require('titlecase-french');
titleCaseFrench.addLowerCaseWords('démonstration,texte');

var myText = titleCaseFrench.convert('mon texte de démonstration');
console.log(myText); // => Mon texte de démonstration

titleCaseFrench.removeLowerCaseWords('de,du,la,la');

var myText = titleCaseFrench.convert('mon texte de démonstration');
console.log(myText); // => Mon Texte De Démonstration

titleCaseFrench.keepCapitalizedSpecials('À,Ç,É');

var myText = titleCaseFrench.convert('ça va!');
console.log(myText); // => Ça Va!
```

## The rules

There are 5 main rules:

- A title always starts with a word in uppercase
- A specific list of words are in lowercase
- After a quote *'* words can be in lowercase or uppercase depending of the word before the quote
- Acronyms are in uppercase
- Special uppercase letters (with accent for example) are replaced with their simple version

### List of lowercase words

- Definite articles:
    - *le, la, les*

- Indefinite articles:
    - *un, une, des*

- Partitive articles:
    - *du, de, des*

- Contracted articles:
    - *au, aux, du, des*

- Demonstrative adjectives:
    - *ce, cet, cette, ces*

- Exclamative adjectives:
    - *quel, quels, quelle, quelles*

- Possessive adjectives:
    - *mon, ton, son, notre, votre, leur, ma, ta, sa, mes, tes, ses, nos, vos, leurs*

- Coordinating conjunctions:
    - *mais, ou, et, donc, or, ni, car, voire*

- Subordinating conjunctions:
    - *que, qu, quand, comme, si, lorsque, lorsqu, puisque, puisqu, quoique, quoiqu*

- Prepositions:
    - *à, chez, dans, entre, jusque, jusqu, hors, par, pour, sans, vers, sur, pas, parmi, avec, sous, en*

- Personal pronouns:
    - *je, tu, il, elle, on, nous, vous, ils, elles, me, te, se, y*

- Relative pronouns:
    - *qui, que, quoi, dont, où*

- Other words:
    - *ne*

### After a quote

- Words after a quote are in lowercase if the word before the quote is:
    - *c', j', m', n', s', t'*

- Words after a quote are in uppercase if the word before the quote is:
    - *d', l'*

### Special uppercase letters

- All the following special uppercase letters are replaced:
    - *À, Â, Ä, É, È, Ê, Ë, Ç, Î, Ï, Ô, Ö, Û, Ü, Ù*

Some examples.

```js
/*
Le Dernier des Mohicans
Du Vent dans les Branches
Junior l'Aventurier
Ca m'intéresse
Avec S.A.M.
Cet Eté à la Plage
*/
```

See here for more than 200 examples of converted French titles [Github - TitleCase for French](https://github.com/benoitvallon/titlecase-french#samples-of-converted-titles)
