---
layout: post
title:  "Jekyll Blog Pagination 分頁(換頁)"
date:   2017-04-22 07:00
icon: code
comments: true
---

### Jekyll有提供分頁功能(Pagination)，這個版型沒有預設這個功能，要自己新增

* Step 1: 安裝``jekyll-paginate``

{% highlight ruby %}

$ gem install jekyll-paginate

{% endhighlight %}

* Step 2: 修改``_config.yml``
{% highlight yml %}

gems: [jekyll-paginate]
paginate: 5
# Permalinks
permalink: pretty
url: https://noworneverev.github.io 
baseurl: 

{% endhighlight %}
上面的url記得改成自己的username

* Step 3: 修改``index.html``, 照搬[官網](https://jekyllrb.com/docs/pagination/){: target="_blank"}的文件：

{% highlight html %}
{% raw %}

<!-- This loops through the paginated posts -->
{% for post in paginator.posts %}
<div class="list">
<div class="post-index">
    <div class="post-image">
        <a href="{{post.url}}">
              <i class="fa fa-{{post.icon}} fa-fw"></i>
        </a>
    </div>
    <div class="post-content">
        <p class="post-index-title"><a href="{{site.baseurl}}{{post.url}}">{{post.title}}</a></p>
        <p>
             <span class="excerpt">{{ post.content | strip_html | strip_newlines | truncate: 90 }}</span>
        </p>
        <p class="post-detail">{{ post.date | date: '%B %d, %Y' }}
             <a href="{{site.baseurl}}{{post.url}}/index.html#disqus_thread" data-disqus-identifier="{{post.url}}"></a>
        </p>
    </div>
</div>
</div>
{% endfor %}

{% if paginator.total_pages > 1 %}
<div class="pagination" style="text-align: center;">
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">&laquo; Prev</a>
  {% else %}
    <span>&laquo; Prev</span>
  {% endif %}
  {% for page in (1..paginator.total_pages) %}
    {% if page == paginator.page %}
      <em>{{ page }}</em>
    {% elsif page == 1 %}
      <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">{{ page }}</a>
    {% else %}
      <a href="{{ site.paginate_path | prepend: site.baseurl | replace: '//', '/' | replace: ':num', page }}">{{ page }}</a>
    {% endif %}
  {% endfor %}
  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">Next &raquo;</a>
  {% else %}
    <span>Next &raquo;</span>
  {% endif %}
</div>
{% endif %}

{% endraw %}

{% endhighlight %}
Then, it's done.






