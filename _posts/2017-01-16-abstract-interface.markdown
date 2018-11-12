---
layout: post
title:  "Abstract Class or Interface"
date:   2017-01-16 15:52:06 -0400
categories: uncategorized
---

<h3>Abstract classes</h3>

allow you to define both abstract and non abstract methods
cannot be instantiated on its own. must be subclassed
subclasses must implement all abstract methods
Use abstract classes if you need a superclass that defines some default behaviors (that most likely will not change), and leaves others for the subclasses to implement

<h3>Interfaces</h3>

Don't allow you to define any methods
cannot be instantiated on its own. other classes must implement the interface
ALL methods in an interface must be implemented by a class that implements it
Use interfaces when possibly other code is depending on, and expecting results from your code, and you want to assure them that the results will be met with an interface. Can be used when things are changing around a lot in the background.
