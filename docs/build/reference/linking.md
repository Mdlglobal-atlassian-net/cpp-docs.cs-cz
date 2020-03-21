---
title: Referenční zdroje k linkeru MSVC
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: d46874b5eaff889834df284ba90e6c6f196d8d66
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079516"
---
# <a name="linking"></a>Propojení

V C++ projektu je krok *propojení* proveden poté, co kompilátor zkompiluje zdrojový kód do souborů objektů (*. obj). Linker (Link. exe) kombinuje soubory objektů do jediného spustitelného souboru.

Možnosti linkeru lze nastavit uvnitř nebo vně sady Visual Studio. V rámci sady Visual Studio získáte přístup k možnostem linkeru kliknutím pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a výběrem **vlastnosti** zobrazíte stránky vlastností. V levém podokně vyberte **linker** a rozbalte uzel a zobrazte všechny možnosti.

## <a name="linker-command-line-syntax"></a>Syntaxe příkazového řádku linkeru

Když spustíte odkaz mimo sadu Visual Studio, můžete zadat vstup jedním nebo více způsoby:

- Na příkazovém řádku

- Použití souborů příkazů

- V proměnných prostředí

Propojte možnosti prvního procesu zadané v proměnné prostředí propojení a potom klikněte na možnosti v pořadí, v jakém jsou zadány na příkazovém řádku a v souborech příkazů. Pokud se možnost opakuje s jinými argumenty, má poslední zpracování přednost.

Možnosti platí pro celé sestavení; pro konkrétní vstupní soubory nelze použít žádné možnosti.

Pro spuštění odkazu. EXE použijte následující syntaxi příkazu:

```
LINK arguments
```

`arguments` zahrnují možnosti a názvy souborů a lze je zadat v libovolném pořadí. Napřed se zpracují tyto možnosti a pak soubory. Oddělte argumenty pomocí jedné nebo více mezer nebo karet.

> [!NOTE]
>  Tento nástroj můžete spustit pouze z příkazového řádku sady Visual Studio. Nemůžete ho spustit z příkazového řádku systému nebo z Průzkumníka souborů.

## <a name="command-line"></a>Příkazový řádek

V příkazovém řádku se možnost skládá z specifikátoru možnosti, buď spojovníku (-), nebo lomítko (/) následovaný názvem možnosti. Názvy možností nelze zkracovat. Některé možnosti přebírají argument zadaný za dvojtečkou (:). V rámci specifikace možnosti nejsou povoleny mezery ani tabulátory, s výjimkou řetězce v uvozovkách v možnosti/COMMENT. Zadejte číselné argumenty v desítkovém nebo jazykovém zápisu jazyka C. Názvy možností a jejich klíčové slovo nebo argumenty filename nerozlišují velká a malá písmena, ale identifikátory jako argumenty rozlišují malá a velká písmena.

Chcete-li předat souboru linkeru, zadejte název souboru na příkazovém řádku za příkazem LINK. Můžete zadat absolutní nebo relativní cestu k názvu souboru a můžete použít zástupné znaky v názvu souboru. Pokud vynecháte příponu tečky (.) a filename, odkaz předpokládá, že pro účely hledání souboru. ODKAZ nepoužívá přípony názvů souborů ani nedostatečné informace k vytvoření předpokladů o obsahu souborů; Určuje typ souboru jeho prozkoumáním a zpracuje ho odpovídajícím způsobem.

Link. exe vrátí hodnotu nula pro úspěch (bez chyb).  V opačném případě linker vrátí číslo chyby, která odkaz zastavila.  Například pokud linker generuje LINKERŮ LNK1104, linker vrátí 1104.  Tedy nejnižší číslo chyby vrácené linkerem je 1000.  Návratová hodnota 128 představuje problém s konfigurací buď s operačním systémem, nebo souborem. config; zavaděč nenačte buď Link. exe, nebo C2. dll.

## <a name="link-command-files"></a>Soubory příkazů LINK

Můžete předat argumenty příkazového řádku pro propojení ve formě souboru příkazů. K určení souboru příkazů linkeru použijte následující syntaxi:

> **Propojit \@** <em>CommandFile</em>

*CommandFile* je název textového souboru. Mezi znakem at ( **\@** ) a názvem souboru není povolen žádný prostor ani tabulátor. Neexistuje žádné výchozí rozšíření. je nutné zadat úplný název souboru včetně všech přípon. Nelze použít zástupné znaky. Můžete zadat absolutní nebo relativní cestu k názvu souboru. ODKAZ nepoužívá k vyhledání souboru proměnnou prostředí.

V souboru příkazů mohou být argumenty odděleny mezerami nebo tabulátory (jako na příkazovém řádku) a znakem nového řádku.

V souboru příkazů můžete zadat celý nebo celý příkazový řádek. V příkazu LINK můžete použít více než jeden soubor příkazů. ODKAZ přijme vstup z příkazového souboru, jako kdyby byl zadán v tomto umístění na příkazovém řádku. Soubory příkazů nelze vnořovat. ODKAZ vrátí obsah souborů příkazů, pokud není zadána možnost [/nologo](nologo-suppress-startup-banner-linker.md) .

## <a name="example"></a>Příklad

Následující příkaz pro sestavení knihovny DLL předává názvy objektů a knihoven do samostatných souborů příkazů a používá třetí příkazový soubor pro specifikaci možnosti/EXPORTS:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>Proměnné prostředí LINK

Nástroj propojení používá následující proměnné prostředí:

- ODKAZ a \_propojení\_, je-li definován. Nástroj propojení přiřadí možnosti a argumenty definované v proměnné prostředí propojení a připojí parametry a argumenty definované v proměnné prostředí \_propojení\_ k argumentům příkazového řádku před zpracováním.

- LIB, je-li definován. Nástroje pro propojení používají cestu LIB při hledání objektu, knihovny nebo jiného souboru zadaného v příkazovém řádku nebo pomocí možnosti [/Base](base-base-address.md) . Také používá cestu LIB k nalezení souboru PDB s názvem v objektu. Proměnná LIB může obsahovat jednu nebo více specifikací cesty, které jsou odděleny středníky. Jedna cesta musí ukazovat na podadresář \lib vaší vizuální C++ instalace.

- CESTA, pokud nástroj potřebuje spustit CVTRES a nemůže najít soubor ve stejném adresáři jako samotný odkaz. (Odkaz vyžaduje CVTRES k propojení souboru. res.) Cesta musí ukazovat na podadresáři \Bin vaší vizuální C++ instalace.

- TMP, chcete-li určit adresář při propojování souborů OMF nebo. res.

## <a name="see-also"></a>Viz také

[C/C++ sestavit odkaz](c-cpp-building-reference.md)
[MSVC Možnosti linkeru](linker-options.md)
[soubory definice modulu (. def)](module-definition-dot-def-files.md)
[Podpora linkeru pro odložené načítání knihoven DLL](linker-support-for-delay-loaded-dlls.md)
