# KACTL Team Notebook

The team reference notebook that **BAUET Twisted Minds**, a programming contest team from BAUET (Bangladesh Army University of Engineering & Technology), took to the **IUT 11th National ICT Fest Programming Contest 2024**. It is a 25-page, three-column PDF of copy-pasteable C++ algorithms and notes. The notebook is built from [KACTL](https://github.com/kth-competitive-programming/kactl), the ICPC team reference document of [KTH](https://en.wikipedia.org/wiki/KTH_Royal_Institute_of_Technology).

The team made these changes to KACTL:

- **Cover page:** a new cover with the university, the team, the contest and the BAUET logo.
- **Contest template:** KACTL's short contest template replaced with the team's own longer one.
- **Our Snippets:** a new chapter of personal snippets from each team member.
- **Algorithm selection:** a different choice of algorithms in several chapters. The graph chapter is left out of the PDF entirely.

The current build is from 26 April 2024.

**Read the notebook:** [kactl.pdf](kactl.pdf)

## Team

- Md. Arik Rayhan
- Md. Ohiduzaman Pranto
- Ratul Hasan

## Contents

| Chapter | Source | In the PDF |
| --- | --- | --- |
| Contest: template, file input/output snippet, troubleshooting checklist | [content/contest/](content/contest/) | Yes |
| Mathematics | [content/math/](content/math/) | Yes |
| Data structures | [content/data-structures/](content/data-structures/) | Yes |
| Numerical | [content/numerical/](content/numerical/) | Yes |
| Number theory | [content/number-theory/](content/number-theory/) | Yes |
| Combinatorial | [content/combinatorial/](content/combinatorial/) | Yes |
| Graph | [content/graph/](content/graph/) | No (commented out in `content/kactl.tex`) |
| Geometry | [content/geometry/](content/geometry/) | Yes |
| Strings | [content/strings/](content/strings/) | Yes |
| Various | [content/various/](content/various/) | Yes |
| Our Snippets: [arik.cpp](content/own-data/arik.cpp), [ratul.cpp](content/own-data/ratul.cpp), [pranto.cpp](content/own-data/pranto.cpp) | [content/own-data/](content/own-data/) | Yes |
| Appendix: problem-solving techniques | [content/appendix/](content/appendix/) | No |

Inside each chapter, the `chapter.tex` file decides which source files are printed. Files that are commented out there stay in the repository but don't appear in the PDF. Run `make showexcluded` to list them.

## Building the PDF

You need `pdflatex` (with common packages such as `listings`), Python and `make` on a Unix-like system.

```bash
make kactl     # build kactl.pdf (runs LaTeX twice)
make fast      # quicker build that runs LaTeX once
make clean     # remove build files
```

[doc/README](doc/README) has more notes on the build.

## Customizing

These notes are kept from KACTL's own README.

- `content/kactl.tex` is the main file. Edit it to change the university, team name, contest, logo and syntax highlighting, or to add or remove whole chapters. The cover logo is `content/tex/kth.pdf`. The file keeps KACTL's name but holds the BAUET logo.
- Each `content/<chapter>/chapter.tex` pulls in source files with `\kactlimport` lines. Add or remove those lines to change what's printed. For nicer alignment you can insert `\hardcolumnbreak`, `\columnbreak` or `\newpage`.
- Every algorithm gets a 6-character MD5 hash in the upper-right corner, which helps you check code you typed in by hand. Generate it with `content/contest/hash.sh` or the `:Hash` command in `content/contest/.vimrc`. The hash ignores whitespace and comments.
- The code style is terse. A few macros and typedefs from the [contest template](content/contest/template.cpp) shorten the code. Lines are at most 63 characters, indented with tabs. Each file starts with a header that gives its author, date, description, testing status and, where known, source, licence and time complexity.

## Testing

[stress-tests/](stress-tests/) compares many algorithms against a simpler brute-force version on large numbers of random cases. [old-unit-tests/](old-unit-tests/) holds a few older unit tests, which KACTL describes as broken. This copy has no CI, so run the checks yourself:

```bash
make test            # run every stress test
make test-compiles   # check that every header compiles
```

## Project structure

```
content/            LaTeX chapters and algorithm sources (one folder per chapter)
content/kactl.tex   main LaTeX file: cover page and chapter list
content/tex/        KACTL style file, preprocessor and cover logo
stress-tests/       randomized tests for the algorithms
old-unit-tests/     older unit tests
doc/                build notes, a contest strategy document and historical KACTL PDFs
kactl.pdf           compiled notebook
test-session.pdf    checklist for a contest's practice session
```

## Credits and licence

Almost all of the algorithms, the LaTeX tooling and the tests come from [KACTL](https://github.com/kth-competitive-programming/kactl) by KTH's competitive programming community and its contributors. Each source file names its original author and source.

KACTL describes its licensing as a bit unclear. Many files are marked [CC0](https://creativecommons.org/share-your-work/public-domain/cc0/) and many aren't marked at all. Everything in `stress-tests/` is implicitly CC0, except reference implementations taken from elsewhere. This repository adds no licence of its own.

## Author

Md Arik Rayhan — [mdarikrayhan.com](https://mdarikrayhan.com)
