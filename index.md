{% for post in site.posts %}
<div class="row">
  <div class="col-md-1"></div>
  <div class="col-md-10">
    <div class="panel panel-default post">
      <h2><a href="{{ post.url }}" class="nodeco">{{ post.title }}</a></h2>
      <div class="date">
        {{ post.date | date_to_string }}
      </div> <!-- /date -->
      <div class="post_body">
        {{ content }}
      </div> <!-- /post -->
    </div>
  </div>
  <div class="col-md-1"></div>
</div>
{% endfor %}
