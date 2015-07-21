# rake_markdown_writing - DRAFT

What is this? It's a way to speed up (academic) writing  with markdown.

<!-- http://rmarkdown.rstudio.com/word_document_format.html -->

## How to use

To use, cd into the drafts folder, and simply run `rake`, that's it.

This will export and convert all markdown file with extension `.md` using pandoc, into word and pdf.

It also generates bibliography, using a bibtext file specied in the file's header, for references mentioned in the markdown files as `[@uk_trade_and_investment_landscaping_2015]` (similar to zotero word plugin).

Using `doc_style/reference.docx` you can specify the style of the word document.

And you can also add images...

## Setup
what you need to install

- pandoc
	does the converison markdown -> pdf/word
- ruby
	to run the rake file(?)

Optional 

- zotero(firefox plugin)
	to generate `bibtext` files.
- sublime text
	to write markdown with sytax hilight and get live preview(needs plugins)


## project file structure


```
.
├── README.markdown
├── bib
│   └── biblio.bib
├── csl
│   ├── american-anthropological-association.csl
│   ├── apa-annotated-bibliography.csl
│   ├── apa-cv.csl
│   ├── apa.csl
│   ├── chicago-annotated-bibliography.csl
│   └── chicago-author-date.csl
│
├── doc_style
│   ├── reference.docx
│   └── sample.jpg
├── drafts
│   ├── A_Chapter01.md
│   ├── B_Chapter02.md
│   ├── Rakefile
│   ├── Z_biblio.md
│   └── img
│       └── sample_04.jpg
└── export
    ├── draft_2015-07-21_Tue_00-16-14-871.docx
    └── draft_2015-07-21_Tue_00-16-14-871.pdf


6 directories, 16 files
```

`bibliography.md` only contains the bibliography heading, and is a place holder for the automatic generated bibliography on compile.


## Markdown(academic) writign workflow

<!-- high level overview,
- add references in zotero, 
- export into .bib file, 
- write in markdown, 
- reference your sources, 
- compile/export your writing in pdf and word -->

### Learn markdown 

1. Learn markdown 
First thing first, learn markdown

