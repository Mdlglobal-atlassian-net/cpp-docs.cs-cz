---
title: Spuštění knihovny LIB
description: Popisuje možnosti příkazového řádku, které lze použít s nástrojem lib. exe.
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
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
ms.openlocfilehash: 871b92809f38b4dcbf84de802b1ac9940ea6f1e9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438935"
---
# <a name="running-lib"></a>Spuštění knihovny LIB

K řízení knihovny LIB lze použít různé možnosti příkazového řádku.

## <a name="lib-command-line"></a>LIB – příkazový řádek

Chcete-li spustit LIB, zadejte příkaz `lib`následovaný parametry a názvy souborů pro úlohu, pro kterou používáte LIB. LIB také přijímá vstup z příkazového řádku v souborech příkazů, které jsou popsány v následující části. LIB nepoužívá proměnnou prostředí.

## <a name="lib-command-files"></a>LIB – soubory příkazů

Argumenty příkazového řádku můžete předat do knihovny LIB v souboru příkazů pomocí následující syntaxe:

> **LIB \@** <em>příkazového souboru</em>

Soubor *Command-File* je textový soubor. Mezi znakem @ ( **\@** ) a názvem souboru nejsou povoleny mezery ani tabulátory. Název *souboru příkazu* nemá výchozí příponu. Zadejte úplný název souboru včetně všech přípon. Nelze použít zástupné znaky. Je možné zadat absolutní nebo relativní cestu s názvem souboru.

V souboru příkazů mohou být argumenty odděleny mezerami nebo kartami, jak mohou být na příkazovém řádku. Argumenty lze také oddělit znaky nového řádku. Použijte středník ( **;** ) k označení komentáře. LIB ignoruje veškerý text od středníku po konec řádku.

Do příkazového řádku můžete zadat buď všechny, nebo jenom jeho část, a v příkazu LIB můžete použít více než jeden soubor příkazů. LIB přijímá vstup z příkazového souboru, jako by byl zadán v tomto umístění na příkazovém řádku. Soubory příkazů nemůžou být vnořené. LIB vypisuje obsah souborů příkazů, pokud se nepoužije možnost **/nologo** .

## <a name="using-lib-options"></a>Použití možností LIB

Možnost se skládá z specifikátoru možnosti, který je buď spojovník ( **-** ), nebo lomítko ( **/** ) následovaný názvem možnosti. Názvy možností nejde zkracovat. Některé možnosti přebírají argument zadaný za dvojtečkou ( **:** ). Ve specifikaci možnosti nejsou povoleny mezery ani tabulátory. Jednotlivé specifikace možností lze na příkazovém řádku oddělit jednou nebo více mezerami či tabulátory. Názvy možností a jejich klíčové slovo nebo argumenty názvu souboru nerozlišují velká a malá písmena, ale identifikátory používané jako argumenty rozlišují malá a velká písmena. LIB zpracovává možnosti v pořadí zadaném v příkazovém řádku a v souborech příkazů. Pokud se možnost opakuje s jinými argumenty, má poslední zpracování přednost.

Následující možnosti platí pro všechny režimy LIB:

> **/Errorreport** \[**žádné** &#124; &#124; **odeslání** **fronty** **výzvy** &#124;

Možnost/ERRORREPORT je zastaralá. Od Windows Vista se hlášení chyb řídí nastavením [zasílání zpráv o chybách systému Windows (WER)](/windows/win32/wer/windows-error-reporting) .

> **/LINKREPRO:** _directory-Path_ \
> **/LINKREPROTARGET:** _název souboru_

Aby bylo možné pomáhat společnosti Microsoft diagnostikovat chyby a vnitřní chyby nástroje lib. exe, můžete použít možnost [/LINKREPRO](linkrepro.md) . Tato možnost vygeneruje *odkaz reprodukci*, sadu artefaktů sestavení, které umožní společnosti Microsoft reprodukování problému, ke kterému dochází během operací knihovny. Možnost [/LINKREPROTARGET](linkreprotarget.md) lze použít s možností **/LINKREPRO** . Generuje pouze artefakty reprodukci propojení, když soubor LIB. exe vytvoří zadaný soubor. Další informace najdete v tématu [postup nahlášení problému pomocí sady nástrojů Microsoftu C++ ](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

> **/LTCG**

"LTCG" představuje pro *generování kódu při propojování*. Tato funkce vyžaduje spolupráci mezi kompilátorem ([CL. exe](compiler-options.md)), lib a linkerem ([odkaz](linker-options.md)). Společně mohou optimalizovat kód nad rámec toho, co může kterákoli komponenta provádět sám sebe.

Možnost **/LTCG** pro lib určuje, že vstupy z CL. exe obsahují soubory objektů generované pomocí možnosti kompilátoru [/GL](gl-whole-program-optimization.md) . Pokud LIB nalezne takové vstupy a **/LTCG** se nezadá, restartuje se s/LTCG povolenou po zobrazení informační zprávy. Jinými slovy není nutné tuto možnost nastavit explicitně, ale zrychluje výkon sestavení. To je proto, že LIB nemusí restartovat sám sebe.

V procesu sestavení je výstup z knihovny LIB odeslán na odkaz. ODKAZ má svou vlastní samostatnou možnost **/LTCG** . Používá se k provádění různých optimalizací, včetně optimalizace celého programu a instrumentace s optimalizací na základě profilu (PGO). Další informace o možnosti propojení naleznete v tématu [/LTCG](ltcg-link-time-code-generation.md).

> **/MACHINE**

Určuje cílovou platformu pro program. Obvykle není nutné zadávat **/Machine**. LIB odvodí typ počítače ze souborů. obj. V některých případech však LIB nemůže určit typ počítače a vydá chybovou zprávu. Pokud dojde k takové chybě, zadejte **/Machine**. V režimu **/Extract** je tato možnost určena pouze pro ověřování. K zobrazení dostupných typů počítačů použijte `lib /?` na příkazovém řádku.

> **/NOLOGO**

Potlačí zobrazení zprávy o autorských právech LIB a čísla verze a zabrání v vracení souborů příkazů.

> **/VERBOSE**

Zobrazí podrobnosti o průběhu relace, včetně názvů přidávaných souborů. obj. Informace se odesílají do standardního výstupu a dají se přesměrovat na soubor.

> **/WX**[ **: No**]

Považovat upozornění za chyby. Další informace naleznete v tématu [/WX (zpracovávání upozornění linkeru jako chyby)](wx-treat-linker-warnings-as-errors.md).

Další možnosti se vztahují pouze na konkrétní režimy LIB. Tyto možnosti jsou popsány v oddílech popisujících jednotlivé režimy.

## <a name="see-also"></a>Viz také

[Referenční dokumentace ke knihovně LIB](lib-reference.md)
