Testing can only capture some errors, but never all of them. Nonetheless, we still use it since it captures more bugs than otherwise.

Purposes:
- Find bugs
- Prevent bugs from sneaking in during development (new ones)
- give high confidence in the integrity of product
- explore class method design
- specification of expected behavior

Unit Testing - isolated a bit of source code to validate expected behavior

Integration Testing - larger software components, make sure separate features work together


Three Big Ideas:
- Coverage: seek to execute all possibilities
- Test Equivalent Classes: tests should cover different thing, no unnecessary tests
- Bottom Up Testing: Still too many tests, so we just test each component, and more for each merging of bottom to up.

![[Pasted image 20261012035917.png]]


Black Box Testing - don't look inside the component being tested
Pro: not biased by implementation details
Con: Can't leverage opportunities

White Box Testing - look in the component being tested
Pro: exploit possible weaknesses
Con: May miss impossible bugs

Grey Box: Somewhere in the middle


What happens when A depends on B? 
We use mockings, to fake that A is done, so we can do B.

