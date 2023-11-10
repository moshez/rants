On Notes
========

Some people keep
"notes".
In general,
as I said before,
I'm not a big fan of notes:
as far as I'm concerned,
notes are things that you have not figured
the place for.

There are some people who need notes,
some for reasons I'd disagree with
and some 
for reasons I'd agree with.
Instead of repeating myself,
I want to clarify what my position on
various platforms that keep notes
is.

In this,
I'm going to mostly ignore the use case of
"shared notes".
I'm also going to ignore the case of
"available on mobile".
This makes the discussion simpler.

Web platforms
-------------

Because this analysis takes the approach of
"desktop first",
most
SaaS products are mostly experienced as web platforms.
This category includes
Notion,
Evernote,
Trello,
and more.

The overwhelming advantage that all of these platforms have is
that backup is not an issue.
All notes are automatically backed up in the cloud.
The main problem all of these platforms have
is that the tooling is limited to what the platform,
and perhaps blessed plugins,
allow for.

Local platforms
---------------

Local platforms include
Obsidian,
Emacs Org-mode,
and other local editors.
Most of these edit local text files.

All of these can be backed up using
``git``.
Git can upload them to a software forge
(such as Gitlab or GitHub)
or to a synchronized local directory
(like Dropbox or Google Drive).
The user experience is nearly identical,
and these platforms run the entire
trade-off gamut.
Because of that,
"backup"
will be assumed to use something like
``git add . && git commit -m backup && git push``
to a main branch
and no further distinction will be made.

Obsidian
^^^^^^^^

This tool is
growing in popularity.
I can understand why!
For the people who find web platforms
unsuitable,
it seems like an odd choice:
presumably,
they are already using some editor.

Org Mode
^^^^^^^^

Org Mode refers to two things:

* A file format
* A set of editor macros to help manage this format

This exists for
Emacs
and VSCode.
If you are already using Emacs and VSCode,
this is probably a good idea.

Jupyter Notebooks
^^^^^^^^^^^^^^^^^

Jupyter notebooks can be stored in
``git``,
support Markdown in moveable cells.
Notebooks support extensions for various
ways of drawing diagrams like
PlantUML
and
Graphviz.

They also support tagging individual cells
with arbitrary tags.
These tags can be used by,
say,
``nbconvert``
to filter cells in and out.
This allows searching by tags
with a unix pipeline.

Summary
-------

As always,
the conclusion is that
you should probably use
Jupyter
to edit your notes,
unless you are an Emacs die-hard.
