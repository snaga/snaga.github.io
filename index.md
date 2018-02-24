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

      <div class="social_buttons">
        <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
        <a class="twitter-share-button" href="https://twitter.com/intent/tweet?text={{ post.title }} &mdash; {{ site.name }}&url={{ site.url }}{{ post.url }}">Tweet</a>

         <a href="http://b.hatena.ne.jp/entry/{{ site.url }}{{ post.url }}" class="hatena-bookmark-button" data-hatena-bookmark-layout="basic-label" data-hatena-bookmark-lang="ja" title="このエントリーをはてなブックマークに追加"><img src="https://b.st-hatena.com/images/entry-button/button-only@2x.png" alt="このエントリーをはてなブックマークに追加" width="20" height="20" style="border: none;" /></a><script type="text/javascript" src="https://b.st-hatena.com/js/bookmark_button.js" charset="utf-8" async="async"></script>
      </div> <!-- /social_buttons -->
    </div>
  </div>
  <div class="col-md-1"></div>
</div>
{% endfor %}
