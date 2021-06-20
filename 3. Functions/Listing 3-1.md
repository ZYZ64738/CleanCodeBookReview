# Listing 3-1
`HtmlUtil.java (FitNesse 20070619)`

```java
public static String testableHtml(
PageData pageData, boolean includeSuiteSetup) throws Exception {
  WikiPage wikiPage = pageData.getWikiPage();
  StringBuffer buffer = new StringBuffer();
  if (pageData.hasAttribute("Test")) {
    if (includeSuiteSetup) {
      WikiPage suiteSetup = PageCrawlerImpl.getInheritedPage(
      SuiteResponder.SUITE_SETUP_NAME, wikiPage);
      if (suiteSetup != null) {
        WikiPagePath pagePath = suiteSetup.getPageCrawler().getFullPath(suiteSetup);
        String pagePathName = PathParser.render(pagePath);
        buffer.append("!include -setup .").append(pagePathName).append("\n");
      }
    }
    WikiPage setup = PageCrawlerImpl.getInheritedPage("SetUp", wikiPage);
    if (setup != null) {
      WikiPagePath setupPath = wikiPage.getPageCrawler().getFullPath(setup);
      String setupPathName = PathParser.render(setupPath);
      buffer.append("!include -setup .").append(setupPathName).append("\n");
    }
  }
  buffer.append(pageData.getContent());
  if (pageData.hasAttribute("Test")) {
    WikiPage teardown = PageCrawlerImpl.getInheritedPage("TearDown", wikiPage);
    if (teardown != null) {
      WikiPagePath tearDownPath = wikiPage.getPageCrawler().getFullPath(teardown);
      String tearDownPathName = PathParser.render(tearDownPath);
      buffer.append("\n").append("!include -teardown .").append(tearDownPathName).append("\n");
    }

    if (includeSuiteSetup) {
      WikiPage suiteTeardown = PageCrawlerImpl.getInheritedPage(
      SuiteResponder.SUITE_TEARDOWN_NAME, wikiPage);
      if (suiteTeardown != null) {
        WikiPagePath pagePath = suiteTeardown.getPageCrawler().getFullPath(suiteTeardown);
        String pagePathName = PathParser.render(pagePath);
        buffer.append("!include -teardown .").append(pagePathName).append("\n");
      }
    }
  }
  pageData.setContent(buffer.toString());
  return pageData.getHtml();
}

```


### Do One Thing

Es sollte klar sein, dass Listing 3-1 viel mehr als nur eine Sache tut. Es erstellt Puffer, holt Seiten, sucht nach vererbten Seiten, rendert Pfade, hängt obskure Strings an und generiert HTML, neben anderen Dingen. Listing 3-1 ist sehr damit beschäftigt, viele verschiedene Dinge zu tun.