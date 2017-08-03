# Converting Markdown to PDF
## NodeJS based solution
at this moment I'm using a node.js package that avoid to use LaTeX to do the conversion (it's actually using phantom.js):

From [StackExchange](https://softwarerecs.stackexchange.com/questions/3588/convert-markdown-to-pdf-without-latex):

So to use the CLI of [Markdown-PDF](https://www.npmjs.org/package/markdown-pdf) just:

1. Install Node.js (if necessary)
2. Install Markdown-PDF - from cmdline just run `npm install -g markdown-pdf`
3. run `markdown-pdf -o readme.pdf readme.md` (or whatever source and destination and other options you want; see CLI Options for all the details of what you can specify).

It is Open-Source (MIT licenced), and has a [Github repo](https://github.com/alanshaw/markdown-pdf), it is free and as far as I've found it is is quite fast.

## Another solution based on native apps
First, you need to have a `markdown` converter to `HTML` the basic utility is ok:

    brew install markdown

then you need another utility to convert `HTML` files to `PDF`, in this case, I'm using `htmldoc`:

    brew install htmldoc

with both utility installed, then you can use the command line:

    markdown <File.md> | htmldoc --cont --headfootsize 8.0 --linkcolor blue --linkstyle plain --format pdf14 - > FileFormat.pdf
