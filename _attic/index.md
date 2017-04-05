---
layout: default
title: Create Your Own Templates - Template Reference
---

# {{ page.title }}

<div class="toc" markdown="1">
Contents:

* [Site](#site)
* [Feed](#feed)
* [Item](#item)
* [Questions? Comments?](#questions)
</div>


Create your own templates (use `site`, `feed`, `item`, etc.)


## Site  {#site}

Example: Planet Title

~~~
<%= site.title %>
~~~


Example: List all subscriptions

~~~
<% site.feeds.each do |feed| %>
  <%= feed.url %>  or  <%= feed.link %>
  <%= feed.title %>  or  <%= feed.name %>
  <%= feed.title2 %>
  <%= feed.feed_url %>  or  <%= feed.feed %>
<% end %>
~~~


## Feed {#feed}

Example: Lastest feed items

~~~
<% items = site.items.latest.limit(24)
     ItemCursor.new( items ).each do |item,new_date,new_feed| %>

  <% if new_date %>
    <%= item.published %>
  <% end %>

  <% if new_feed %>
    <%= item.feed.url %>  or  <%= item.feed.link %>
    <%= item.feed.title %>  or  <%= item.feed.name %>
    <%= item.feed.title2 %>
  <% end %>

  <% if item.title %>
    <%= item.title %>
  <% end %>

  <% item.content %>
  <% item.url %>  or  <% item.link %>
  <% item.published %>

<% end %>
~~~


{% include questions.md %}

