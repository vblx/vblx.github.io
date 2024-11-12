# vblx.github.io
static landingpage example for www.berasco.de


## Änderungen am Inhalt ##
Alles wichtige ist in hugo.toml als Klartext veraenderbar:
- Auf GitHub einloggen
- Datei editieren: https://github.com/vblx/vblx.github.io/edit/main/hugo.toml
- Gruener Button "Commit changes", optional kurze Beschreibung
  eingeben und abschicken...
- Website wird generiert, die Änderungen sollten in 1-2 Minuten sichtbar
  sein..

## Struktur / Aufbau ##
Es handelt sich hier um eine Monopage-Seite. Es gibt also keine
Unterseiten, und alles was die Navigation oben macht ist runterscrollen.
Das ist so gewollt.  Man kann sehr leicht neue Sektionen hinzufuegen,
oder vorhandene Sektionen ausblenden.

Alles was irgendwie wichtig ist und mit dem Inhalt der Seite zu tun hat,
findet sich in der "hugo.toml" Datei: Text, Eingebundene Bilder, Icons,
nacheinander in Sektionen eingeteilt so, in der gleichen Reihenfolge wie
es auf der generierten Website ist.

### hugo.toml  ###
Oben sind Page-wide settings fuer den Header der Seite und 'globale'
Dinge wie custom CSS, oder googleMapsApiKey (gelten also fuer die ganze
Seite).

Danach folgen diese Sektionen:
- hero (hero ist sozusagen das erste was man sieht)
- intro ("Start")
- work ("Leistungen")
- testimonials ("Referenzen")
- services ("Services")
- about ("Über uns")
- counters ("Berasco in Zahlen")
- contact ("Kontakt")
- footer

Alle diese Sektionen koennen sehr leicht ausgeblendet werden. Einfach
ein `enable = true` in der hugo.toml datei fuer eine Sektion in ein
`enable = false` aendern.

### icons ###
Die Seite benutzt icons und Bilder.  Die exakten Namen fuer Icons
koennen hier gefunden werden: https://simplelineicons.github.io/ Man
kann z.B. `icon = "icon-bulb"` in `icon = "icon-star"` umaendern, und
auf der Seite erscheint dann ein Stern-symbol anstelle von einer
Gluehbirne.

### bilder ###
Bilder sind in hugo.toml immer `img = dateiname.jpg` und alle bilder
liegen im Unterordner 'images'. Man kann auf GitHub in diesen ordner
einfach neue Bilder hochladen und dann in der hugo.toml in der
jeweiligen Sektion verwenden.  Die Intro Sektion mit den Kacheln ist
nach dem Hero das erste was der Kunde sieht. Hier soll der Zweck der
angezeigten info-Kacheln im Intro-bereich gut ueberlegt sein. Das
Beispiel Zeigt 3 Kacheln mit icons (man kann hier auch Bilder statt
icons nehmen!), Textbeschreibung, und einem Knopf. Damit kann man eine
Stelle der Seite scrollen, einen internen oder externen Link aufrufen,
oder ein popup mit z.B. einer Bilder-slideshow.

Es ist natuerlich auch moeglich ein Video von Vimeo oder YouTube
einzubetten.


## Kontakt Form ##
Um das "Kontakt" feature der Seite nutzen zu können, muss man erst auf
https://formspree.io/ einen Account machen, mit genau der Email addresse
auf der man später Kunden-Emails empfangen möchte.  1000 Emails pro
Monat sind gratis. Die Funktion ist getestestet und Funktioniert.


### sonstiges ###
	Weil es eine Monopage Seite ist, ohne einzelne unterseiten (wie
z.B. Blog-eintraege), ist der order "content" leer und der ordner
"archetypes", aus dem wir sonst Format fuer Blog-eintraege in mardown
etc. ableiten wuerden hat auch keine besonderen inhalte. Beide
Unterordner koennen hier ignoriert werden.  Es werden alle Sektionen der
Seite im Unterordner './layouts' gefunden und dann zu einer einzigen
index.html Seite zusammengefuegt.

