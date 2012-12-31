---
layout: post
title: Don't Inherit From Struct
category: posts
---

I just finished looking through James Edward Gray II's <a title="&quot;10 Things You Didn't Know Ruby Could Do&quot; by JEG2" href="https://speakerdeck.com/jeg2/10-things-you-didnt-know-ruby-could-do">slides from his talk "10 Things You Didn't Know Ruby Could Do"</a>.

Number 64 caught my attention because I've been writing utility classes that inherit from Struct for years. (Ever since I first saw the pattern in <a title="DelayedJob's README" href="https://github.com/collectiveidea/delayed_job">DelayedJob's README</a>.)

For example, instead of this:
<pre style="padding-left: 30px;">class Name &lt; Struct.new(:first, :last)
  def full
    "#{first} #{last}"
  end
end</pre>
You should write this:
<pre style="padding-left: 30px;">Name = Struct.new(:first, :last) do
  def full
    "#{first} #{last}"
  end
end</pre>
It's not really a big deal, but the first example creates a class then immediately subclasses it.  This needlessly leaves an extra class in the hierarchy.  The second example simply assigns the created class directly to your new constant.
