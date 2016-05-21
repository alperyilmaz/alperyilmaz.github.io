---
id: 36
title: wppost markup test
date: 2010-01-13T03:14:33+00:00
author: admin
layout: post
guid: http://alperyilmaz.org/blog/?p=36
permalink: /2010/01/13/wppost-markup-test-5/
categories:
  - blogging
  - linux
  - perl
---
It's great that wppost supports html markup in blog posting. For example I can type in **bold** or I can generate URL links like [link](http://alperyilmaz.org).
  
Plus I can do syntax highlighting via [WP-Codebox](http://www.ericbess.com/ericblog/2008/03/03/wp-codebox/)

## Usage examples:

**How to use wp-codebox**
  
Example 1: PHP, no line numbers
(Edit: I used code fence to highlight code)

```php
<?php
      function foo() {
        echo "Hello World!\\n";
      }
      for (\$i = 0; \$i < 10 $i++) {
        foo();
      }
    ?>
```
Example 2: Java, with line numbers, collapse codebox
(Edit: I used Jekyll Liquid extension for highlight, in this case there's no collapse)

{% highlight java linenos=table %}
public class Hello {
      public static void main(String[] args) {
        System.out.println("Hello World!");
      }
    }
{% endhighlight %}

Example 3: Ruby, with line numbers starting at 18, code downloading(ruby.txt)
(Edit: I used Jekyll Liquid extension for highlight, in this case there's no starting line number trick)

{% highlight ruby linenos=table %}
class Example
      def example(arg1)
        return "Hello: " + arg1.to_s
      end
    end
{% endhighlight %}

Note:(if colla="+" not used, default is collapsed, if line="1" not used default is no line numbers)

**How to post with wppost:**

```bash
wppost -t 'wppost markup test' -i ./content.txt -T image.png -c category1,category2
```

> Edit: Since I moved to Jekyll from Wordpress, syntax highlighting in this post has been done via Markdown, not Wordpress plugin. Thus, line numbering has been achieved by Jekyll highlight. (2016/5/7)