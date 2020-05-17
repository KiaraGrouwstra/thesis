# UvA master thesis

### planning 

- [x] December: finish literature review
- [x] January/February: implement dataset generation
- [x] March: implement baseline
- [ ] April: implement improvement
- [ ] May: finish experiment design
- [ ] June: perform experiment, gather results
- [ ] July: finalize write-up
- [ ] August: uitloop
- [ ] Nov: defense

### building

```bash
# verify references with biber thru docker (optional)
docker run -ti -v $PWD:/app konraifen88/biber-texlive biber --tool --validate-datamodel /app/references.bib
# install latex packages (Arch Linux):
pacman -S texlive-core texlive-latexextra
# compile
latexmk
```
