---
layout: default
description: "残業は、AIがする。AI残業部は、Claude Codeで業務を自動化する手順と、安全に任せるためのルールを発信するメディアです。"
---

<section class="intro">
  <h1>AI残業部</h1>
  <p class="intro-slogan">残業は、AIがする。</p>
  <figure class="hero-photo">
    <img src="{{ '/assets/images/hero-night-laptop.jpg' | relative_url }}" alt="夜の部屋で光るノートPCとマグカップ。窓の外には街の明かり" width="1600" height="1067">
  </figure>
  <p>AI残業部は、会社で仕事を任されすぎた平凡なおじさんが、自分の仕事をAIに押しつけるためだけに全時間を使っているメディアです。Claude Codeで業務を自動化する手順と、AIに安全に任せるためのルール（速くする仕組みと、安全に止める仕組み）をセットで発信します。</p>
  <p>ここは、その記事の正本を置く場所です。機能の紹介だけで終わらせず、振られた仕事に対して実際に作った「仕組み」と、その作り方・効き目を書きます。出典は公式ドキュメント等の一次情報を確認し、記事の末尾にはよくある質問をまとめます。</p>
</section>

<section class="series">
  <h2>連載（シリーズ）</h2>
  <div class="series-block">
    <h3><a href="{{ '/series/konya-daiko/' | relative_url }}">今夜の残業代行</a></h3>
    <p>Claude Codeの活用レシピの連載です。身近な仕事を題材に、実際に作った仕組みと手順を「第◯夜」の形で紹介します。</p>
  </div>
  <div class="series-block">
    <h3><a href="{{ '/series/anzen-kakunin/' | relative_url }}">代行前の安全確認</a></h3>
    <p>AIに任せる前に確認する、セキュリティの連載です。権限、秘密情報の扱い、プロンプトインジェクション対策、MCPの選定などを扱います。</p>
  </div>
  <div class="series-block">
    <h3><a href="{{ '/series/asa-owatta/' | relative_url }}">朝には終わってた</a></h3>
    <p>定期実行・自動化の事例の連載です。夜の間に終わらせておく仕組みと、その作り方を紹介します。</p>
  </div>
  <div class="series-block">
    <h3><a href="{{ '/series/dogubako/' | relative_url }}">部室の道具箱</a></h3>
    <p>そのまま使えるテンプレートとチェックリストの置き場です。記事で作った仕組みを、道具としてまとめ直します。</p>
  </div>
</section>

<section class="channels">
  <h2>ほかの場所でも書いています</h2>
  <ul class="channel-list">
    <li><a href="{{ site.channels.note }}">note（AI残業部）</a><span class="channel-desc">記事の連載と、部員のみなさんとのやり取りの場です。</span></li>
    <li><a href="{{ site.channels.zenn_book }}">Zenn本『残業は、AIがする。 — Claude Code実践入門』</a><span class="channel-desc">Claude Codeの実践を一冊にまとめた本です。</span></li>
    <li><a href="{{ site.channels.x }}">X（AI残業部長）</a><span class="channel-desc">日々の実況と、記事のお知らせです。</span></li>
    <li><a href="{{ site.channels.youtube }}">YouTube（AI残業部）</a><span class="channel-desc">動画で手順を紹介するチャンネルです。</span></li>
    <li><a href="{{ site.channels.booth }}">BOOTH（AI残業部）</a><span class="channel-desc">テンプレートやチェックリストを置いています。まずは無料のものからどうぞ。</span></li>
    <li><a href="{{ site.channels.suzuri }}">SUZURI（AI残業部）</a><span class="channel-desc">部のグッズを置いています。着て、貼って、みんなで定時退社を目指しましょう。</span></li>
  </ul>
</section>

<section class="latest">
  <h2>新着記事</h2>
  {% if site.posts.size > 0 %}
  <ul class="post-list">
    {% for post in site.posts limit: 10 %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span class="post-list-meta">{{ post.date | date: "%Y年%-m月%-d日" }}／{{ post.categories | join: "・" }}</span>
    </li>
    {% endfor %}
  </ul>
  {% else %}
  <p>記事は準備中です。最初の記事は note で公開したものを、こちらにも順に置いていきます。</p>
  {% endif %}
</section>

<section class="about-link">
  <h2>部長について</h2>
  <p>どんな人が書いているかは、<a href="{{ '/profile/' | relative_url }}">部長について</a>をご覧ください。</p>
</section>
