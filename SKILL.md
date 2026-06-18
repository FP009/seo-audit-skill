---
name: seo-audit
version: 1.0.0
description: Kompleksowy audyt SEO strony według 100-punktowej checklisty (15 kategorii). Sprawdza content, nagłówki, meta tagi, grafiki, URL-e, nawigację, pliki techniczne, bezpieczeństwo, wydajność i integracje zewnętrzne.
trigger: /seo-audit
allowed-tools:
  - WebFetch
  - WebSearch
  - Bash
  - AskUserQuestion
---

## Kiedy używać tego skilla

Używaj gdy użytkownik prosi o audyt SEO strony, sprawdzenie optymalizacji, checklistę SEO lub gdy mówi "sprawdź stronę pod SEO".

## Instrukcja audytu

### Krok 1 — Pobierz URL

Jeśli użytkownik nie podał URL-a, zapytaj: "Podaj adres strony do audytu SEO."

### Krok 2 — Zbierz dane

Wykonaj następujące fetche równolegle:
1. `WebFetch(url, "Return full raw HTML source")` — główna strona
2. `WebFetch(url + "/robots.txt", "Return full content")` — robots.txt
3. `WebFetch(url + "/sitemap.xml", "Return full content")` — sitemap XML

Jeśli strona jest sklepem, pobierz też przykładową kategorię i produkt (sprawdź linki na stronie głównej).

### Krok 3 — Audytuj według checklisty

Przejdź przez WSZYSTKIE 15 kategorii poniżej. Dla każdego punktu oceń: ✅ OK / ❌ Błąd / ⚠️ Do sprawdzenia / ➖ Nie dotyczy.

---

## CHECKLISTA SEO (100 punktów)

### 1. TREŚĆ (Content) — 14 punktów

1. **Linkowanie wewnętrzne** — czy strona używa linków wewnętrznych i czy są stylizowane spójnie?
2. **Atrybuty title linków** — czy linki mają atrybut `title` z keyword?
3. **Rozmiar czcionki** — czy tekst jest min. 11px? (sprawdź CSS lub meta viewport)
4. **Duplikacja treści** — czy nie ma zduplikowanych bloków treści na stronie?
5. **Kanibalizacja słów kluczowych** — czy różne podstrony nie konkurują o te same frazy?
6. **Treść above-the-fold** — czy ważna treść jest widoczna bez scrollowania?
7. **Treść AI** — czy treść jest zmodyfikowana i unikalana (nie surowy output AI)?
8. **Keyword stuffing** — czy nie ma przesytu słów kluczowych?
9. **Format treści** — czy treść jest tekstowa (nie tylko obrazki z tekstem)?
10. **Skróty i akronimy** — czy są wyjaśniane przy pierwszym użyciu?
11. **Długość treści** — czy strony mają wystarczającą ilość tekstu?
12. **Czytelność** — czy tekst jest podzielony nagłówkami, listami, akapitami?
13. **Aktualność treści** — czy treść jest aktualna?
14. **Linki wychodzące** — czy linki zewnętrzne mają `rel="nofollow"` lub `rel="noopener"`?

### 2. ARTYKUŁY BLOGOWE — 9 punktów

15. **Tematyczna trafność** — czy artykuły odpowiadają na intencję użytkownika?
16. **Oryginalne grafiki** — czy artykuły mają własne grafiki z atrybutem `alt`?
17. **Kategorie i tagi** — czy artykuły są skategoryzowane?
18. **Blok autora** — czy artykuły mają informację o autorze?
19. **Data publikacji i aktualizacji** — czy daty są widoczne?
20. **Spis treści** — czy długie artykuły mają działający spis treści z kotwicami?
21. **Hierarchia nagłówków** — czy nagłówki tworzą logiczną strukturę (H1 → H2 → H3)?
22. **Możliwość komentowania** — czy jest sekcja komentarzy?
23. **Schema Article** — czy artykuły mają structured data typu Article/BlogPosting?

### 3. KATEGORIE SKLEPU — 4 punkty

24. **Unikalne nazwy kategorii** — czy każda kategoria ma unikalną nazwę?
25. **Opisy kategorii min. 300 słów** — czy kategorie mają rozbudowane opisy?
26. **Słowa kluczowe w opisach** — czy opisy zawierają targetowane frazy?
27. **Pozycja słów kluczowych** — czy główna fraza pojawia się na początku opisu?

### 4. PRODUKTY SKLEPU — 5 punktów

