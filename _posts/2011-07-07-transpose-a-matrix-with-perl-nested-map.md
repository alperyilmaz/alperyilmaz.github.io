---
id: 120
title: transpose a matrix with perl nested map
date: 2011-07-07T09:33:37+00:00
author: admin
layout: post
guid: http://alperyilmaz.org/blog/?p=120
permalink: /2011/07/07/transpose-a-matrix-with-perl-nested-map/
categories:
  - command-line
  - one-liner
  - perl
---
Here's the matrix that we'll be using:

{% terminal %}
$ paste <(seq 1 5) <(seq 12 16) 
1	12
2	13
3	14
4	15
5	16
{% endterminal %}

Now, let's use a perl one-liner with nested maps to transpose the matrix:

{% terminal %} 
$ paste <(seq 1 5) <(seq 12 16) | perl -ane 'push @matrix,[@F]; END { print join "\n",map {$row=$_; join"\t",map { $matrix[$_][$row]} 0 .. $#matrix } 0 .. $#{$matrix[0]}; print "\n" }'
1	2	3	4	5
12	13	14	15	16
{% endterminal %}

I got the idea from this [blog post](http://www.hidemail.de/blog/perl_tutor.shtml#map_transpose_matrix), but I slightly modified it so that you don't need to make a copy of the transposed array (to save memory)