1.1 [Interactive tutorial](http://markdowntutorial.com)

1.2 [reference guide](https://guides.github.com/features/mastering-markdown/) 

## Setup zotero on firefox plugin

make project folder
<!-- screenshot -->
add entries, the quick way :

### extract reference metadata

<!-- ie on amazon screenshot, saves locally -->

<!-- check in zotero all metadata fields present, date, author, in particular + add screenshot of this. -->

### export .bib file in zotero
<!-- what is a bib file -->

export `.bib` file in zotero.

<!-- code, syntax hilight this is what it looks like -->

for instance.

```
@techreport{uk_trade_and_investment_fintech_2014,
	title = {Fintech {The} {UK}'s unique environment for growth},
	author = {UK Trade {and} Investment},
	file = {Fintech_-_The_UK_s_unique_environment_for_growth.pdf:/Users/pietropassarelli/Dropbox/UCL Msc/UCL_COURSES/TERM2/GC18 Entreprenurship/finTech/Fintech_-_The_UK_s_unique_environment_for_growth.pdf:application/pdf}
}

```

### export notes from pdf files with ZotFile
You can make your notes on the pdfs as you are reading along and then Extract Annotations from PDF Files with [ZotFile](http://zotfile.com) (a firefox plugin).

from zotFile:

>Zotfile can extracted annotations and highlighted text from many PDF files. The extracted annotations are saved in Zotero notes and you can go back to the annotation in the pdf by clicking on the link after the extracted text. PDFs are a very complex format and the extraction will never work for all files. If you can not copy & paste meaningful text from the file in your pdf viewer (open your pdf viewer (not the browser plugin), select text, copy and paste it somewhere), zotfile won’t be able to extract the highlighted text either. If you can, there is a chance that future versions of zotfile will solve the problem. When you have a pdf file that does not work or with clear spacing problems, feel free to share the file on the zotfile thread in the Zotero forum or upload it to the zotfile Zotero group in the PUT FILES HERE folder. But only share files for which you can copy and paste text! Otherwise you are wasting everyone’s time.
On Mac OS, you can also use poppler to extract pdf annotations (ZotFile Preferences -> Advanced Settings). Currently, pdf.js is more reliable and should be the default in most cases. The poppler-based tool, however, is faster and might handle certain pdf standards that are not yet supported by [pdf.js](https://github.com/mozilla/pdf.js).


## markdown template

```
---  
title: Project Title
subtitle: Project Subtitle
author: Name LastName
bibliography: ../bib/biblio.bib 
csl: 
reference-docx: ../doc_style/reference.docx
abstract: Some abstract
---  

# Hello World
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean nec dolor nec eros blandit lobortis[@uk_trade_and_investment_landscaping_2015].


## Bibliography

```

### doc detils
`title`, `subtitle`, and `author` are pretty self explanatory. 

### `bibliography`
`bibliography` is the path to where yoru `.bib` text is stored.
<!-- so in this case .. means the folder above, and then `/bib` means inside the folder `bib`, and it's the file `.bib` -->

### citation
`csl` if you want to specify the qutation style, ie hardvard, chicago etc.. 

[Here you can find a list](https://github.com/citation-style-language/styles)
<!-- can you get this from zotero? -->

### word doc style
`reference-docx` optionoal if you have a stylesheet template for word.

`reference.docx` which we'll keep in the `doc_style` folder.

this is how markdown describes the 

> Use the specified file as a style reference in producing a docx file. For best results, the reference docx should be a modified version of a docx file produced using pandoc. The contents of the reference docx are ignored, but its stylesheets and document properties (including margins, page size, header, and footer) are used in the new docx. If no reference docx is specified on the command line, pandoc will look for a file reference.docx in the user data directory (see --data-dir). If this is not found either, sensible defaults will be used. The following styles are used by pandoc: [paragraph] Normal, Compact, Title, Subtitle, Authors, Date, Abstract, Heading 1, Heading 2, Heading 3, Heading 4, Heading 5, Block Text, Definition Term, Definition, Bibliography, Body Text, Table Caption, Image Caption, Figure, FigureWithCaption; [character] Default Paragraph Font, Body Text Char, Verbatim Char, Footnote Reference, Hyperlink.


[pandoc options](http://pandoc.org/demo/example9/options.html)

NB: the implications of this `reference.docx` is that you can style your document using any other word document style, regardless of it's content.
<!--  `reference.docx` does not look at the content, just the styling of the them -->

<!-- screenshot showing how to set your own doc reference, you need to click "modify style." -->



###`abstract`
`abstract`, and abstract is what it says on the thin.

then you got your markdown text. 

### adding References in markdown
to add a quote,  if you remember your bib file:

```bibtext
@techreport{uk_trade_and_investment_landscaping_2015,
	title = {Landscaping {UK} {Fintech}},
```
to ad a quote, you take `uk_trade_and_investment_landscaping_2015`  and you write it inside square brakets using `@` like so:

```
[@uk_trade_and_investment_landscaping_2015]
```

you can also add page numbers to your references

```
[@uk_trade_and_investment_landscaping_2015 page 11-20 ]
```

<!-- re-do these examples using one that has bib fields filled in properly. -->


### adding images in markdown

```
![img text description](imgurl)

```

images are considered figures, and therefor float, in position decided by the compiler, and the caption text is deiplayeed, and they are numbered

<!-- screenshot -->


while you follow them with `\` then they will be inline, but with no caption.

```
![This image won't be a figure](img/sample_04.jpg)\
```

### adding conde (with stylax hilight)

using ``` fenced block quotes delineates a code block. 

usin it with the name of the language after the fenced block gives the color hilighting. for instance ```ruby .

if you want a nice separation from your code and your text example, you can add  `---` before and after the code, to add separation lines.


## Preview in browser

<!-- sublime plugin + live preview/reload-->

<!-- cmd shift p +screenshot -->


## concatenate multiple markdown
give letter to order them up
`AChapter1.md`, `BChapter2.md`, `ZBibliography.md`


## Convert word to markdown
if you end up collaborating with someone who is using word, and don't want to disrupt your "master file" workflow. To [convert word to markdown](http://word-to-markdown.herokuapp.com) you can use the online app. or you can [download the sorucecode](https://github.com/benbalter/word-to-markdown) (`gem install word-to-markdown`).

and from command line:

```bash
$ w2m path/to/document.docx
```

<!-- do another bash script to convert word back to markdown as wella s folder structure -->

## Footnotes
<!-- footnotes 
http://wcm1.web.rice.edu/my-academic-book-in-plain-text.html 

 as crucial to establishing the credibility of
unconventional therapies.[^9]

[^9]: See Charles E. Rosenberg, “The Therapeutic Revolution: Medicine, Meaning, and Social Change in Nineteenth-Century America,” *Perspectives in Biology and Medicine* 20 (Summer 1977): 485–506;
Steven Shapin, “Trusting George Cheyne: Scientific Expertise, Common Sense, and Moral Authority in Early Eighteenth-Century Dietetic  Medicine,” *Bulletin of the History of Medicine* 77 (Summer 2003): 263–297; Cayleff, *Wash and Be Healed*. For an account of Harriet Beecher Stowe's conversion to hydropathy that reflects this historiography and emphasizes broad cultural factors, see Joan D.
Hedrick, *Harriet Beecher Stowe: A Life* (New York: Oxford University Press, 1994), 173--85.

https://raw.githubusercontent.com/wcaleb/website/master/research/trusting-water-cure.txt

https://scholarship.rice.edu/bitstream/handle/1911/64493/mcdaniel-shear2012.pdf
-->

## Export markdown to word /pdf
<!-- run rake in terminal from drafts folder
    what's terminal, ways to write comand/interact/navigate the computer + screenshot of DOS before GUI.
Screenshots:
+ open terminal
+ cd to draft,  or copy in finder and cd+paste
+ rake
that's it.
 -->

<!-- 
$ pandoc -S -o ../export/draft_terminal-test.docx --filter pandoc-citeproc A_Chapter01.md B_Chapter02.md Z_biblio.md  --reference-docx=../doc_style/reference.docx 

$ open ../export/draft_terminal-test.docx 
-->

## Sources and resources

- [http://lincolnmullen.com/blog/rake-and-pandoc/]
- [rake languag] (http://martinfowler.com/articles/rake.html) - if you want to modify the script

<!-- https://howistart.org/posts/ruby/1 -->