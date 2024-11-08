# berasco.github.io
static weblog www.berasco.de

### dev corner ###
#### how everything was setup initially ####
- create a new [github](https://github.com) account
- create a new public github repo named 'MYNEWREPO.github.io'
- in repo settings, under "pages" choose "deploy from a branch" and as
  branch chose "gh-pages" (click save!)
- have [git](https://git.scm) and [gh-cli](https://cli.github.com) installed
- clone repo locally: `gh repo clone <repo>`
- have [Go installed](https://go.dev/doc/install), or use
  '[goenv](https://github.com/go-nv/goenv)'.
- install hugo locally:
``` sh
  CGO_ENABLED=1 go install -tags extended github.com/gohugoio/hugo@latest
  goenv rehash #if using goenv. otherwise restart your shell
```
- generate new hugo site:
``` sh
  hugo new site --force MYNEWREPO # replace with local repo folder!
```
- add and configure elate theme from ./hugo.toml:
``` sh
  cd MYNEWREPO
  git submodule add https://github.com/saey55/hugo-elate-theme themes/hugo-elate-theme
  cp themes/hugo-elate-theme/exampleSite/config.toml ./hugo.toml
  $EDITOR ./hugo.toml
```
- add github action in `./.github/workflows/gh-pages.yaml`
- push everything:
``` sh
  git commit -am'push recent changes' && git push
```
