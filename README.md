# IS-Izbori

**Informacioni sistem za organizaciju i sprovođenje studentskih izbora**

Timski projekat na kursu *Informacioni sistemi*, master studije, Matematički fakultet, Univerzitet u Beogradu, školska 2026/27. godina.

---

## O projektu

IS-Izbori je veb platforma koja podržava ceo životni ciklus studentskih izbora: od raspisivanja izbora i prijave izbornih lista, preko formiranja biračkog spiska i elektronskog glasanja, do praćenja izlaznosti i objavljivanja rezultata.

Projekat obuhvata analizu i projektovanje celog sistema (slučajevi upotrebe, UML, DFD i BPMN dijagrami, model baze podataka, arhitektura, skice korisničkog interfejsa), kao i funkcionalni prototip koji demonstrira centralni slučaj upotrebe: **elektronsko glasanje**.

### Životni ciklus izbora

1. Izborna komisija kreira izbore i definiše pravila.
2. Prijavljuju se i verifikuju izborne liste.
3. Utvrđuje se birački spisak (studenti sa pravom glasa).
4. Izbori se otvaraju za glasanje.
5. Student se prijavljuje, bira listu i glasa.
6. Izbori se zatvaraju i objavljuju se rezultati.
7. Generišu se izveštaji o izlaznosti i rezultatima.

### Korisničke uloge

| Uloga | Glavne funkcionalnosti |
|---|---|
| **Student** | Prijava na sistem, pregled dostupnih izbora, glasanje, pregled potvrde o iskorišćenom pravu glasa |
| **Izborna komisija** | Kreiranje i konfiguracija izbora, upravljanje izbornim listama, formiranje biračkog spiska, otvaranje i zatvaranje glasanja, praćenje izlaznosti, objavljivanje rezultata |
| **Administrator** | Upravljanje korisnicima, dodela uloga i ovlašćenja |

### Ključni projektni izazovi

- **Sprečavanje višestrukog glasanja i kontrola biračkog prava** – kombinacija ograničenja na nivou baze i poslovnih pravila (aktivni izbori, pravo glasa, validna lista).
- **Očuvanje tajnosti glasanja** – razdvajanje evidencije izlaznosti od evidencije glasova, uz razmatranje drugih kanala curenja informacija (vremenske oznake, logovi, prikaz rezultata tokom glasanja).
- **Transakciona konzistentnost** – provera prava, upis izlaznosti i evidentiranje glasa izvršavaju se u jednoj transakciji.
- **Kontrola pristupa i upravljanje izbornim procesom** – jasno razdvojena ovlašćenja po ulogama i stanjima izbora.

---

## Tim

| Ime i prezime | Broj indeksa | GitHub | Primarna oblast |
|---|---|---|---|
| Ime Prezime 1 | 1xxx/2026 | [@korisnik1]() | Izborni procesi, BPMN, model baze podataka |
| Ime Prezime 2 | 1xxx/2026 | [@korisnik2]() | Proces glasanja, UML, arhitektura i bezbednost |
| Ime Prezime 3 | 1xxx/2026 | [@korisnik3]() | Analiza zahteva, DFD, korisnički interfejs |

Svi članovi učestvuju u svakom projektnom zadatku. Navedene oblasti označavaju primarnu odgovornost, a ne isključivo zaduženje.

---

## Struktura repozitorijuma

```
is-izbori/
├── dokumentacija/          # Glavni LaTeX dokument projekta
│   ├── main.tex            # Glavna datoteka (uključuje poglavlja)
│   ├── main.pdf            # Tekuća verzija projekta
│   ├── poglavlja/          # Pojedinačna poglavlja (.tex)
│   └── slike/              # Slike korišćene u dokumentu
├── dijagrami/              # Izvorne datoteke dijagrama + eksportovane slike
│   ├── slucajevi-upotrebe/
│   ├── aktivnosti/
│   ├── sekvence/
│   ├── bpmn/
│   ├── dfd/
│   └── arhitektura/
├── baza/                   # ER model, dijagram tabela, SQL skripte
├── ui-skice/               # Skice korisničkog interfejsa (izvorne + PNG)
├── prototip/               # Izvorni kod funkcionalnog prototipa
│   ├── frontend/
│   └── backend/
└── demo/                   # Snimak demonstracije prototipa
```

Za svaki dijagram čuvaju se izvorne datoteke (Visual Paradigm, draw.io i sl.), kako bi mogao kasnije da se menja, kao i eksportovane slike.

---

## Dokumentacija

Glavni dokument projekta pisan je u LaTeX-u i nalazi se u direktorijumu [`dokumentacija/`](dokumentacija/). Tekuća verzija uvek je dostupna kao [`main.pdf`](dokumentacija/main.pdf).

Prevođenje dokumenta:

```bash
cd dokumentacija
latexmk -pdf main.tex
```

Izveštaji za svaki zadatak nalaze se u [Wiki sekciji](../../wiki) repozitorijuma.

---

## Prototip

Prototip demonstrira slučaj upotrebe **Elektronsko glasanje**:

1. Student se prijavljuje demonstracionim nalogom.
2. Sistem prikazuje aktivne izbore i izborne liste.
3. Student bira listu i potvrđuje izbor.
4. Backend u jednoj transakciji proverava pravo glasa, evidentira izlaznost i upisuje glas.
5. Ponovni pokušaj glasanja se odbija.
6. Rezultati po listama prikazuju se tek nakon zatvaranja izbora (tokom glasanja vidljiva je samo ukupna izlaznost).

### Planirane tehnologije

| Sloj | Tehnologija |
|---|---|
| Frontend | React |
| Backend | ASP.NET Core Web API |
| Baza podataka | PostgreSQL |
| Autentifikacija | Lokalni demonstracioni nalozi (bez integracije sa fakultetskim sistemom) |

> Tehnologije će biti konačno potvrđene u fazi predloga arhitekture (Zadatak 5).

### Pokretanje

*Uputstvo će biti dopunjeno u okviru Zadatka 7.*

```bash
# Baza podataka
psql -U postgres -f baza/schema.sql
psql -U postgres -f baza/seed.sql

# Backend
cd prototip/backend
dotnet run

# Frontend
cd prototip/frontend
npm install
npm run dev
```

---

## Plan rada

| # | Rok | Zadatak | Status |
|---|---|---|---|
| 1 | 26.10 – 02.11. | Formiran tim, repozitorijum, odobrena tema, inicijalna zaduženja | ⬜ |
| 2 | 03 – 12.11. | Prva analiza sistema, svaki član opisuje bar jedan slučaj upotrebe | ⬜ |
| 3 | 13 – 24.11. | Završena analiza, svi slučajevi upotrebe, UML, DFD, BPMN dijagrami | ⬜ |
| 4 | 25.11 – 04.12. | Model baze podataka | ⬜ |
| 5 | 05 – 13.12. | Predlog arhitekture sistema | ⬜ |
| 6 | 14 – 20.12. | Skice korisničkog interfejsa | ⬜ |
| 7 | 21.12 – 10.01. | Funkcionalni prototip i demo | ⬜ |
| 8 | 11 – 15.01. | Finalna verzija projekta (PDF) | ⬜ |
| 9 | 16 – 22.01. | Odbrana projekta | ⬜ |

Legenda: ⬜ nije započeto · 🟡 u toku · ✅ završeno
