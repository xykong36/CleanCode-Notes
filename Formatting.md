* The Purpose of Formatting
* Vertical Formatting
  * Vertical Openness Between Concepts
  
  Listing 5-2 BoldWidget.java 演示空格对于不同概念的切割有助于提高可读性
  ```java
  package fitnesse.wikitext.widgets;

  import java.util.regex.*;

  public class BoldWidget extends ParentWidget {
      public static final String REGEXP = "’’’.+?’’’";
      private static final Pattern pattern = Pattern.compile("’’’(.+?)’’’",
              Pattern.MULTILINE + Pattern.DOTALL
      );

      public BoldWidget(ParentWidget parent, String text) throws Exception {
          super(parent);
          Matcher match = pattern.matcher(text);
          match.find();
          addChildWidgets(match.group(1));
      }

      public String render() throws Exception {
          StringBuffer html = new StringBuffer("<b>");
          html.append(childHtml()).append("</b>");
          return html.toString();
      }
  }
  ```
  
  ```java
  // 同样的代码在 去掉空格之后可读性变差
  package fitnesse.wikitext.widgets;
  import java.util.regex.*;
  public class BoldWidget extends ParentWidget {
      public static final String REGEXP = "’’’.+?’’’";
      private static final Pattern pattern = Pattern.compile("’’’(.+?)’’’",
              Pattern.MULTILINE + Pattern.DOTALL
      );
      public BoldWidget(ParentWidget parent, String text) throws Exception {
          super(parent);
          Matcher match = pattern.matcher(text);
          match.find();
          addChildWidgets(match.group(1));
      }
      public String render() throws Exception {
          StringBuffer html = new StringBuffer("<b>");
          html.append(childHtml()).append("</b>");
          return html.toString();
      }
  }
  ```
  
    * Vertical Density
    * Vertical Distance
  
* Horizontal Formatting
* Team Rules
