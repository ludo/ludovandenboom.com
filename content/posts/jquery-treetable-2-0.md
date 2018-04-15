+++
title = "jQuery treeTable 2.0"
authors = ["ludo"]
description = ""
tags = []
date = "2008-11-12T10:00:00"
+++

Today I released [treeTable](http://plugins.jquery.com/project/treetable), a [jQuery](http://jquery.com) JavaScript plugin. This plugin is essentially the same as the [ActsAsTreeTable](/posts/28) plugin I released just one month ago.

## So, why the name change?

Well, I didn't like the ActsAsTreeTable name to begin with. Then why didn't I use treeTable to begin with? That's because there already exists a plugin that is named almost the same ([jQTreeTable](http://www.hanpau.com/jquery/unobtrusivetreetable.php)) and it does almost the same thing as my plugin. It works a bit differently, but it also displays a tree in a table. After a month of thinking I haven't come up with a better name and jQTreeTable doesn't look very much alive at this point, so I have decided that I will just use the name ‘treeTable’.

## What's new?

With ActsAsTreeTable being my first jQuery plugin ever, I wanted to do a bit of refactoring to let the plugin benefit from everything I've learned about jQuery during the last month. And I wanted to find out how hard it would be to implement drag & drop with [jQuery UI](http://ui.jquery.com "jQuery UI Website"). Other changes are some additional and renamed [configuration options](http://ludo.cubicphuse.nl/jquery-plugins/treeTable/doc/index.html#settings) and the addition of a minified version of the plugin (less than 4 KB!).

## Dragging and dropping

The most notable feature is the addition of the <tt>appendBranchTo</tt> function, which lets you move an entire branch in the tree by dragging and dropping. The documentation contains [an example](http://ludo.cubicphuse.nl/jquery-plugins/treeTable/doc/index.html#example-1) that shows how to use this method in combination with Draggables and Droppables.

![Dragging and dropping with jQuery treeTable](treetable-dnd.png)