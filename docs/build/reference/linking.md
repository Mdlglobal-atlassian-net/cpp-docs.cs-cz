---
title: Referenční zdroje k linkeru MSVC
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 2503e212e7325fc97f9057861cb85d5cf0571094
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336489"
---
# <a name="linking"></a>Propojení

V projektu Jazyka C++ se krok *propojení* provede poté, co kompilátor zkompiloval zdrojový kód do objektových souborů (*.obj). Linker (link.exe) kombinuje soubory objektů do jednoho spustitelného souboru.

Možnosti propojovacího zařízení lze nastavit uvnitř nebo vně sady Visual Studio. V rámci sady Visual Studio získáte přístup k možnostem propojovacího programu kliknutím pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a výběrem **možnosti Vlastnosti** pro zobrazení stránek vlastností. Zvolte **Propojovací zařízení** v levém podokně, chcete-li uzel rozbalit a zobrazit všechny možnosti.

## <a name="linker-command-line-syntax"></a>Syntaxe příkazového řádku linkeru

Při spuštění link mimo Visual Studio, můžete zadat vstup jedním nebo více způsoby:

- Na příkazovém řádku

- Použití souborů příkazů

- V proměnných prostředí

LINK nejprve zpracuje možnosti zadané v proměnné prostředí LINK, následované možnostmi v pořadí, v jakém jsou určeny na příkazovém řádku a v souborech příkazů. Pokud se možnost opakuje s různými argumenty, má přednost poslední zpracovaná možnost.

Možnosti platí pro celé sestavení; u konkrétních vstupních souborů nelze použít žádné možnosti.

Chcete-li spustit LINK. EXE, použijte následující syntaxi příkazu:

```
LINK arguments
```

Zahrnout `arguments` možnosti a názvy souborů a lze zadat v libovolném pořadí. Možnosti jsou zpracovány jako první, pak soubory. K oddělení argumentů použijte jednu nebo více mezer nebo tabulátorů.

> [!NOTE]
> Tento nástroj lze spustit pouze z příkazového řádku sady Visual Studio. Nelze jej spustit ze systémového příkazového řádku nebo z Průzkumníka souborů.

## <a name="command-line"></a>Příkazový řádek

Na příkazovém řádku se možnost skládá z specifikátoru možnosti, buď pomlčky (-), nebo lomítka (/), následovaná názvem možnosti. Názvy možností nelze zkracovat. Některé možnosti trvat argument, zadaný za dvojtečkou (:). V rámci specifikace možnosti nejsou povoleny žádné mezery ani tabulátory, s výjimkou řetězce v uvozovkách v možnosti /COMMENT. Zadejte číselné argumenty v desítkovédesítice nebo zápisu v jazyce C. Názvy možností a argumenty klíčového slova nebo názvu souboru nerozlišují malá a velká písmena, ale identifikátory jako argumenty rozlišují malá a velká písmena.

Chcete-li soubor předat propojovacímu systému, zadejte název souboru na příkazovém řádku za příkazem ODKAZ. Můžete určit absolutní nebo relativní cestu s názvem souboru a můžete použít zástupné znaky v názvu souboru. Pokud vynechete tečku (.) a příponu názvu souboru, odkaz předpokládá obj pro účely nalezení souboru. LINK nepoužívá přípony názvu souboru nebo jejich nedostatek, aby se předpoklady o obsahu souborů; určuje typ souboru jeho kontrolou a podle toho jej zpracuje.

link.exe vrátí nulu pro úspěch (žádné chyby).  V opačném případě propojovací centrum vrátí číslo chyby, která zastavila propojení.  Například pokud propojovací centrum generuje LNK1104, propojovací ho vrátí 1104.  V souladu s tím je nejnižší číslo chyby vrácené při chybě propojovacím sítí 1000.  Vrácená hodnota 128 představuje problém s konfigurací operačního systému nebo souboru .config; zavaděč nenačetl ani link.exe nebo c2.dll.

## <a name="link-command-files"></a>Soubory příkazů LINK

Argumenty příkazového řádku můžete předat propojení ve formě příkazového souboru. Chcete-li zadat soubor příkazů do propojovacího systému, použijte následující syntaxi:

> ** \@PŘÍKAZOVÝ ** <em>SOUBOR</em> LINK

*Příkazový soubor* je název textového souboru. Mezi znakem at ( )**\@** a názvem souboru není povolena žádná mezera ani karta. Neexistuje žádné výchozí rozšíření; musíte zadat úplný název souboru, včetně jakékoli přípony. Zástupné znaky nelze použít. S názvem souboru můžete určit absolutní nebo relativní cestu. ODKAZ nepoužívá proměnnou prostředí k vyhledání souboru.

V souboru příkazů mohou být argumenty odděleny mezerami nebo kartami (jako na příkazovém řádku) a znaky nového řádku.

V příkazovém souboru můžete určit celý příkazový řádek nebo jeho část. V příkazu LINK můžete použít více než jeden soubor příkazů. LINK přijímá vstup příkazového souboru, jako by byl zadán v tomto umístění na příkazovém řádku. Soubory příkazů nelze vnořit. LINK odráží obsah souborů příkazů, pokud není zadána možnost [/NOLOGO.](nologo-suppress-startup-banner-linker.md)

## <a name="example"></a>Příklad

Následující příkaz k vytvoření knihovny DLL předá názvy souborů objektů a knihoven v samostatných souborech příkazů a používá třetí příkazový soubor pro specifikaci možnosti /EXPORTS:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>Proměnné prostředí LINK

Nástroj LINK používá následující proměnné prostředí:

- LINK \_a\_LINK , pokud jsou definovány. Nástroj LINK předcvádí možnosti a argumenty definované v proměnné prostředí \_LINK\_ a připojí možnosti a argumenty definované v proměnné prostředí LINK k argumentům příkazového řádku před zpracováním.

- LIB, pokud je definována. Nástroje LINK používají cestu LIB při hledání objektu, knihovny nebo jiného souboru určeného na příkazovém řádku nebo volbou [/BASE.](base-base-address.md) Používá také cestu LIB k vyhledání souboru PDB pojmenovaného v objektu. Proměnná LIB může obsahovat jednu nebo více specifikací cesty oddělených středníky. Jedna cesta musí směřovat k podadresáři \lib instalace visual c++.

- PATH, pokud nástroj potřebuje spustit CVTRES a nemůže najít soubor ve stejném adresáři jako samotný LINK. (LINK vyžaduje CVTRES pro propojení souboru .res.) CESTA musí ukazovat na podadresář \bin instalace visual c++.

- TMP, chcete-li určit adresář při propojování souborů OMF nebo RES.

## <a name="see-also"></a>Viz také

[C/C++ Stavební reference](c-cpp-building-reference.md)
[MSVC Linker Možnosti](linker-options.md)
[Modul-Definition (.def) Soubory](module-definition-dot-def-files.md)
[Linker Podpora pro zpoždění-naložené Knihovny DLL](linker-support-for-delay-loaded-dlls.md)
