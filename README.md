# UvA master thesis

- accompanying [implementation repo](https://gitlab.com/tycho01/hasktorch/tree/synthesis/synthesis/)
- [thesis defense slides](https://docs.google.com/presentation/d/1MeN00D5PjtrNtbTEnVWXk0D-uir21LUuRUk2qc-FIDI/edit?usp=sharing)
- [thesis defense recording](https://youtu.be/qpOhUXaxnQI)

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
