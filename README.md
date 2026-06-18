# /seo-audit — Claude Code Skill

Kompleksowy audyt SEO strony według **100-punktowej checklisty** podzielonej na 15 kategorii.

## Instalacja

```bash
mkdir -p ~/.claude/skills/seo-audit
curl -o ~/.claude/skills/seo-audit/SKILL.md \
  https://raw.githubusercontent.com/YOUR_USERNAME/seo-audit-skill/main/SKILL.md
```

Następnie dodaj do `~/.claude/CLAUDE.md`:

```markdown
# seo-audit
- **seo-audit** (`~/.claude/skills/seo-audit/SKILL.md`) - kompleksowy audyt SEO strony według 100-punktowej checklisty. Trigger: `/seo-audit`
When the user types `/seo-audit`, invoke the Skill tool with `skill: "seo-audit"` before doing anything else.
```

## Użycie

Wpisz `/seo-audit` w Claude Code i podaj URL strony do audytu.

## Co sprawdza

| Kategoria | Punkty |
|-----------|--------|
| Treść (Content) | 14 |
| Artykuły blogowe | 9 |
| Kategorie sklepu | 4 |
| Produkty sklepu | 5 |
| Nagłówki (Headers) | 7 |
| Meta tagi | 6 |
| Grafiki | 6 |
| URL-e | 4 |
| Nawigacja | 6 |
| Stopka (Footer) | 6 |
| Pliki (robots.txt, sitemap) | 3 |
| Skrypty | 3 |
| Bezpieczeństwo | 7 |
| Aspekty techniczne | 8 |
| Narzędzia zewnętrzne | 11 |
| **RAZEM** | **100** |

## Wynik audytu

Skill generuje raport z:
- Wynikiem ogólnym (X/100 punktów)
- Listą krytycznych błędów (❌)
- Kwestiami do poprawy (⚠️)
- Co działa dobrze (✅)
- Priorytetami działań (natychmiast / tydzień / długoterminowo)

## Źródło checklisty

Oparta na checkliście SEO z [feb.net.pl](https://feb.net.pl/checklista-seo).
