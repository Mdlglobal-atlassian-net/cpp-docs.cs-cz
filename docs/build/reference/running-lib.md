---
title: Spuštění knihovny LIB | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- Lib
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
dev_langs:
- C++
helpviewer_keywords:
- -MACHINE target platform option
- command files, LIB
- MACHINE target platform option
- colon command files
- VERBOSE library manager option
- /NOLOGO library manager option
- dash option specifier
- /MACHINE target platform option
- forward slash option specifier
- -NOLOGO library manager option
- LIB [C++], running LIB
- -VERBOSE library manager option
- /VERBOSE library manager option
- command files
- NOLOGO library manager option
- slash (/)
- semicolon, command files
- / command files
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d8a221a829d3cded8d974c608bdd27edab07f60
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235413"
---
# <a name="running-lib"></a>Spuštění knihovny LIB

Různé možnosti příkazového řádku umožňuje řízení LIB.

## <a name="lib-command-line"></a>Lib – příkazový řádek

Spuštění knihovny LIB, zadejte příkaz `lib` následovaný možností a názvy souborů pro úlohu používáte LIB provádět. LIB také přijímá vstup příkazového řádku v souborech příkazů, které jsou popsány v následující části. Nepoužívat proměnnou prostředí LIB.

> [!NOTE]
> Pokud jste zvyklí LINK32.exe a LIB32.exe nástroje zadaný s Microsoft Win32 Software Development Kit pro Windows NT, pravděpodobně používáte buď příkaz `link32 -lib` nebo příkaz `lib32` pro správu knihoven a vytváření Importujte knihovny. Nezapomeňte změnit soubory pravidel a dávkové soubory použít `lib` místo příkazu.

## <a name="lib-command-files"></a>Příkazové soubory knihovny LIB

Argumenty příkazového řádku můžete předat LIB v souboru příkazů, použijte tuto syntaxi:

> **LIB \@**  <em>commandfile</em>

Soubor *commandfile* je textový soubor. Je povolená žádná mezera nebo tabulátor mezi zavináč (**\@**) a název souboru. Neexistuje žádný výchozí příponou; musíte zadat úplný název souboru, včetně všech rozšíření. Zástupné znaky nelze použít. Můžete zadat absolutní nebo relativní cestu s názvem souboru.

V souboru příkazů argumentů je možné oddělit mezerami či tabulátory, jak to jde na příkazovém řádku; také je možné oddělit znaky nového řádku. Použijte středník (**;**) k označení komentář. Lib – ignoruje veškerý text z středník na konec řádku.

Můžete zadat část nebo celý příkazový řádek v souboru příkazů a můžete použít více než jeden soubor příkazů v příkazu LIB. LIB přijímá vstupní soubor příkazů, jako kdyby byly zadány v dané oblasti na příkazovém řádku. Soubory příkazů nelze vnořit. LIB vypisuje obsah souborů příkazů, pokud není použit parametr/nologo.

## <a name="using-lib-options"></a>Pomocí možností LIB

Možnost sestává ze specifikátoru možnosti, které je buď pomlčka (**-**) nebo lomítka (**/**), následuje název možnosti. Názvy možností nelze zkracovat. Některé možnosti přijímají argument, zadané za dvojtečkou (**:**). Ve specifikaci možnosti nejsou povoleny mezery ani tabulátory. Jednotlivé specifikace možností lze na příkazovém řádku oddělit jednou nebo více mezerami či tabulátory. Názvy možností a jejich klíčového slova nebo argumenty názvů souborů nejsou velká a malá písmena, ale identifikátory používané jako argumenty jsou malá a velká písmena. Lib – zpracovává možnosti v pořadí zadaném v příkazovém řádku a v souborech příkazů. Pokud je možnost Opakovat různé argumenty, poslední z nich má být zpracován přednost.

Tyto možnosti platí pro všechny druhy LIB:

> **/ ERRORREPORT** [**NONE** &AMP;#124; **VÝZVY** &AMP;#124; **FRONTY** &AMP;#124; **ODESLAT**]

Pokud lib.exe selže v době běhu, můžete použít **/errorreport** odesílat informace společnosti Microsoft o tyto vnitřní chyby.

Další informace o **/errorreport**, naleznete v tématu [/errorreport (sestava interními chybami kompilátoru)](../../build/reference/errorreport-report-internal-compiler-errors.md).

> **/LTCG**

Zastupuje "LTCG" *generování kódu při propojování*. Tato funkce vyžaduje spolupráci mezi kompilátor ([cl.exe](compiler-options.md)), LIB a linkeru ([odkaz](linker-options.md)) k optimalizaci kódu za jakékoli součásti přínosech samostatně.

Pro LIB **parametru/LTCG** možnost určuje, že vstupy z cl.exe obsahovat objektové soubory, které byly generovány použitím [/GL](gl-whole-program-optimization.md) – možnost kompilátoru. Pokud tyto vstupy zaznamená LIB a **parametru/LTCG** není zadán, bude pomocí parametru/LTCG povolena poté, co zobrazení informačních zpráv restartujte. Jinými slovy není nutné explicitně nastavit tuto možnost, ale jeho zrychluje výkon sestavení to provést, protože není potřeba restartovat LIB.

V procesu sestavení na odkaz přijde výstup LIB. PROPOJENÍ má svůj vlastní samostatný **parametru/LTCG** možnost, která se používá k provádění různých optimalizací, včetně celého programu optimalizace a optimalizace na základě profilu (PGO) instrumentace. Další informace o možnosti propojení naleznete v tématu [parametru/LTCG](ltcg-link-time-code-generation.md).

> **/ MACHINE**

Určuje cílovou platformu programu. Obvykle není potřeba zadat/Machine. LIB odvodí typ počítače ze souborů .obj. V některých případech však LIB nelze určit typ počítače a vydává chybovou zprávu. Pokud k takové chybě dojde, zadejte volbu /MACHINE. V režimu/extract tato možnost se týká jenom k ověření. Použití `lib /?` příkazového řádku, chcete-li zobrazit typy dostupných počítačů.

> **/NOLOGO**

Potlačí zobrazení LIB o autorských právech zprávu a číslo verze a zabraňuje zobrazování souborů příkazu.

> **/ VERBOSE**

Zobrazí podrobnosti o průběhu relace, včetně názvů přidávané soubory .obj. Informace odeslány na standardní výstup a je možné přesměrovat do souboru.

> **/WX**[**: NO**]

Zpracovávat upozornění jako chyby. Zobrazit [/WX (zpracovávat upozornění Linkeru jako chyb)](../../build/reference/wx-treat-linker-warnings-as-errors.md) Další informace.

Další možnosti platí jenom pro konkrétní druhy LIB. Tyto možnosti jsou popsány v části popisující oba režimy.

## <a name="see-also"></a>Viz také

[Referenční dokumentace ke knihovně LIB](../../build/reference/lib-reference.md)
