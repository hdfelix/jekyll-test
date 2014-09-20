jQuery selectors          purpose
selector, selector, ...   Finds all of the specified selectors
.class1.class2            Finds all elements with both .class1 and .class2 applied
parent > child            Finds all child elements that are direct children of elements
                          of type parent.
ancestor descendant       Finds all descendant elements that are contained within elements of type ancestor
prev + next               Finds all next elements that are next to a prev element
prev ~ siblings           Finds all sibling elements that come after preve and match
                          the siblings selector


$("document").ready(functions() {   // do the following once the page finishes rendering
  $("p").css("border", "1px sold red");
}


JQuery filters

