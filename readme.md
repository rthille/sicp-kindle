# Original writeup
_Original work all done by twcamper_

## Slight reformatting of the pages at http://mitpress.mit.edu/sicp/full-text/book/book.html

1. I got the source:
      wget -r http://mitpress.mit.edu/sicp/full-text/book/book.html
2. used hpricot to:
    - remove 'navigation' divs
    - insert <mbp:pagebreak /> tags at the top of each html body ( this keeps lines from getting split )
3. removed cover page 'book.html' since there's already a cover image
4. set height="2em" on div tags in 'References' section (kindle doesn't support the CSS for controlling this)
5. added jump table to top of index
6. built opf and ncx with ruby.  toc.ncx allows 'nav points' for the 5-way kindle knob to get you from chapter to chapter

---

# Module Use documentation

If you want to make tweaks and/or just run the code yourself for whatever reason, follow these steps. (Note: these are *nix-oriented, but should adapt easily enough to Windows.)

1. Install [KindleGen](http://www.amazon.com/gp/feature.html?ie=UTF8&docId=1000765211).
2. Install the (deprecated but required for this plugin) hpricot module: `gem install hpricot`.
3. Update the KindleGen build string in the `build_book.rb` file:
    a. Update path to the `kindlegen` utility wherever you chose to install it -- for me, this was `/Applications/KindleGen/kindlegen` on my Mac.
    b. Update the value of `$OUTPUT` in `properties.rb`; otherwise, it will automatically generate the `.mobi` file in the root directory of the project.
4. In `lib`, run `ruby build_book.rb build ../content/sicp.opf ../content/toc.ncx`
