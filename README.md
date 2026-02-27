# Test Repository

This is a test repository for the petrnovosad-ext95887 organization.

## 📁 Struktura adresářů (Directory Structure)

Tento repozitář obsahuje následující hlavní adresáře a soubory:

### Kořenový adresář (Root Directory)
- **`.git/`** - Git repozitář s verzovací historií projektu
- **`.gitignore`** - Soubor definující, které soubory a adresáře mají být ignorovány Gitem (zejména Gradle build artefakty)
- **`LICENSE`** - MIT licence pro tento projekt
- **`README.md`** - Tento soubor s dokumentací projektu

### Popis `.gitignore`
Soubor `.gitignore` je nakonfigurován pro Gradle projekty a ignoruje:
- `.gradle` - Gradle cache adresář
- `/build/` - Výstupní adresář s kompilovanými soubory
- `gradle-app.setting` - Gradle GUI konfigurace
- `.gradletasknamecache` - Cache názvů Gradle úloh

## 🔄 GitHub Actions

Repozitář využívá následující GitHub Actions workflows:

### Copilot Coding Agent
- **Název**: Copilot coding agent
- **Cesta**: `dynamic/copilot-swe-agent/copilot`
- **Stav**: Aktivní
- **Popis**: Automatizovaný coding agent využívající GitHub Copilot pro asistenci při vývoji

Tento workflow je dynamicky spravován GitHub Copilot agentem a pomáhá s:
- Automatizovanými úpravami kódu
- Code review
- Implementací změn na základě požadavků

## 📄 Licence

Tento projekt je licencován pod MIT licencí - viz soubor [LICENSE](LICENSE) pro detaily.

## 🚀 Začínáme

Tento repozitář je založen na Gradle build systému. Pro práci s projektem budete potřebovat:
- Java Development Kit (JDK)
- Gradle (nebo použijte Gradle wrapper, pokud je k dispozici)

## 📝 Poznámky

- Repozitář je aktuálně v základním stavu s minimální strukturou
- Používá MIT licenci z roku 2021
- Je připraven pro Gradle-based Java/Kotlin projekty

---

*Dokumentace vytvořena: 2026-02-27*
