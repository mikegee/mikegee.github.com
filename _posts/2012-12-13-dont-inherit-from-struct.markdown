---
layout: post
title: Don't Inherit From Struct
category: posts
---

I just finished looking through James Edward Gray II's [slides from his talk "10 Things You Didn't Know Ruby Could Do"][jeg-slides]</a>.

Number 64 caught my attention because I've been writing utility classes that inherit from Struct for years.
(Ever since I first saw the pattern in [DelayedJob's README][dj-readme].)

For example, instead of this:
{% highlight ruby %}
class Name &lt; Struct.new(:first, :last)
  def full
    "#{first} #{last}"
  end
end
{% endhighlight %}

You should write this:
{% highlight ruby %}
Name = Struct.new(:first, :last) do
  def full
    "#{first} #{last}"
  end
end
{% endhighlight %}

It's not really a big deal, but the first example creates a class then immediately subclasses it.
This needlessly leaves an extra class in the hierarchy.
The second example simply assigns the created class directly to your new constant.

[jeg-slides]: https://speakerdeck.com/jeg2/10-things-you-didnt-know-ruby-could-do "&quot;10 Things You Didn't Know Ruby Could Do&quot; by JEG2"
[dj-readme]: https://github.com/collectiveidea/delayed_job#readme
