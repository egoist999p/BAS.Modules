## JSON Module Documentation

- JPath is the equivalent of XPath, which can be applied to data in JSON format. It works on the same principle, but not all of the XPath features are available in this case. The reason is that JSON is a more primitive data structure than Xml/
- For example, we cannot refer to the attributes of the elements, because in JSON they simply do not exist. But we can also search by conditions, use indexing and other features.
- The resulting variable can contain a simple value (**string**, **number**, **boolean**) or an array, which is a found element with all its fields.
- If the single query failed, the variable will contain **null** value.
- If the multiple query failed, the variables will contain **null** values.
- The **null** value can also be in an array in the case of a using action **Get Key** or **Get Keys**, if one of the sub-elements in turn represents the array itself.

## Helpful links

- [JPath Syntax and Examples](https://goessner.net/articles/JsonPath/)
- [JPath Online Constructor](http://jsonpathfinder.com/) 
- [JPath Online Evaluator](http://jsonpath.com/)
