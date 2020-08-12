# Java Doc

{@link}

{@link package.class#member label }
Inserts an inline link with a visible text label that points to the documentation for the specified package, class, or member name of a referenced class. This tag is valid in all documentation comments: overview, module, package, class, interface, constructor, method and field, including the text portion of any tag, such as the @return, @param and @deprecated tags.

This tag is similar to the @see tag. Both tags require the same references and accept the same syntax for package.class#member and label. The main difference is that the {@link} tag generates an inline link rather than placing the link in the "See Also" section. The {@link} tag begins and ends with braces to separate it from the rest of the inline text. If you need to use the right brace (}) inside the label, then use the HTML entity notation &#125;.

There is no limit to the number of {@link} tags allowed in a sentence.





## Resources

* [How to Write Doc Comments for the Javadoc Tool](https://www.oracle.com/technical-resources/articles/java/javadoc-tool.html)
* [Javadoc Guide](https://docs.oracle.com/en/java/javase/11/javadoc/javadoc.html#GUID-7A344353-3BBF-45C4-8B28-15025DDCC643)
* [javadoc command](https://docs.oracle.com/en/java/javase/11/tools/javadoc.html)