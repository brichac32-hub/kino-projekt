# Kino Obzor

Responzivní studentský projekt pro předmět **Internetové technologie – Client Side**. Struktura vychází z dodaných wireframů v dokumentu Kino_ClientSite.pdf. Pracovní značka, filmy, tvůrci, adresa a ceny jsou ukázkové.

## Spuštění

Projekt nevyžaduje instalaci balíčků, sestavení ani databázi. V této složce je kompletní web.

1. Otevřete složku `Kino_Obzor` ve Visual Studio Code.
2. Spusťte `index.html` pomocí rozšíření Live Server.
3. Alternativně ve složce `Kino_Obzor` spusťte `python3 -m http.server 8000` a otevřete `http://localhost:8000`.

Většina funkcí funguje také při přímém otevření `index.html`. Pro konzistentní chování úložiště a Web Crypto API používejte **localhost nebo HTTPS**. Internet není potřeba: fotografie, ikony, styly i skripty jsou lokální. Web používá systémové písmo Arial / sans-serif.

## Stránky

| Soubor | Obsah |
| --- | --- |
| `index.html` | Hlavní banner, přepínání filmových tipů, karusel, program, nabídka klubu |
| `program.html` | Program na 28 dní, kombinovatelné filtry, stránkování |
| `film.html?id=za-hranici-svetla` | Detail titulu, popis, obsazení, textová upoutávka a termíny |
| `rezervace.html?show=…` | Výběr sedadel, kontaktní údaje a potvrzení rezervace |
| `obcerstveni.html` | Nabídka popcornu, nápojů a filmových menu |
| `kino-klub.html` | Prezentace účtu a navržených klubových výhod |
| `kontakt.html` | Kontakty, otevírací doba, formulář s validací a časté dotazy |
| `ucet.html` | Přihlášení, přehled rezervací a jejich zrušení |

## Co si vyzkoušet

- Přepínání tipů v banneru a filmů v karuselu.
- Kombinování dne, názvu, 2D/3D a kategorií Kino / Divadlo / Koncerty. Divadlo a koncerty se střídají po dnech, takže některé dny nemají zvolenou událost.
- Vyhledávání názvu i přes vyhledávání v hlavičce na velkém displeji.
- Detail filmu a přechod na konkrétní projekci.
- Rezervaci 1–8 míst, kontrolu povinných údajů a tisk potvrzení.
- Vytvoření účtu se smyšleným e-mailem a testovacím heslem (alespoň 8 znaků).
- Přihlášení, odhlášení, přehled rezervací na stejný e-mail a jejich zrušení.
- Reakci formulářů na prázdná pole, neplatný e-mail a neshodující se hesla.
- Mobilní menu, ovládání klávesnicí a zavření dialogu klávesou Escape.

## Struktura

```text
Kino_Obzor/
  index.html, program.html, film.html, rezervace.html
  obcerstveni.html, kino-klub.html, kontakt.html, ucet.html
  css/style.css
  js/data.js
  js/app.js
  assets/  (lokální fotografie a favicon.svg)
README.md
DOKUMENTACE.md
ZDROJE.md
```

## Hranice klientské demonstrace

Projekt neobsahuje server, databázi, skutečné platby ani odesílání e-mailů. Rezervace a účty se ukládají pouze do `localStorage` aktuálního prohlížeče; přihlášení do `sessionStorage`. Účty neposkytují skutečné zabezpečení dat a nejsou vhodné pro reálné osobní údaje. Používejte pouze testovací údaje a heslo, které nikde jinde nepoužíváte. Obnova hesla vysvětlí toto omezení, neposílá skutečný e-mail. Přehled rezervací je lokální demonstrace vztahu podle stejného e-mailu.

Heslo se neukládá jako otevřený text: Web Crypto API odvozuje hodnotu PBKDF2-SHA-256 se samostatnou náhodnou solí a 100 000 iteracemi. Toto opatření nenahrazuje serverovou autentizaci.

Ukázkový program se generuje od dnešního data na dalších 28 dní. Již vytvořené rezervace zůstávají v profilu i po uplynutí data projekce. Obsazení sedadel se sdílí jen mezi kartami stejného prohlížeče, ne mezi různými zařízeními. Souběžné rezervace mezi zařízeními by řešil až backend.

## Úpravy

- Tituly, ceny a termíny: `js/data.js`.
- Barvy, rozložení a responzivní pravidla: `css/style.css`.
- Interakce a validace: `js/app.js`.
- Obsah jednotlivých stránek: příslušný soubor HTML.

Dokumentace slouží i jako podklad pro obhajobu. Před odevzdáním doplňte autory a porovnejte výsledek s konkrétními podmínkami předmětu, které nebyly součástí zadání.