28. **Kompletne karty produktów** — czy produkty mają wszystkie info (opis, zdjęcia, cena, dostępność)?
29. **Historia cen promocyjnych** — czy pokazana jest poprzednia cena przy promocji?
30. **Unikalne opisy produktów** — czy opisy nie są skopiowane od producenta?
31. **Powiadomienia o braku w magazynie** — czy jest opcja powiadomienia?
32. **Możliwość recenzji** — czy klienci mogą wystawiać opinie?

### 5. NAGŁÓWKI STRONY (Headers) — 7 punktów

33. **Hierarchia nagłówków** — czy H1 → H2 → H3 tworzy logiczną strukturę?
34. **Jeden H1 na stronę** — czy każda podstrona ma dokładnie jeden H1?
35. **Unikalny H1 w całej witrynie** — czy H1 nie powtarza się na różnych stronach?
36. **H1 zawiera keyword** — czy H1 zawiera główną frazę kluczową strony?
37. **Menu bez H-tagów** — czy menu nawigacyjne nie używa tagów H?
38. **Footer bez H-tagów** — czy stopka nie używa tagów H?
39. **Długość H1** — czy H1 jest zwięzły (do ~70 znaków)?

### 6. META TAGI — 6 punktów

40. **Długość title** — czy title ma max 60 znaków?
41. **Title zawiera keyword** — czy title zawiera główną frazę?
42. **Meta description max 160 znaków** — czy opis meta jest odpowiedniej długości?
43. **CTA w meta description** — czy opis meta zawiera wezwanie do działania?
44. **Keyword w meta description** — czy opis zawiera targetowane frazy?
45. **Unikalność meta tagów** — czy każda podstrona ma unikalne title i description?

### 7. GRAFIKI — 6 punktów

46. **Rozdzielczość max 1920×1080px** — czy grafiki nie są za duże?
47. **Rozmiar pliku** — czy grafiki są skompresowane (WebP, AVIF, lub zoptymalizowane JPG/PNG)?
48. **Odpowiednie rozszerzenia** — czy używane są nowoczesne formaty (WebP/AVIF preferowane)?
49. **Unikalne nazwy plików** — czy pliki mają opisowe nazwy (nie img001.jpg)?
50. **Alt text** — czy wszystkie grafiki mają atrybut `alt`?
51. **Lazy loading** — czy grafiki below-the-fold używają `loading="lazy"`?

### 8. URL-E — 4 punkty

52. **Logiczna hierarchia URL** — czy URL-e odzwierciedlają strukturę witryny?
53. **Przekierowania 301** — czy stare URL-e mają poprawne przekierowania?
54. **Konsekwentny trailing slash** — czy URL-e są spójne (z `/` lub bez)?
55. **Canonical links** — czy strony z duplikatami mają tag `<link rel="canonical">`?

### 9. NAWIGACJA — 6 punktów

56. **Poprawna struktura menu** — czy menu jest czytelne i logiczne?
57. **Sticky menu** — czy menu jest widoczne podczas scrollowania?
58. **Wyszukiwarka** — czy strona ma wewnętrzną wyszukiwarkę?
59. **Breadcrumbs** — czy są breadcrumby (zwłaszcza w sklepach)?
60. **Przycisk scroll-to-top** — czy jest przycisk powrotu na górę?
61. **Dostępność (accessibility)** — czy menu działa z klawiaturą i ma ARIA labels?

### 10. STOPKA (Footer) — 6 punktów

62. **Linki do kluczowych podstron** — czy stopka linkuje do ważnych sekcji?
63. **Dokumenty prawne** — czy są linki do polityki prywatności, regulaminu, RODO?
64. **Sekcja kontaktowa** — czy stopka zawiera dane kontaktowe lub link?
65. **Linki do social media** — czy są linki do profili?
66. **Linki do kategorii** — czy stopka linkuje do głównych kategorii produktów/usług?
67. **Mapa strony HTML** — czy jest link do mapy strony?

### 11. PLIKI — 3 punkty

68. **robots.txt** — czy plik robots.txt istnieje i jest poprawnie skonfigurowany?
69. **Sitemap XML** — czy sitemap.xml istnieje i zawiera wszystkie ważne URL-e?
70. **Sitemap w Google Search Console** — czy sitemap jest przesłany do GSC? (weryfikuj pośrednio)

### 12. SKRYPTY — 3 punkty

