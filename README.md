Leap Presentations
==================

Clone repo:

    git clone https://leap.se/git/leap_presentations
    cd leap_presentations

Some presentations use reveal-ck gem, which makes using reveal.js much easier. Some presentations use reveal.js directly.

If using reveal-ck:

    sudo gem install reveal-ck
    cd <presentation>
    edit slides.haml or config.yml
    reveal-ck generate
    open slides/index.html

If using reveal.js directly:

    git pull
    git submodule sync && git submodule update --init
    edit and open html files directly

Directory Layout
----------------

* `tools/` : submodule(s) for tools used by the presentations, i.e. reveal-js (HTML Presentation Framework)
* `img/`: images

Presentations
-------------

* `overview`
  basic presentation (wip), currently german version is behind english
  use `file:///home/varac/leap/git/leap_presentations/overview/en.html` url in browser to start

* `ta3m`
  draft of ta3m slides.
  Uses reveal-ck