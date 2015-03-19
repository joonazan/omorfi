# Omorfi–Open morphology of Finnish =

This package contains free and open source morphological lexical database for
the Finnish language. This package is licenced under GNU GPL version 3, but not
necessarily later. Licence can be found from `COPYING` file in root of the
distribution package. Other licences are possible from authors named in the
`AUTHORS`.

The dictionaries used in omorfi are [Nykysuomen sanalista](http://kaino.kotus.fi) (LGPL),  [Joukahainen](http://joukahainen.lokalisointi.org) (GPL) and
[FinnWordNet](http://www.ling.helsinki.fi/research/finnwordnet) (Princeton
Wordnet licence / GPL; relicenced with kind permission from University of
Helsinki), and [wiktionary](http://fi.Wiktionary.org) (Creative Commons
Attribution–ShareAlike). Some words have also been collected by omorfi
developers and contributors and are GPLv3 like the rest of the package.

## Downloading

Omorfi is available from [github's omorfi
repository](https://github.com/falmmie/omorfi). Future releases can be fetched
from releases tab. Past releases may be available through discontinued [google
code's omorfi page](https://code.google.com/p/omorfi).

## Dependencies

* hfst-3.8 or greater is required for omorfi versions >2014
* python-3 is needed to handle TSV database data

## Installation

Installation uses standard autotools system:

```
./configure && make && make install
```

The compiling may take forever or more depending on the hardware and settings.
The stable release versions should be compilable on average end-user systems.

If configure cannot find HFST tools, you must tell it where to find them:

```
./configure --with-hfst=${HFSTPATH}
```

Autotools system supports installation to e.g. home directory:

```
./configure --prefix=${HOME}
```

With git version you must create necessary autotools files in the host system
once, after initial checkout:

```
  ./autogen.sh
```

For further instructions, see `INSTALL`, the GNU standard install instructions
for autotools systems.

## Usage

Omorfi installs experimental scripts that are meant for easy command line based use of omorfi automata: `omorfi-analyse.sh` is a simple shell script invoking `hfst-proc` the tokenising analyser, which uses the morphological analyser to break the input into words and then analyses them. The basic usage:

```
  omorfi-analyse.sh [FILENAME]
```

So for basic analysis of a text file named `kalevala.txt` is:

```
  omorfi-analyse.sh kalevala.txt
```

or:

```
  omorfi-analyse.sh < kalevala.txt
```

The script `omorfi-interactive.sh` can be used to analyse pre-tokenised text or
input one word form at a time from the shell (N.B. the input is read raw from
command line, so special keys, such as arrows will not work).

For more information of these tools, invoke `--help`, or view their man pages:
```
  omorfi-analyse --help
  man omorfi-analyse
```

Other automata, such as tokeniser, segmentation, hyphenation or whatever, may
be available in the build directories. These should be installed into
`${prefix}/share/hfst/fi/` directory, which contains all the omorfi automata in
HFST binary format. These can be manipulated by standard HFST tools.

## Note about character codings

This implementation of morphology uses UTF-8 encoded Unicode, and all relevant
tools typically only process UTF-8 encoded format. On some systems, characters
with potential diacritics, such as ä and ö, may be encoded differently; the
implemented version uses a form of unicode where diacritics are precomposed to
characters, also known as unicode normal form C (NFC). Systems using decomposed
form (NFD), such as certain tools of Mac OS X, may experience problems.

## Contributing

Omorfi code and data are free and libre open source, modifiable and
redistributable by anyone. IRC channel [#omorfi on
Freenode](irc://Freenode/#omorfi) is particularly good for immediate discussion
about contributions. Any data or code contributed must be compatible with our
licencing policy, i.e. GNU compatible free licence.