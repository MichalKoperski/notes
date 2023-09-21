---
layout:
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: false
  outline:
    visible: false
  pagination:
    visible: false
---

# regex

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td><br><strong>Operators</strong></td><td><strong>Description</strong></td><td></td></tr><tr><td>1</td><td><code>(a)</code></td><td>The round brackets are used to group parts of a regex. Within the brackets, you can define further patterns which should be processed together.</td></tr><tr><td>2</td><td><code>[a-z]</code></td><td>The square brackets are used to define character classes. Inside the brackets, you can specify a list of characters to search for.</td></tr><tr><td>3</td><td><code>{1,10}</code></td><td>The curly brackets are used to define quantifiers. Inside the brackets, you can specify a number or a range that indicates how often a previous pattern should be repeated.</td></tr><tr><td>4</td><td><code>|</code></td><td>Also called the OR operator and shows results when one of the two expressions matches</td></tr><tr><td>5</td><td><code>.*</code></td><td>Also called the AND operator and displayed results only if both expressions match</td></tr></tbody></table>

**OR operator**

```
grep -E "(my|false)" /etc/passwd
```

**AND operator**

```
grep -E "(my.*false)" /etc/passwd

grep -E "my" /etc/passwd | grep -E "false"
```
