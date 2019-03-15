---
title: Odkaz na MSVC linkeru
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 3a9eebef0a264b0131311b5ca96011a4d56264a1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820374"
---
# <a name="linking"></a>Propojení

V projektu v jazyce C++ *propojení* krok se provádí po kompilátor obsahuje zdrojový kód zkompilovány do souborů objektů (*.obj). Linker (link.exe) kombinuje objektových souborů v jediném spustitelném souboru. 

Možnosti linkeru můžete nastavit uvnitř nebo mimo sadu Visual Studio. V sadě Visual Studio, můžete přístup k možnosti linkeru kliknutím pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a zvolíte **vlastnosti** pro zobrazení stránky vlastností. Zvolte **Linkeru** v levém podokně rozbalte uzel a zobrazíte všechny možnosti. 


## <a name="linker-command-line-syntax"></a>Syntaxe příkazového řádku linkeru

Při spuštění odkaz mimo sadu Visual Studio, můžete zadat vstup jednu nebo více způsoby:

- Na příkazovém řádku

- Pomocí příkazu souborů

- V seznamu proměnných prostředí

ODKAZ první procesy možnosti zadané v proměnné prostředí LINK, za nímž následuje možnosti v pořadí, v jakém jsou uvedeny v příkazovém řádku a v souborech příkazů. Pokud možnost se opakuje různé argumenty, posledním blokem zpracovat přednost.

Možnosti platí pro celé sestavení; bez možností je použít na konkrétní vstupní soubory.

Ke spuštění odkaz. Soubor EXE, použijte tuto syntaxi příkazu:

```
LINK arguments
```

`arguments` Zahrnují možnosti a názvy souborů a dá se zadat v libovolném pořadí. Možnosti jsou zpracované první a soubory. K oddělení argumentů použijte mezery nebo tabulátory.

> [!NOTE]
>  Tento nástroj můžete spustit pouze z příkazového řádku sady Visual Studio. Nelze provést toto spuštění z příkazového řádku systému nebo Průzkumníka souborů.

## <a name="command-line"></a>Příkazový řádek

Na příkazovém řádku možnost sestává ze specifikátoru možnosti, pomlčku (-) nebo lomítkem (/), za nímž následuje název možnosti. Názvy možností nelze zkracovat. Některé možnosti přijímají argument, zadané za dvojtečkou (:). Mezery ani tabulátory jsou povoleny ve specifikaci možnosti, s výjimkou v rámci řetězec v uvozovkách ve variantě pro Comment. Určení argumentů v desítkovém zápisu nebo v zápisu jazyka. Názvy možností a jejich – klíčové slovo nebo název souboru argumenty nejsou velká a malá písmena, ale identifikátory jako argumenty jsou malá a velká písmena.

Do propojovacího programu předat do souboru, zadejte na příkazovém řádku po příkazu LINK název souboru. Můžete zadat absolutní nebo relativní cestu s názvem, a můžete použít zástupné znaky v názvu souboru. Pokud vynecháte tečku (.) a názvem souboru s příponou, odkaz předpokládá .obj za účelem vyhledání souboru. ODKAZ přípony názvu souboru nebo chybějící je, abyste neklikli vytvářet předpoklady o obsah souborů. Určuje typ souboru porovnáním se a zpracovává je odpovídajícím způsobem.

Link.exe vrátí hodnotu 0 pro úspěch (bez chyb).  V opačném případě vrátí linkeru číslo chyby, který zastavil na odkaz.  Například pokud linker vydá LNK1104, linker vrátí 1104.  Nejnižší číslo chyby vrácené v případě chyby linkeru odpovídajícím způsobem, je 1000.  Vrácená hodnota 128 představuje buď problém s operačním systémem nebo o soubor .config. zavaděč se nenačetla link.exe nebo c2.dll.

## <a name="link-command-files"></a>Soubory příkazů LINK

Můžete předat argumenty příkazového řádku na odkaz ve formě souboru příkazů. K určení souboru příkazů do propojovacího programu, použijte následující syntaxi:

> **ODKAZ \@**  <em>commandfile</em>

*Commandfile* je název textového souboru. Je povolená žádná mezera nebo tabulátor mezi zavináč (**\@**) a název souboru. Neexistuje žádný výchozí příponou; je nutné zadat úplný název souboru, včetně všech rozšíření. Zástupné znaky nelze použít. Můžete zadat absolutní nebo relativní cestu s názvem. ODKAZ nepoužívá proměnnou prostředí k vyhledání souboru.

V souboru příkazů, argumentů je možné oddělit mezerami či tabulátory (jako v příkazovém řádku) a znaky nového řádku.

Můžete zadat část nebo celý příkazový řádek v souboru příkazů. Můžete použít více než jeden soubor příkazů v příkazu LINK. ODKAZ přijímá vstup souboru příkazů, jako kdyby byly zadány v dané oblasti na příkazovém řádku. Soubory příkazů nelze vnořit. ODKAZ vypisuje obsah soubory příkazů, pokud [/nologo](nologo-suppress-startup-banner-linker.md) je zadána možnost.

## <a name="example"></a>Příklad

Následující příkaz pro vytvoření knihovny DLL předá názvy souborů objektů a knihoven v souborech samostatných příkazů a používá třetí příkaz specifikace možnost/EXPORTS v souboru:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>Proměnné prostředí LINK

Nástroj LINK používá následující proměnné prostředí:

- ODKAZ a \_odkaz\_, pokud je definována. Nástroj LINK připojí na začátek možnosti a argumenty, které jsou definovány v proměnné prostředí LINK a připojí možností a argumentů definované v \_odkaz\_ proměnnou prostředí pro argumenty příkazového řádku před zpracováním.

- LIB, pokud je definována. Nástroje pro propojení používá cesta ke KNIHOVNĚ při hledání objektu, knihovny nebo jiný soubor zadaný v příkazovém řádku nebo pomocí [/základní](base-base-address.md) možnost. Cesta ke KNIHOVNĚ také používá k nalezení souboru .pdb s názvem v objektu. LIB proměnné může obsahovat jeden nebo více specifikace cesty oddělené středníky. Jedna cesta musí odkazovat na podadresáři \lib instalace sady Visual C++.

- CESTA, je-li nástroj je potřeba spustit CVTRES a nemůže najít soubor ve stejném adresáři jako samotného odkazu. (Odkaz vyžaduje CVTRES propojit soubor .res). Cesta musí odkazovat na podadresáři \bin instalace sady Visual C++.

- TMP, zadejte adresář, při propojování omf – nebo .res souborů.

## <a name="see-also"></a>Viz také:

[Reference sestavení C/C++](c-cpp-building-reference.md)
[možnosti Linkeru MSVC](linker-options.md)
[soubory definice modulu (.def)](module-definition-dot-def-files.md)
[podpora Linkeru pro Knihovny DLL s odloženým načtením](linker-support-for-delay-loaded-dlls.md)
