---
layout: default
---


{% for post in paginator.posts %}
  <h1><a href="{{ post.url }}">{{ post.title }}</a></h1>
  <p class="author">
    <span class="date">{{ post.date }}</span>
  </p>
  <div class="content">
    {{ post.content }}
  </div>
{% endfor %}

<h1>{{ paginator.total_pages }}</h1>

<div id="post-pagination" class="pagination">
  {% if paginator.previous_page %}
    <p class="previous">
      {% if paginator.previous_page == 1 %}
        <a href="/">Previous</a>
      {% else %}
        <a href="{{ paginator.previous_page_path }}">Previous</a>
      {% endif %}
    </p>
  {% else %}
    <p class="previous disabled">
      <span>Previous</span>
    </p>
  {% endif %}

  <ul class="pages">
    <li class="page">
      {% if paginator.page == 1 %}
        <span class="current-page">1</span>
      {% else %}
        <a href="/">1</a>
      {% endif %}
    </li>

    {% for count in (2..paginator.total_pages) %}
      <li class="page">
        {% if count == paginator.page %}
          <span class="current-page">{{ count }}</span>
        {% else %}
          <a href="/page{{ count }}">{{ count }}</a>
        {% endif %}
      </li>
    {% endfor %}
  </ul>

  {% if paginator.next_page %}
    <p class="next">
      <a href="{{ paginator.next_page_path }}">Next</a>
    </p>
  {% else %}
    <p class="next disabled">
      <span>Next</span>
    </p>
  {% endif %}

</div>



<div class="container">
    <div class="row">
        <div class="col-md-2 col-sm-0"></div>
            <div class="col-md-8 col-sm-12">
                <!-- 遍历所有文章 [start]-->
                <article>
                    <div class="posts">
                        {% for post in paginator.posts %}
                            <div class="perpost">
                                    <h1 class="posttitle"><a href="{{ post.url  }}" title="{{ post.title }}">{{ post.title }}</a></h1>
                                    <div class="perpostinfo">
                                        <span class="postdate"><span class="glyphicon glyphicon-calendar"></span>&nbsp;{{ post.date | date: "%Y-%m-%d" }}</span>&nbsp;&nbsp;
                                        <span class="postcategories"><span class="glyphicon glyphicon-folder-open"></span>&nbsp;&nbsp;<a href="{{ site.baseurl }}/category.html" title="Category">{{ post.categories }}</a></span>&nbsp;&nbsp;
                                        <span class="glyphicon glyphicon-tag"></span>
                                        <span class="posttags">
                                        {% for tag in post.tags %}
                                            <a href="{{ site.baseurl }}/tag.html" title="Tag">{{ tag }}</a> 
                                        {% endfor %}
                                        </span>
                                    </div>
                                <div class="summary">{{ post.summary }}</div>
                                <span class="readallpost"><a href="{{ post.url  }}" title="阅读全文">阅读全文</a></span>
                            </div>
                        {% endfor %}
                    </div>
                </article> <!-- 遍历所有文章 [end]-->

                <div class="postspage">
                        <div class="btn-group">
                        {% if paginator.previous_page %}
                            {% if paginator.previous_page == 1 %}
                                <a href="/">
                                    <button type="button" class="btn btn-default btn-sm">首页</button>
                                </a>
                            {% else %}
                                <a href="/page{{paginator.previous_page}}">
                                    <button type="button" class="btn btn-default btn-sm">前一页</button>   
                                </a>
                            {% endif %}
                        {% else %}
                            <span><button type="button" class="btn btn-default btn-sm active">首页</button></span>
                        {% endif %}
                        <span><button type="button" class="btn btn-default btn-sm active">{{ paginator.page }}</button> </span>
                        {% if paginator.next_page %}
                            {% if paginator.next_page == paginator.total_page %}
                                <a href="/page{{paginator.next_page}}">
                                    <button type="button" class="btn btn-default btn-sm">末页</button>
                                </a>
                            {% else %}
                                <a href="/page{{paginator.next_page}}">
                                    <button type="button" class="btn btn-default btn-sm">后一页</button>   
                                </a>
                            {% endif %}
                        {% else %}
                            <span>
                                <button type="button" class="btn btn-default btn-sm active">末页</button>
                            </span>
                        {% endif %}
                    </div>
                </div>
            </div>
        <div class="col-md-2 col-sm-0"></div>
    </div>
</div>
