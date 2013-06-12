---
layout: post
category: posts
title: Reset Sidekiq Stats
---

![Sidekiq Stats at Zero](/images/sidekiq_stats_at_zero.png)

{% highlight ruby %}
Sidekiq::Stats.new.reset
{% endhighlight %}

was added to the API in [this pull request](https://github.com/mperham/sidekiq/pull/888)
