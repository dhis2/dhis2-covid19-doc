tx config mapping -r covid19-support-material.index --source-lang en --type GITMAR --source-file locale/ui.pot --expression 'locale/<lang>/ui.po'

tx config mapping -r covid19-support-material.index-md -f docs/en/index.md -s en -t GITHUBMARKDOWN 'docs/<lang>/index.md'
