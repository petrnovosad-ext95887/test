# WPS XSLT Konfigurace

Tento projekt obsahuje konfiguraci XSLT šablon pro komponentu WPS (WYSIWYS Processing Service) systému MEP.

## Přehled projektu

Projekt slouží k transformaci zdrojových XSLT souborů do SQL příkazů, které jsou následně nasazovány do databáze systému WPS. Automatizovaný pipeline zajišťuje kompletní proces od transformace až po nasazení do cílových prostředí.

## Struktura adresářů

### `/src/xslt`
Obsahuje zdrojové XSLT šablony, které definují transformační pravidla pro WPS komponentu. Tyto soubory jsou vstupem pro generování SQL příkazů.

### `/sql`
Zde jsou ukládány vygenerované SQL skripty vytvořené transformací XSLT souborů. Tyto SQL příkazy jsou připraveny pro nasazení do databáze WPS.

### `/flyway`
Obsahuje Flyway migrační skripty, do kterých jsou zabaleny vygenerované SQL příkazy. Flyway zajišťuje verzování a řízenou migraci databázových změn.

### `/.github/workflows`
GitHub Actions workflows, které automatizují celý proces transformace a nasazení.

## GitHub Actions Pipeline

Pipeline využívá následující GitHub Actions s prefixem "WPS" v názvu:

### 1. **WPS XSLT to SQL Generator**
- **Účel**: Transformuje zdrojové XSLT soubory na SQL příkazy
- **Vstup**: XSLT soubory z adresáře `/src/xslt`
- **Výstup**: SQL skripty v adresáři `/sql`

### 2. **WPS Flyway Packager**
- **Účel**: Zabalí vygenerované SQL skripty do Flyway migračních skriptů
- **Vstup**: SQL soubory z adresáře `/sql`
- **Výstup**: Flyway skripty v adresáři `/flyway`

### 3. **WPS Artifact Publisher**
- **Účel**: Vytvoří ZIP archiv a publikuje ho do Artifactory
- **Vstup**: Flyway skripty z adresáře `/flyway`
- **Výstup**: ZIP soubor publikovaný v Artifactory

### 4. **WPS Deployment Preparer**
- **Účel**: Připraví nasazení do vybraných prostředí vytvořením pull requestu
- **Vstup**: Publikovaný artifact z Artifactory
- **Výstup**: Pull request do repozitáře v organizaci `csas-ops`

## Workflow procesu

```
XSLT šablony → SQL generování → Flyway balíčkování → ZIP archiv → Artifactory → PR do csas-ops
     ↓              ↓                    ↓                 ↓             ↓              ↓
  /src/xslt      /sql              /flyway           package.zip   publikace    nasazení
```

### Kroky pipeline:

1. **Transformace XSLT → SQL**: Zdrojové XSLT soubory jsou automaticky transformovány do SQL příkazů
2. **Vytvoření Flyway skriptů**: SQL příkazy jsou zabaleny do Flyway migračních skriptů pro verzované nasazení
3. **Vytvoření ZIP archivu**: Všechny Flyway skripty jsou zabaleny do jednoho ZIP souboru
4. **Publikace do Artifactory**: ZIP archiv je nahrán do Artifactory pro správu verzí a distribuci
5. **Příprava nasazení**: Systém vytvoří pull request do repozitáře v organizaci `csas-ops` s připraveným nasazením do vybraných prostředí

## Poznámky

- Pipeline používá **pouze actions s prefixem "WPS"** v názvu
- Ostatní actions nejsou v tomto projektu využívány
- Celý proces je plně automatizovaný prostřednictvím GitHub Actions
- Nasazení do produkčních prostředí vyžaduje schválení pull requestu v csas-ops organizaci

## Licence

Tento projekt je licencován pod MIT licencí - viz soubor [LICENSE](LICENSE) pro detaily.
