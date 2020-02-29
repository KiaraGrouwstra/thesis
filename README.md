# UvA master thesis

TODO (March 01):
- [x] research question
- [ ] literature review
- [ ] methodology
- [x] updated title
- [~] updated planning
- [/] any new information

### building

```bash
# verify references with biber thru docker (optional)
docker run -ti -v $PWD:/app konraifen88/biber-texlive biber --tool --validate-datamodel /app/references.bib
# compile
latexmk
```
