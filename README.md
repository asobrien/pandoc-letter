# A simple letter template for Pandoc

This template allows you to write letters in Markdown and convert them to nice looking PDFs using [Pandoc][] and [LaTeX][]. It's basically just a copy of Pandoc's [default LaTeX template][latex-template], slightly modified to accept arguments used in the LaTeX letter class, including:

* opening
* closing
* address
* return-address

Additional options inlude:

* links-as-notes -- turns URLs into footnotes
* address-caps -- if specified places small caps as the first line of address



All of which can be specified in a YAML metadata block. For example:

	---
	author: Aaron
	opening: To whom it may concern,
	closing: Sincerely,
	address: 
	 - 123 Street Rd
	 - Chicago, IL
	return-address: 
	 - My Home
	 - 456 Road St.
	 - New York, NY

	 # OPTIONAL ARGUMENTS #
	 links-as-notes: true
	 address-caps: Company Name
	...

Note that each address component should start with a hypen. The provided example letter can be compiled with the following command:

```
pandoc --template=simple-letter.tex example/letter.md -o letter.pdf
```

If you want to use this template globally with Pandoc, then move `simple-letter.tex` into `~/.pandoc/templates`. If that folder doesn't yet exist, go ahead and create it.

[Pandoc]: http://johnmacfarlane.net/pandoc/
[LaTeX]: http://www.latex-project.org/
[latex-template]: https://github.com/jgm/pandoc-templates