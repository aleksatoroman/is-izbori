# IS-Izbori

**Informacioni sistem za organizaciju i sprovođenje studentskih izbora**

Timski projekat na kursu *Informacioni sistemi*, master studije, Matematički fakultet, Univerzitet u Beogradu, školska 2026/27. godina.

Projekat obuhvata analizu i projektovanje informacionog sistema za studentske izbore, kao i funkcionalni prototip.

## Dokumentacija

Tekuća verzija projekta je [`main.pdf`](main.pdf), a prevodi se iz [`main.tex`](main.tex).

```
main.tex                          # glavni dokument (uvod, ciljevi, akteri, slučajevi upotrebe)
main.pdf                          # prevedena tekuća verzija
dfd.tex                           # dijagrami toka podataka
bpmn.tex                          # BPMN dijagrami
SlucajeviUpotrebe/                # opis svakog slučaja upotrebe u posebnom .tex fajlu
Dijagrami/                        # izvorni fajlovi dijagrama (.puml, .bpmn, .drawio)
Slike/                            # izvezene slike dijagrama (.png) koje se ubacuju u dokument
```

### Prevođenje dokumenta

Dokument se prevodi pdfLaTeX-om (npr. na Overleaf-u) ili XeLaTeX-om, odnosno [Tectonic](https://tectonic-typesetting.github.io/)-om:

```
pdflatex main.tex   # pokrenuti dva puta zbog sadržaja
tectonic main.tex   # alternativa, sam preuzima potrebne pakete
```

### Izmena dijagrama

| Vrsta dijagrama | Izvor | Alat |
|---|---|---|
| Slučajevi upotrebe, aktivnosti, sekvence, DFD | `Dijagrami/*.puml` | [PlantUML](https://plantuml.com/) (npr. ekstenzija za VS Code) |
| BPMN | `Dijagrami/*.bpmn` | [bpmn.io](https://demo.bpmn.io/) ili Camunda Modeler |
| Aktivnosti (prva iteracija) | `Dijagrami/*.drawio` | [diagrams.net](https://app.diagrams.net/) |

Nakon izmene, dijagram treba ponovo izvesti kao PNG u folder `Slike/`, pod istim imenom. PlantUML dijagrami se izvoze komandom:

```
java -jar plantuml.jar -charset UTF-8 -tpng -Sdpi=150 -o ../Slike Dijagrami/*.puml
```
