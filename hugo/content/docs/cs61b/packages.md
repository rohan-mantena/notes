---
title: "Packages and Access"
weight: 3    
---

- Non netsted classes or interfacnes may be public or package private 
- Classes without a modifier are package private (only accesible within the same package)
- Members of a class (attriubes/fields/instance variables, methods, constructors, nested types) can be any of the four access levels 
- Access is based on static not dynamic types -> class not object 
- Only override a method with one that is at least as permissive 
- protected {...}

- public declarations are for ['clients'](),
- package private is for use in implementation in a class that must be known to other classes that assist in the implemetation (use it but don't reveal it)
- protected declarations are part of implementation that subtypes may need but clients don't generally use -> can use constructor in a subtype but cannot invoke constuctor outside 
- private (need to know basis), only that class needs