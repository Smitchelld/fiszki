# DryRun: fiszki przed rozmową

> **Wersja demo**, a DryRun to na razie nazwa robocza. Projekt powstał we współpracy z [Claude](https://claude.ai) (Anthropic): z pomocą AI powstały strona i pierwsza baza pytań.

Pytania rekrutacyjne na **Junior Python Web Developer** i **Junior DevOps**, przewijane na telefonie jak rolki: jedna karta na ekran.

**Strona:** https://fiszki.smitchelld.dev

- dwa typy kart: fiszka (tapnij, żeby odsłonić odpowiedź, potem „Wiedziałem” / „Nie wiedziałem”) i pytanie wyboru (losowa kolejność odpowiedzi, wyjaśnienie po kliknięciu);
- pytania, na które odpowiedziałeś źle, wracają na początek następnej sesji;
- kategorie: Python, Web, HTTP, Projektowanie, Git, SQL, Algorytmy, Docker, Kubernetes, Linux, CI/CD, Sieci, Chmura, Bezpieczeństwo, Miękkie;
- własne pytania dodasz przyciskiem **+** i wyeksportujesz jako JSONL;
- postęp zapisuje się w przeglądarce (`localStorage`), bez kont i bez backendu.

## Uruchomienie lokalnie

```bash
cd docs
python -m http.server 8000
```

Otwórz `http://localhost:8000`. Telefon w tej samej sieci Wi-Fi: `http://<IP komputera>:8000`.

## Format pytań

`docs/questions.jsonl`, jedno pytanie na linię:

```json
{"id": "git-001", "kategoria": "git", "typ": "fiszka", "pytanie": "…", "odpowiedz": "…"}
{"id": "http-001", "kategoria": "http", "typ": "wybor", "pytanie": "…", "opcje": ["400", "404", "500"], "poprawna": 1, "wyjasnienie": "…"}
```

`poprawna` to indeks w `opcje`, liczony od 0. Odpowiedzi do 220 znaków, żeby karta zmieściła się na ekranie telefonu. Kod w odwrotnych apostrofach: `` `git stash` ``.
