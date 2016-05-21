---
id: 39
title: Retrieve WP categories from commandline
date: 2010-01-13T19:08:15+00:00
author: admin
layout: post
guid: http://alperyilmaz.org/blog/?p=39
permalink: /2010/01/13/retrieve-wp-categories-from-commandline/
categories:
  - blogging
  - command-line
  - perl
---
Posting to WP from commandline is great. Before I post it, I need to lookup available categories so that I can categorize the new post correctly. To prevent a visit to WP admin GUI, I used the same Perl module for posting to retrieve available categories. Below is the code. I hope it helps you too..

```perl
use WordPress::XMLRPC;
my $o = WordPress::XMLRPC->new({
   username => 'username',
   password => 'password',
   proxy => 'http://yourblog-address/xmlrpc.php',
 });

my $categories= $o->getCategories();
foreach (0..scalar(@$categories)) {
	print ${$categories}[$_]->{'categoryId'},"\t",${$categories}[$_]->{'categoryName'};
	if (${$categories}[$_]->{'parentId'} != 0){
		print "\tParentId=",${$categories}[$_]->{'parentId'},"\n";
		}
	else {print "\n"}
}
```