Alle statischen assets der Seite sind im './static' Unterordner zu
finden, so z.B. auch CSS und Bilder in './static/css/' und
'./static/images/'

Alle HTML-bausteine fuer die verschiedenen Sektionen sind im Unterordner
'./layouts'. Besonders interessant ist hier der Unterordner
'.layouts/partials/': hier befinden sich die HTML Templates aller
Sektionen.

In './themes/hugo-elate-theme' steckt das benutzte Hugo-Theme
"Elate". Alle Dateien die im Hauptverzeichnis sind, nehmen Vorrang
gegenueber den Dateien im Theme folder. Sollte aber etwas aus dem
Hauptverzeichnis fehlen, wird es aus dem Theme unterordner
geladen. Idealerweise laesst man das Theme unveraendert und kopiert
stattdessen benoetigte Dateien dort heraus ins Hauptverzeichnis und
editiert diese dort.  Das Theme selbst ist allerdings jetzt bereits
leicht angepasst im vergleich zum Original.

---

### dev corner ###
This info is *not* needed unless you want to do everything again from
scratch!  I.e. if you want to make another blog / landing page for
another customer, you will have to repeat these steps below.  This is
the most simple incarnation of a Static blog / landingpage website
generated by [Hugo](https://gohugo.io/) hosted on [GitHub
Pages](https://pages.github.com/) using [GitHub
Actions](https://github.com/features/actions) for automatic Build &
Deploy.

#### Dev Laptop needs the following prerequisites: ####
- Have [Git](https://git-scm.com/downloads)
  [installed](https://github.com/git-guides/install-git)
  - Windows users can use ["git bash"](https://gitforwindows.org/)
  - MacOS users can use [homebrew](https://brew.sh/) `brew install git`
  - Linux users probably already have git installed.
- Optional steps for work with GitHub (note: git and github are 2
  completely different things!)
  - Optional: if you prefer a GUI client for git instead of using the
  Terminal you can install [GitHub
  Desktop](https://github.com/apps/desktop)
  - Also optional: install [gh-cli](https://cli.github.com) if you
  prefer to work on the Terminal.
- Have the [Go](https://go.dev) programming language
  [installed](https://go.dev/doc/install), or use
  '[goenv](https://github.com/go-nv/goenv)' to install a version of your
  choice (highly recommended).
- Have [Hugo](https://gohugo.io/) installed:
``` sh
  CGO_ENABLED=1 go install -tags extended github.com/gohugoio/hugo@latest
  goenv rehash #if using goenv. or just restart your shell/terminal
```

#### how everything was setup initially ####
- create a new [github](https://github.com) account and chose a username
- create a new public repo named something like 'MYGITHUBUSER.github.io'
  - example: if your GitHub username is 'asdfmyuser', the name of the
    new repo would be _exactly_ "asdfmyuser.github.io".
- on GitHub, in the repo's settings tab, under "pages" choose "deploy
from a branch" and as branch chose "gh-pages" (click save!).
- clone repo locally: `gh repo clone <repo>` (or use GitHub Desktop).
- generate new hugo site:
``` sh
  hugo new site --force MYNEWREPO #replace MYNEWREPO with actual folder!

```
- add and configure elate theme from ./hugo.toml:
``` sh
  cd MYNEWREPO #replace MYNEWREPO with actual folder!
  git submodule add https://github.com/saey55/hugo-elate-theme themes/hugo-elate-theme
  cp themes/hugo-elate-theme/exampleSite/config.toml ./hugo.toml
  $EDITOR ./hugo.toml #make changes for new site
```
- add github action in `./.github/workflows/gh-pages.yaml`
- push everything:
``` sh
  git commit -am'push recent changes' && git push
```
