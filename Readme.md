# Durham IPPP thesis template

This template is a hand-me-down from numerous people and has evolved over the
past few years. Steven Charlton worked on a number of fiddly details and fixed
much of the template, which was started by M. Imran.
Matthew Kirk altered a few details to make it suitable for [IPPP] students,
with a few touches taken from Helen Brooks' thesis.

The template aims to satisfy the university [guidelines], but these could change
at any time. The most significant change would be to the margin sizes, which are
specified in the template when the `geometry` package is loaded.

## Usage

Most of the weight of the thesis options are hidden in the `ip3thesis.cls` class
file, which is used by calling `\documentclass{ip3thesis}` at the top of your
thesis file. The class options are documented below.

Also provided is a `preamble.tex` which contains some possibly useful packages,
tool and commands.

Chapters are included using the [subfiles] package.
This is a nice package that allows you to compile either the entire thesis *or* just a single chapter without doing anything extra, just by compiling the appropriate file.
An example chapter is provided in `intro.tex`.

Bibliography support is provided by bibtex. Change the `bibliography.bib`
filename in the main file to match your bibliography file. Uses the JHEP style
by default.

## Building

Running the standard build chain including `bibtex` in any of the standard latex
writing programs should work.
However a better option is just to use [latexmk].
```
# Makes the PDF
latexmk -pdf <filename>
# Cleans up all the extra files LaTeX produces
latexmk -pdf -c <filename>
```

## Class options

By default, the thesis template will pass the options `a4paper` and `12pt` to
the underlying report class.

### Modified report options

All other options from the `report` document class can be passed to the thesis
class and will be passed through to the underlying `report` class.

#### draft
By default enables a footer with the date. This option is passed to
the underlying report class so will also highlight any overfull hboxes.

#### twoside
Typeset the document to use both sides of paper. The margins are asymmetric, so
when `twoside` is enabled the inner and outer margins will alternate between
left and right.

### Additional options

#### showframe
Show the page boundaries, heading baselines and footer baselines.

#### showkeys
Show all the labels used in captions, equations, references, citations etc.

#### thesisdraft
This is the equivalent of setting all three of `draft`, `showkeys` and
`showframe`.

#### footerdebug/nofooterdebug
Enable or disable the debug footer line showing git information (if provided),
word counts and date. This enabled by default by the `draft` option.

#### singlespacing
Use single spacing throughout the document. By default double spacing is used.

#### headerfloatpage/noheaderfloatpage
Specify whether the running head should appear on pages which only contain
floats. This is entirely a matter of preference and style, so choose what you
like the look of.

#### frontopenright
Only affects `twoside` documents. Force each section in the front matter
to open on the right.

#### chaprunninghead/nochaprunninghead
Specify whether the running head should display
"Chapter X. Name of chapter" (with `chaprunninghead`) or just "Name of chapter"
(with `nochaprunninghead`).

#### raggedtitles/noraggedtitles
Specify whether section titles should be justified (`noraggedtitles`) or be
allowed to be ragged (`raggedtitles`).

## Environments

All environments will by default be added to the table of contents, use a
starred version (e.g. `\begin{abstract*}...\end{abstract*}`) to prevent this.

None of these are required by the template and can be ommitted. Some, like the
abstract and declaration, are required for your thesis. The order these are
specified in the thesis document will determine the order in which they are
typeset.

#### dedication
Provide a dedication to someone special.

#### epigraph
Provide an inspiring quote. The environment includes a `\source{book}{author}`
command which typesets the source of the quote at that point. Either argument
can be left blank, depending on how you want it to look.

#### abstract
Typesets a half-title page with the abstract below it. The thesis [guidelines]
suggest that an abstract should be contained on a single side and be less than
300 words.

#### declaration
Your thesis needs a declaration that the work contained within it is all your
own, and that you haven't used the work to get any other qualification before.

You should also state which bits if any is based on joint work.

This environment will automatically end in the statement of copyright, as given
in the [guidelines].

#### acknowledgements
Provide any acknowledgements you wish to.

[guidelines]: https://durhamuniversity.sharepoint.com/teams/GraduateSchool/SitePages/appearance.aspx
[IPPP]: https://www.ippp.dur.ac.uk/
[latexmk]: https://ctan.org/pkg/latexmk
[subfiles]: https://www.ctan.org/pkg/subfiles
