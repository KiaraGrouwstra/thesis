# UvA master thesis

### building

```bash
# verify references with biber thru docker (optional)
docker run -ti -v $PWD:/app konraifen88/biber-texlive biber --tool --validate-datamodel /app/references.bib
# install latex packages (Arch Linux):
pacman -S texlive-core texlive-latexextra texlive-science
# compile
latexmk
# compress
tar -czvf arxiv.tar.gz *.tex *.sty *.bib *.bbl figures
```
