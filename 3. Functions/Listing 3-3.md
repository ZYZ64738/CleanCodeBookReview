# Listing 3-3
`HtmlUtil.java (re-refactored)`

```java
public static String renderPageWithSetupsAndTeardowns(
PageData pageData, boolean isSuite) throws Exception {
  if (isTestPage(pageData)) includeSetupAndTeardownPages(pageData, isSuite);
  return pageData.getHtml();
}
```