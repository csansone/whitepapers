# Publish Documentation To Github With MkDocs -- Easily

If you appreciate the simplicity of things like markdown and python, you would probably expect it to be simple to write your project documentation using these tools and get it up on the web for all to see... and it is.

## So, what's the problem?

As often happens in the world of software development, there is no *one true way* to get this done.

- If your project is published to [pypi](https://pypi.org/), you can have your docs hosted on [pythonhosted](https://pythonhosted.org/an_example_pypi_project/buildanduploadsphinx.html). It's awesome that they do this for the community. Your docs have to be written in reStructuredText here though, and I personally don't want to learn a new document syntax at this point in my life, so I looked further.

- Another generous, free offering is [readthedocs](https://readthedocs.org/). This lets you use markdown and MkDocs (indeed, looking into readthedocs is how I discovered the MkDocs library in the first place.), though it is a second-class citizen to sphinx. I  host a cheat sheet and it works OK. The webhooks took some time to set up initially, and ~95% of the time I just push my repository and it updates on the site. More than once though, I have been able to build my docs locally but have them throw errors on the readthedocs build. I'm a lazy guy, I wanted it to be even *easier*.

- `README.md` If your project is on the smaller side and the documentation can fit on a single page (it's the internet, a single page can be quit long, remember), you can put it on the readme page and call it a day. If you can get away with this, I recommend it. It should be noted that until [only a couple of months ago](https://dustingram.com/articles/2018/03/16/markdown-descriptions-on-pypi), pypi description pages [would not render markdown](https://coderwall.com/p/qawuyq/use-markdown-readme-s-in-python-modules) without quite a lot of unpleasant hackery.

## The solution

Github has a [pages]() feature, where you can publish things from your repository as static html and javascript files.

Sounds perfect, right? Your docs can go right in the same repository as your code, and boom! Done.

There's a little bit of a catch, though.

Github pages, at the time of this writing, offers only three sources from which you can publish:

- The `master` branch itself

    This is OK if you don't mind putting the documentation in a separate repository.

- A separate branch, named `gh-pages`

    Meh. Having a separate branch with completely different contents than the main project is a bit too *magical* for me. That said, mkdocs [does support this feature](https://www.mkdocs.org/user-guide/deploying-your-docs/) out of the box.

- The `docs` directory of your master branch

    Now we're cooking.