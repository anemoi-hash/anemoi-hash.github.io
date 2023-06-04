# Anemoi website

This is the source of the official website of [anemoi-hash.github.io](https://anemoi-hash.github.io).

## Generate standalone PNG

Tikz is used to generate drawings in the paper.
To generate standalone drawings,
- copy the tex file from the directory `figures` of the paper repository
- modify the input command line 175 in `tikz-main.tex`
- run:
```
mkdir -p _build
pdflatex -output-directory=_build tikz-main.tex
convert -density 300 -background white -alpha remove -alpha off _build/tikz-main.pdf tikz-main.png
```

Be sure to use the latest release of ImageMagick.
You can compile it from source:
```
mkdir -p $HOME/.bin
git clone https://github.com/ImageMagick/ImageMagick.git
cd ImageMagick
./configure --with-modules --prefix=$HOME/.bin/ImageMagick
make -j 32
make install
```

and use `$HOME/.bin/ImageMagick/bin/convert` instead of `convert`.