71. **Minifikacja JS** — czy pliki JavaScript są zminifikowane?
72. **Usunięcie nieużywanych pluginów** — czy nie ma zbędnych skryptów ładowanych na każdej stronie?
73. **Skrypty w footerze** — czy ciężkie skrypty są ładowane na końcu (`</body>`)?

### 13. BEZPIECZEŃSTWO — 7 punktów

74. **Certyfikat SSL** — czy strona używa HTTPS?
75. **Brak linków HTTP** — czy wszystkie zasoby ładowane są przez HTTPS?
76. **Atrybuty target linków** — czy linki zewnętrzne mają `rel="noopener noreferrer"`?
77. **CAPTCHA** — czy formularze mają zabezpieczenie przed botami?
78. **Brak iframes z obcych źródeł** — czy nie ma podejrzanych iframes?
79. **Nagłówki bezpieczeństwa** — czy są nagłówki HTTP (X-Frame-Options, CSP, HSTS)?
80. **Aktualne pluginy/CMS** — czy CMS i wtyczki są aktualne?

### 14. ASPEKTY TECHNICZNE — 8 punktów

81. **Szybkość ładowania strony** — czy strona ładuje się poniżej 3 sekund? (Core Web Vitals)
82. **Minimalizacja Layout Shift (CLS)** — czy elementy nie "skaczą" podczas ładowania?
83. **Responsywność mobilna** — czy strona jest mobile-friendly?
84. **Schema / Structured Data** — czy strona używa schema.org (Organization, Product, FAQ, etc.)?
85. **Ustawienia indeksacji** — czy ważne strony NIE mają `noindex`?
86. **Crawlowalność** — czy bot Google może dotrzeć do wszystkich ważnych podstron?
87. **Cookie consent** — czy jest prawidłowy baner RODO?
88. **Open Graph / Twitter Cards** — czy strona ma meta OG dla social media?

### 15. NARZĘDZIA ZEWNĘTRZNE — 11 punktów

89. **Google Analytics 4** — czy GA4 jest podłączone? (sprawdź `gtag.js` lub GTM z GA4)
90. **Google Search Console** — czy jest potwierdzenie weryfikacji? (meta tag lub DNS)
91. **Bing Webmaster Tools** — czy strona jest dodana do Bing?
92. **Google Tag Manager** — czy GTM jest wdrożony?
93. **Google Merchant Center** — czy (dla sklepów) jest link do Merchant Center?
94. **Google Ads** — czy jest pixel/tag Google Ads (remarketingowy)?
95. **Google Maps / Business Profile** — czy firma ma profil Google Business?
96. **Narzędzia UX** (Hotjar/MS Clarity) — czy jest narzędzie do analizy zachowań?
97. **Marketing automation** — czy jest system do email marketingu?
98. **Facebook Pixel / Meta Ads** — czy jest piksel Meta?
99. **LinkedIn Insight Tag** — czy jest tag LinkedIn (jeśli B2B)?
100. **TikTok Pixel** — czy jest piksel TikTok?

---

## Krok 4 — Raport końcowy

Wypisz raport w następującym formacie:

```
# Audyt SEO — [nazwa domeny]
Data: [data]

## Wynik ogólny: [X]/100 punktów ([%]%)

### Podsumowanie
[2-3 zdania o ogólnym stanie SEO strony]

### Krytyczne błędy (❌)
[lista błędów do natychmiastowej naprawy]

### Do poprawy (⚠️)
[lista kwestii wymagających uwagi]

### Co działa dobrze (✅)
[lista pozytywnych elementów]

---

## Szczegółowy audyt kategorii

### 1. Treść — [X]/14
[każdy punkt z oceną i komentarzem]

### 2. Artykuły blogowe — [X]/9
...

[itd. dla wszystkich 15 kategorii]

---

## Priorytety działań

**Natychmiast:**
1. ...

**W ciągu tygodnia:**
1. ...

**Długoterminowo:**
1. ...
```

### Wskazówki do audytu

- Zamiast zgadywać, jeśli coś jest niemożliwe do sprawdzenia zdalnie (np. GSC submission), oznacz jako ➖ i daj wskazówkę jak sprawdzić samodzielnie
- Dla aspektów technicznych jak szybkość, sugeruj sprawdzenie w PageSpeed Insights
- Przy braku dostępu do backendu, bazuj na tym co widać w HTML (source code)
- Zaznacz wyraźnie, które punkty wymagają ręcznej weryfikacji przez właściciela
