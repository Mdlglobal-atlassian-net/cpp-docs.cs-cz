---
title: Jak nahlásit problém se sadou nástrojů Microsoft C++
description: Jak vytvořit dobrou zprávu o problému a reprodukci informací pro sadu nástrojů Microsoft C++.
ms.date: 09/24/2019
ms.technology: cpp-ide
author: corob-msft
ms.author: corob
ms.openlocfilehash: 350e902501aca5cbe2b4022ec1f977719844644b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "71685705"
---
# <a name="how-to-report-a-problem-with-the-microsoft-c-toolset-or-documentation"></a>Jak nahlásit problém se sadou nástrojů microsoft c++ nebo dokumentací

Pokud zjistíte problémy v kompilátoru Microsoft C++ (MSVC), propojovacím programu nebo jiných nástrojích a knihovnách, chceme o nich vědět. Když je problém v naší dokumentaci, chceme o tom také vědět.

## <a name="how-to-report-a-c-toolset-issue"></a>Jak nahlásit problém sady nástrojů jazyka C++

Nejlepší způsob, jak nám dát vědět o problému, je poslat nám zprávu, která obsahuje popis problému, který jste objevili. To by mělo mít všechny podrobnosti o tom, jak vytvořit svůj program. A to by mělo zahrnovat *repro*, kompletní testovací případ můžeme použít k reprodukci problému na našich vlastních strojích. Tyto informace nám umožňují rychle ověřit, že problém existuje v našem kódu a není místní pro vaše prostředí. Pomáhá nám určit, zda ovlivňuje jiné verze kompilátoru a diagnostikovat jeho příčinu.

V následujících částech si přečtete, co dělá dobrou zprávu. Popisujeme, jak vygenerovat reprodukci pro druh problému, který jste našli, a jak odeslat zprávu produktovému týmu. Vaše přehledy jsou důležité pro nás i pro ostatní vývojáře, jako jste vy. Děkujeme, že nám pomáháte vylepšovat microsoft c++!

## <a name="how-to-prepare-your-report"></a>Jak připravit sestavu

Je důležité vytvořit vysoce kvalitní zprávu, protože je pro nás obtížné reprodukovat problém, který jste našli, bez úplných informací. Čím lepší je vaše zpráva, tím efektivněji můžeme problém znovu vytvořit a diagnostikovat.

Zpráva by měla obsahovat minimálně:

- Úplné informace o verzi sady nástrojů, kterou používáte.

- Úplný příkazový řádek cl.exe použitý k vytvoření kódu.

- Podrobný popis nalezeného problému.

- Repro: kompletní, zjednodušené, samostatný příklad zdrojového kódu, který ukazuje problém.

Přečtěte si další informace o konkrétních informacích, které potřebujeme a kde je najdete, a o tom, jak vytvořit dobrou reprodukci.

### <a name="the-toolset-version"></a>Verze sady nástrojů

Potřebujeme úplné informace o verzi a cílovou architekturu sady nástrojů, která způsobuje problém. To proto, abychom mohli otestovat vaši reprodukci se stejnou sadou nástrojů na našich strojích. Pokud můžeme problém reprodukovat, tyto informace nám také poskytují výchozí bod pro zjištění, které další verze sady nástrojů mají stejný problém.

#### <a name="to-report-the-full-version-of-your-compiler"></a>Nahlášení úplné verze kompilátoru

1. Otevřete **příkazový řádek pro vývojáře,** který odpovídá verzi sady Visual Studio a konfigurační architektuře použité k vytvoření projektu. Pokud například vytváříte pomocí Visual Studia 2017 na x64 pro cíle x64, zvolte **příkazový řádek x64 Nativní nástroje pro VS 2017**. Další informace naleznete v tématu [Explorer command prompt shortcuts](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts).

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **cl /Bv**.

Výstup by měl vypadat podobně jako:

```Output
C:\Users\username\Source>cl /Bv
Microsoft (R) C/C++ Optimizing Compiler Version 19.14.26428.1 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

Compiler Passes:
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\cl.exe:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1xx.dll:      Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c2.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\link.exe:      Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\mspdb140.dll:  Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\1033\clui.dll: Version 19.14.26428.1

cl : Command line error D8003 : missing source filename
```

Zkopírujte a vložte celý výstup do sestavy.

### <a name="the-command-line"></a>Příkazový řádek

Potřebujeme přesný příkazový řádek, cl.exe a všechny jeho argumenty, které slouží k sestavení kódu. To proto, abychom to mohli postavit úplně stejným způsobem na našich strojích. Je to důležité, protože problém, který jste našli, může existovat pouze při vytváření s určitým argumentem nebo kombinací argumentů.

Nejlepší místo k nalezení těchto informací je v protokolu sestavení ihned po problému. Zajišťuje, že příkazový řádek obsahuje přesně stejné argumenty, které by mohly přispět k problému.

#### <a name="to-report-the-contents-of-the-command-line"></a>Nahlášení obsahu příkazového řádku

1. Vyhledejte soubor **CL.command.1.tlog** a otevřete jej. Ve výchozím nastavení je tento soubor \\umístěn ve složce Dokumenty ve verzi aplikace\\Visual *Studio*\\Projekty\\\\*Název_řešení Název_projektu Název_projektu*\\*Configuration*\\ *.tlog*CL.command.1.tlog nebo ve složce User*SolutionName*ve \\\\složce Source Repos\\*SolutionName*\\*Název_projektu*\\*Název_projektu*\\ *.tlog*\\CL.command.1.tlog. Pokud používáte jiný systém sestavení nebo pokud jste změnili výchozí umístění projektu, může se napojit na jiné umístění.

   Uvnitř tohoto souboru najdete názvy souborů zdrojového kódu následované argumenty příkazového řádku, které se používají ke kompilaci, každý na samostatných řádcích.

1. Vyhledejte řádek, který obsahuje název souboru zdrojového kódu, kde k problému dochází. Řádek pod ním obsahuje odpovídající argumenty příkazu cl.exe.

Zkopírujte a vložte celý příkazový řádek do sestavy.

### <a name="a-description-of-the-problem"></a>Popis problému

Potřebujeme podrobný popis problému, který jste našli. To proto, abychom si mohli ověřit, že vidíme stejný účinek na naše stroje. Je také někdy užitečné, abychom věděli, čeho jste se snažili dosáhnout a co jste očekávali, že se stane.

Dobrý popis obsahuje **přesné chybové zprávy** dané sadou nástrojů nebo přesné chování za běhu, které vidíte. Tyto informace potřebujeme k ověření, že jsme problém správně reprodukovali. Zahrnout **všechny** výstup kompilátoru, nikoli pouze poslední chybová zpráva. Potřebujeme vidět vše, co vedlo k problému, který nahlásíte. Pokud můžete duplikovat problém pomocí kompilátoru příkazového řádku, je upřednostňován výstup kompilátoru. Rozhraní IDE a další systémy sestavení může filtrovat chybové zprávy, které vidíte, nebo pouze zachytit první řádek chybové zprávy.

Pokud je problém, že kompilátor přijímá neplatný kód a negeneruje diagnostiku, zahrňte ji do sestavy.

Chcete-li nahlásit problém s chováním za běhu, uveďte **přesnou kopii** toho, co program vytiskne a co očekáváte. V ideálním případě jej vložíte do samotného výstupního `printf("This should be 5: %d\n", actual_result);`příkazu, například . Pokud se váš program zhroutí nebo přestane reagovat, uveďte to také.

Přidejte další podrobnosti, které by nám mohly pomoci diagnostikovat problém, který jste našli, například všechna zjištěná řešení. Snažte se neopakovat informace, které se nacházejí jinde v sestavě.

### <a name="the-repro"></a>Repro

*Repro* je kompletní, samostatný příklad zdrojového kódu. Reprodukovatelně demonstruje problém, který jste našli, odtud název. Potřebujeme reprodukci, abychom mohli reprodukovat chybu na našich strojích. Kód by měl být sám o sobě dostatečný k vytvoření základního spustitelného souboru, který se zkompiluje a spustí. Nebo, že *by* kompilovat a spustit, ne-li pro problém, který jste našli. Repro není fragment kódu. By měl mít úplné funkce a třídy a obsahovat všechny nezbytné #include direktivy, a to i pro standardní záhlaví.

#### <a name="what-makes-a-good-repro"></a>Co dělá dobrý repro

Dobrý repro je:

- **Minimální.** Repros by měl být co nejmenší, ale stále ukazují přesně ten problém, který jste našli. Repros nemusí být složité nebo realistické. Je třeba pouze zobrazit kód, který odpovídá Standard nebo zdokumentované implementace kompilátoru. Pro chybějící diagnostiku by měl repro zobrazit kód, který není v souladu. Jednoduché reprosy k bodu, které obsahují pouze dostatek kódu k prokázání problému jsou nejlepší. Pokud můžete odstranit nebo zjednodušit kód a zůstat v souladu a také ponechat problém beze změny, pak tak učinit. Není nutné zahrnout counter-příklady kódu, který funguje.

- **Soběstačný.** Repros by se měli vyhnout zbytečným závislostem. Pokud můžete problém reprodukovat bez knihoven jiných výrobců, uvažte. Pokud můžete reprodukovat problém bez kódu knihovny kromě jednoduché `puts("this shouldn't compile");` `std::cout << value;`výstupní `printf("%d\n", value);`příkazy (například , , a ), tak tak proveďte. Je ideální, pokud lze příklad zkondenzovat do jednoho souboru zdrojového kódu bez odkazu na záhlaví uživatelů. Snížení množství kódu, které musíme považovat za možného přispěvatele k problému, je pro nás nesmírně užitečné.

- **Proti nejnovější verzi kompilátoru.** Repros by měl používat nejnovější aktualizaci nejnovější verze sady nástrojů, kdykoli je to možné. Nebo použijte nejnovější předběžnou verzi další aktualizace nebo další hlavní verze. Problémy, které můžete najít ve starších verzích sady nástrojů, byly často opraveny v novějších verzích. Opravy jsou backportovány na starší verze pouze ve výjimečných případech.

- **Kontrolováno proti ostatním kompilátorům,** pokud je to relevantní. Repros, které zahrnují přenosný kód Jazyka C++ by měl ověřit chování proti jiným kompilátorům, pokud je to možné. Standard Jazyka C++ nakonec určuje správnost programu a žádný kompilátor není dokonalý. Však při Clang a GCC přijmout váš kód bez diagnostiky a MSVC není, pravděpodobně jste našli chybu v našem kompilátoru. (Mezi další možnosti patří rozdíly v chování Unixu a Windows nebo různé úrovně implementace standardů Jazyka C++ a tak dále.) Když všechny kompilátory odmítnou váš kód, pak je pravděpodobné, že váš kód je nesprávný. Zobrazení různých chybových zpráv vám může pomoci diagnostikovat problém sami.

   Seznamy online kompilátorů můžete otestovat proti [kompilátorům online C++](https://isocpp.org/blog/2013/01/online-c-compilers) na webu ISO C++ nebo v tomto [kurátorském seznamu kompilátorů Online C++](https://arnemertz.github.io/online-compilers/) na GitHubu. Některé konkrétní příklady zahrnují [Wandbox](https://wandbox.org/), [Compiler Explorer](https://godbolt.org/)a [Coliru](https://coliru.stacked-crooked.com/).

   > [!NOTE]
   > Online weby kompilátoru nejsou přidruženy k microsoftu. Mnoho on-line kompilátor webové stránky jsou provozovány jako osobní projekty. Některé z těchto webů nemusí být při čtení tohoto nedostupného, ale hledání by mělo najít jiné, které můžete použít.

Problémy v kompilátoru, propojovacím systému a v knihovnách mají tendenci se zobrazovat určitými způsoby. Druh problému, který najdete, určí, jaký druh repro byste měli zahrnout do sestavy. Bez vhodnérepro, nemáme co vyšetřovat. Zde je několik druhů problémů, které můžete vidět. Obsahujeme pokyny, jak generovat druh repro byste měli použít k hlášení každého druhu problému.

#### <a name="frontend-parser-crash"></a>Selhání front-endu (analyzátoru)

Front-end dojde k chybě během fáze analýzy kompilátoru. Kompilátor obvykle vydává [závažnou chybu C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md)a odkazuje na soubor zdrojového kódu a číslo řádku, na kterém došlo k chybě. Často zmiňuje soubor s názvem msc1.cpp, ale tento detail můžete ignorovat.

Pro tento druh selhání, zadejte [preprocessed repro](#preprocessed-repros).

Zde je příklad výstupu kompilátoru pro tento druh selhání:

```Output
SandBoxHost.cpp
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        fatal error C1001: An internal error has occurred in the compiler.
(compiler file 'msc1.cpp', line 1369)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        note: This diagnostic occurred in the compiler generated function
        'void Microsoft::Ceres::Common::Tools::Sandbox::SandBoxedProcess::Dispose(bool)'
Internal Compiler Error in d:\o\dev\otools\bin\x64\cl.exe.  You will be prompted
        to send an error report to Microsoft later.
INTERNAL COMPILER ERROR in 'd:\o\dev\otools\bin\x64\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

#### <a name="backend-code-generation-crash"></a>Selhání back-endu (generování kódu)

Back-endu dojde k chybě během fáze generování kódu kompilátoru. Kompilátor obvykle vydává [závažnou chybu C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md)a nemusí odkazovat na soubor zdrojového kódu a číslo řádku přidružené k problému. Často zmiňuje kompilátor\\souborů utc\\\\\\src p2 main.c, ale tento detail můžete ignorovat.

Pro tento druh selhání, zadejte [link repro,](#link-repros) pokud používáte generování kódu link-time (LTCG), povolené **/GL** argument příkazového řádku cl.exe. Pokud ne, zadejte [preprocessed repro](#preprocessed-repros) místo.

Zde je příklad výstupu kompilátoru pro selhání back-endu, ve kterém ltcg nepoužívá. Pokud výstup kompilátoru vypadá takto, měli byste zadat [předpracovanou reprodukci](#preprocessed-repros).

```Output
repro.cpp
\\officefile\public\tadg\vc14\comperror\repro.cpp(13) : fatal error C1001:
        An internal error has occurred in the compiler.
(compiler file 'f:\dd\vctools\compiler\utc\src\p2\main.c', line 230)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
INTERNAL COMPILER ERROR in
        'C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

Pokud řádek, který začíná **vnitřní chyba kompilátoru** zmiňuje link.exe, spíše než cl.exe, LTCG byla povolena. V tomto případě zadejte [reprodukci odkazu.](#link-repros) Pokud není jasné, zda LTCG byla povolena z chybové zprávy kompilátoru, zkontrolujte argumenty příkazového řádku. Zkopírovali jste je z protokolu sestavení v předchozím kroku argumentu příkazového řádku **/GL.**

#### <a name="linker-crash"></a>Selhání linkeru

Dojde k chybám propojovacího evidenčního provozu během fáze propojení po spuštění kompilátoru. Propojovací služba obvykle vyzařuje [nástroj propropojení dat Chyba LNK1000](../error-messages/tool-errors/linker-tools-error-lnk1000.md).

> [!NOTE]
> Pokud výstup zmíní C1001 nebo zahrnuje generování kódu link-time, místo toho se obraťte na [back-end (generování kódu).](#backend-code-generation-crash)

Pro tento druh havárie, zadejte [link repro](#link-repros).

Tady je příklad výstupu kompilátoru pro tento druh selhání:

```Output
z:\foo.obj : error LNK1000: Internal error during IMAGE::Pass2

  Version 14.00.22816.0

  ExceptionCode            = C0000005
  ExceptionFlags           = 00000000
  ExceptionAddress         = 00007FF73C9ED0E6 (00007FF73C9E0000)
        "z:\tools\bin\x64\link.exe"
  NumberParameters         = 00000002
  ExceptionInformation[ 0] = 0000000000000000
  ExceptionInformation[ 1] = FFFFFFFFFFFFFFFF

CONTEXT:

  Rax    = 0000000000000400  R8     = 0000000000000000
  Rbx    = 000000655DF82580  R9     = 00007FF840D2E490
  Rcx    = 005C006B006F006F  R10    = 000000655F97E690
  Rdx    = 000000655F97E270  R11    = 0000000000000400
  Rsp    = 000000655F97E248  R12    = 0000000000000000
  Rbp    = 000000655F97EFB0  E13    = 0000000000000000
  Rsi    = 000000655DF82580  R14    = 000000655F97F390
  Rdi    = 0000000000000000  R15    = 0000000000000000
  Rip    = 00007FF73C9ED0E6  EFlags = 0000000000010206
  SegCs  = 0000000000000033  SegDs  = 000000000000002B
  SegSs  = 000000000000002B  SegEs  = 000000000000002B
  SegFs  = 0000000000000053  SegGs  = 000000000000002B
  Dr0    = 0000000000000000  Dr3    = 0000000000000000
  Dr1    = 0000000000000000  Dr6    = 0000000000000000
  Dr2    = 0000000000000000  Dr7    = 0000000000000000
```

Pokud je povoleno přírůstkové propojení a k chybě došlo až po úspěšném počátečním propojení, to znamená pouze po prvním úplném propojení, na kterém je založeno pozdější přírůstkové propojení, také zadejte kopii souborů objektu (.obj) a knihovny (.lib), které odpovídají zdrojovým souborům změněným po dokončení počátečního propojení.

#### <a name="bad-code-generation"></a>Generování chybného kódu

Generování chybný kód je vzácné. Dojde k chybě, když kompilátor omylem generuje nesprávný kód, který způsobí, že aplikace dojde k chybě za běhu. Místo toho by měl generovat správný kód nebo zjistit problém v době kompilace. Pokud se domníváte, že problém, který jste našli, má za následek generování chybného kódu, zacházejte s vaší sestavou stejně jako s [selháním back-endu (generování kódu).](#backend-code-generation-crash)

Pro tento druh selhání, zadejte [link repro,](#link-repros) pokud používáte **/GL** argument příkazového řádku cl.exe. Zadejte [předpracovnou reprodukci,](#preprocessed-repros) pokud ne.

## <a name="how-to-generate-a-repro"></a>Jak generovat repro

Abychom pomohli vystopovat zdroj problému, je důležitá [dobrá repro.](#what-makes-a-good-repro) Než provedete některý z níže uvedených kroků pro konkrétní druhy repros, pokuste se co nejvíce zkondenzovat kód, který demonstruje problém. Pokuste se eliminovat nebo minimalizovat závislosti, požadovaná záhlaví a knihovny. Pokud je to možné, omezte použité možnosti kompilátoru a definice preprocesoru.

Níže jsou uvedeny pokyny pro generování různých druhů repros budete používat k hlášení různých druhů problémů.

### <a name="preprocessed-repros"></a>Předzpracované repros

*Předzpracované repro* je jeden zdrojový soubor, který ukazuje problém. Je generována z výstupu preprocesoru C. Chcete-li jej vytvořit, použijte možnost kompilátoru **/P** v původním zdrojovém souboru repro. Tato možnost vloží zahrnuté hlavičky, aby se odstranily závislosti na dalších zdrojových a hlavičkových souborech. Tato možnost také řeší makra, #ifdef podmíněných a další chod preprocesorových příkazů, které mohou záviset na místním prostředí.

> [!NOTE]
> Předzpracované repros nejsou tak užitečné pro problémy, které by mohly být výsledkem chyb v naší implementaci standardní knihovny, protože často budeme chtít nahradit naši nejnovější, probíhající implementaci, abychom zjistili, zda jsme již problém vyřešili. V takovém případě nezpracovávejte reprodukci předem a pokud nelze problém snížit na jeden zdrojový soubor, zabalte kód do souboru ZIP nebo podobně nebo zvažte použití repro projektu IDE. Další informace naleznete v [tématu Ostatní repros](#other-repros).

#### <a name="to-preprocess-a-source-code-file"></a>Předběžné zpracování souboru zdrojového kódu

1. Zachyťte argumenty příkazového řádku použité k sestavení repro, jak je popsáno v [části Nahlásit obsah příkazového řádku](#to-report-the-contents-of-the-command-line).

1. Otevřete **příkazový řádek pro vývojáře,** který odpovídá verzi sady Visual Studio a konfigurační architektuře použité k vytvoření projektu.

1. Změňte adresář, který obsahuje projekt repro.

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **cl /P** *argumenty* *filename.cpp*. Pro *argumenty*použijte seznam argumentů zachycených výše. *filename.cpp* je název souboru repro. Tento příkaz replikuje příkazový řádek, který jste použili pro reprodukci, ale zastaví kompilaci po průchodu preprocesoru. Pak zapíše předzpracovaný zdrojový kód na *filename.i*.

Pokud předběžně zpracováváte soubor zdrojového kódu Jazyka C++/CX nebo používáte funkci Moduly jazyka C++, jsou vyžadovány některé další kroky. Další informace naleznete v následujících částech.

Po vygenerování předem zpracovaného souboru je vhodné se ujistit, že se problém při kompilaci předzpracovaného souboru stále reprodukuje.

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>Chcete-li potvrdit, že předzpracovaný soubor stále reprodukuje chybu

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **cl** *arguments* **/TP** *filename.i,* který má cl.exe zkompilovat předzpracovaný soubor jako zdrojový soubor jazyka C++. *Argumenty* jsou stejné argumenty zachycené výše, ale s všechny **/D** a **/I** argumenty odebrány. Je to proto, že již byly zahrnuty do předem zpracovaného souboru. *filename.i* je název vašeho předem zpracovaného souboru.

1. Potvrďte, že problém je reprodukován.

Nakonec připojte k sestavě předzpracovaný *název souboru*repro .i.

### <a name="preprocessed-ccx-winrtuwp-code-repros"></a>Předzpracované reprosy kódu C++/CX WinRT/UpW

Pokud používáte C++/CX k vytvoření spustitelného souboru, existují některé další kroky potřebné k vytvoření a ověření předzpracované repro.

#### <a name="to-preprocess-ccx-source-code"></a>Předběžné zpracování zdrojového kódu jazyka C++/CX

1. Vytvořte předem zpracovaný zdrojový soubor, jak je popsáno v [dokumentu Chcete-li předem zpracovat soubor zdrojového kódu](#to-preprocess-a-source-code-file).

1. Vyhledejte v generovaném _souboru_.i **soubor #using** direktivy.

1. Vytvořte seznam všech odkazovaných souborů. Vynechejte všechny soubory Windows\*.winmd, soubory platform.winmd a mscorlib.dll.

Příprava na ověření, zda předzpracovaný soubor stále reprodukuje problém,

1. Vytvořte nový adresář pro předzpracovaný soubor a zkopírujte jej do nového adresáře.

1. Zkopírujte soubory .winmd ze seznamu **#using** do nového adresáře.

1. Vytvořte prázdný soubor vccorlib.h v novém adresáři.

1. Upravte předzpracovaný soubor, abyste odebrali všechny direktivy **#using** pro soubor mscorlib.dll.

1. Úpravou předem zpracovaného souboru změňte všechny absolutní cesty pouze na holé názvy souborů pro zkopírované soubory WINMD.

Zkontrolujte, zda předzpracovaný soubor stále reprodukuje problém, jak je uvedeno výše.

### <a name="preprocessed-c-modules-repros"></a>Předzpracované moduly C++ reprodukuje

Pokud používáte funkci Moduly kompilátoru Jazyka C++, jsou nutné k vytvoření a ověření předzpracované repro.

#### <a name="to-preprocess-a-source-code-file-that-uses-a-module"></a>Předběžné zpracování souboru zdrojového kódu, který používá modul

1. Zachyťte argumenty příkazového řádku použité k sestavení repro, jak je popsáno v [části Nahlásit obsah příkazového řádku](#to-report-the-contents-of-the-command-line).

1. Otevřete **příkazový řádek pro vývojáře,** který odpovídá verzi sady Visual Studio a konfigurační architektuře použité k vytvoření projektu.

1. Změňte adresář, který obsahuje projekt repro.

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **cl /P** *argumenty* *filename.cpp*. *Argumenty* jsou argumenty zachycené výše a *filename.cpp* je název zdrojového souboru, který spotřebovává modul.

1. Změňte adresář, který obsahuje projekt repro, který vytvořil rozhraní modulu (výstup .ifc).

1. Zachyťte argumenty příkazového řádku použité k vytvoření rozhraní modulu.

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **cl /P** *argumenty* *modulename.ixx*. *Argumenty* jsou argumenty zachycené výše a *modulename.ixx* je název souboru, který vytváří rozhraní modulu.

Po vygenerování předem zpracovaných souborů je vhodné se ujistit, že se problém při použití předzpracovaného souboru stále reprodukuje.

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>Chcete-li potvrdit, že předzpracovaný soubor stále reprodukuje chybu

1. V okně vývojářské konzole změňte zpět na adresář, který obsahuje váš projekt repro.

1. Zadejte příkaz **cl** *arguments* **/TP** *název souboru*.i jak je uvedeno výše, chcete-li zkompilovat předzpracovaný soubor, jako by se jednalo o zdrojový soubor Jazyka C++.

1. Zkontrolujte, zda je problém stále reprodukován předem zpracovaným souborem.

Nakonec připojte k sestavě předzpracované soubory repro (*název souboru*.i a *název modulu*.i) spolu s výstupem .ifc.

### <a name="link-repros"></a>Repros odkazů

Repro *propojení* je propojovací systém generovaný obsah adresáře, určený buď proměnnou prostředí **repro\_propojení,** nebo jako argument možnosti propojovacího zařízení [/LINKREPRO.](../build/reference/linkrepro.md) Obsahuje artefakty sestavení, které společně ukazují problém, ke kterému dochází v době propojení. Příklady zahrnují selhání back-endu zahrnující generování kódu link-time (LTCG) nebo selhání propojovacího zařízení. Tyto artefakty sestavení jsou ty potřebné jako vstup propojovacího eru, takže problém může být reprodukován. Odkaz repro lze snadno vytvořit pomocí této proměnné prostředí. Umožňuje vestavěnou funkci generování reprodukci linkeru.

#### <a name="to-generate-a-link-repro-using-the-link_repro-environment-variable"></a>Generování repro propojení pomocí proměnné prostředí link_repro

1. Zachyťte argumenty příkazového řádku použité k sestavení repro, jak je popsáno v [části Nahlásit obsah příkazového řádku](#to-report-the-contents-of-the-command-line).

1. Otevřete **příkazový řádek pro vývojáře,** který odpovídá verzi sady Visual Studio a konfigurační architektuře použité k vytvoření projektu.

1. V okně konzoly příkazového řádku vývojáře změňte adresář, který obsahuje projekt repro.

1. Zadejte **mkdir linkrepro** vytvořit adresář s názvem *linkrepro* pro odkaz repro. Můžete použít jiný název k zachycení jiného odkazu repro.

1. Zadejte **příkaz\_set link repro=linkrepro** a nastavte proměnnou prostředí **repro propojení\_** na adresář, který jste vytvořili. Pokud je sestavení spuštěno z jiného adresáře, jak je tomu často u složitějších projektů, nastavte propojení **\_repro** na úplnou cestu k adresáři repro propojení.

1. Chcete-li vytvořit projekt repro v sadě Visual Studio, zadejte v okně konzoly příkazového řádku pro vývojáře příkaz **devenv**. Zajišťuje, že hodnota proměnné prostředí **repro propojení\_** je viditelná pro Visual Studio. Chcete-li vytvořit projekt na příkazovém řádku, použijte argumenty příkazového řádku zachycené výše k duplikaci sestavení repro.

1. Sestavte si reprodukci projektu a potvrďte, že došlo k očekávanému problému.

1. Zavřete Visual Studio, pokud jste jej použili k vytvoření.

1. V okně konzoly příkazového řádku pro vývojáře zadejte **odkaz\_sady příkazů repro=** chcete-li vymazat proměnnou prostředí **repro propojení.\_**

Nakonec zabalte reprodukci komprimací celého adresáře linkrepro do souboru ZIP nebo podobného souboru a připojte jej k sestavě.

Možnost **propojovacího zařízení /LINKREPRO** má stejný účinek jako proměnná prostředí **repro propojení.\_** Pomocí možnosti [/LINKREPROTARGET](../build/reference/linkreprotarget.md) můžete zadat název, který chcete filtrovat pro vygenerovaný odkaz repro. Chcete-li použít **/LINKREPROTARGET**, musíte také zadat možnost propojovacího systému **/OUT.**

#### <a name="to-generate-a-link-repro-using-the-linkrepro-option"></a>Generování repro propojení pomocí možnosti /LINKREPRO

1. Vytvořte adresář pro uložení repro odkazu. Úplnou cestu k adresáři, kterou vytvoříte, budeme označovat jako _cestu k adresáři_. Pokud obsahuje mezery, použijte kolem cesty dvojité uvozovky.

1. Přidejte příkaz **/LINKREPRO:**_adresář-cesta_ do příkazového řádku linkeru. V sadě Visual Studio otevřete dialogové okno **Stránky vlastností** pro váš projekt. Vyberte stránku vlastností**příkazového řádku** **propojovacího** > programu **Vlastnosti** > konfigurace. Potom zadejte **/LINKREPRO:**_adresář cesta_ možnost v další **možnosti** pole. Chcete-li uložit změny, zvolte **OK.**

1. Sestavte si reprodukci projektu a potvrďte, že došlo k očekávanému problému.

Nakonec zabalte reprodukci komprimací celého adresáře repro propojení _adresáře_ do souboru ZIP nebo podobného souboru a připojte jej k sestavě.

### <a name="other-repros"></a>Další reprosy

Pokud nemůžete snížit problém na jeden zdrojový soubor nebo předzpracované repro a problém nevyžaduje reprodukci odkazu, můžeme prozkoumat projekt IDE. Všechny pokyny, jak vytvořit dobrý repro stále platí: Kód by měl být minimální a soběstačný. Problém by měl nastat v našich nejnovějších nástrojů a pokud je to relevantní, by neměly být vidět v jiných kompilátorů.

Vytvořte reprodukci jako minimální projekt IDE a pak jej zabalte komprimací celé adresářové struktury do souboru ZIP nebo podobného souboru a připojte jej k sestavě.

## <a name="ways-to-send-your-report"></a>Způsoby odeslání sestavy

Máte pár dobrých způsobů, jak nám podat zprávu. Můžete použít visual studio je předdefinovaný [nástroj report a problem tool](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)nebo Visual Studio Developer [Community](https://developercommunity.visualstudio.com/) stránky. V dolní části této stránky je také tlačítko **pro zpětnou vazbu produktu.** Volba závisí na tom, zda chcete použít integrované nástroje v integrovaném rozhraní IDE k zachycení snímků obrazovky a uspořádání sestavy. Pokud nechcete, můžete použít webové stránky komunity vývojářů přímo.

> [!NOTE]
> Bez ohledu na to, jak odešlete zprávu, společnost Microsoft respektuje vaše soukromí. Společnost Microsoft se zavazuje dodržovat všechny zákony a předpisy týkající se ochrany osobních údajů. Informace o tom, jak nakládáme s údaji, které nám posíláte, naleznete v [Prohlášení společnosti Microsoft o zásadách ochrany osobních údajů](https://privacy.microsoft.com/privacystatement).

### <a name="use-the-report-a-problem-tool"></a>Použití nástroje Nahlásit problém

Nástroj **Nahlásit problém** v sadě Visual Studio je způsob, jak mohou uživatelé sady Visual Studio hlásit problémy pouhými několika kliknutími. Zobrazí se jednoduchý formulář pro odeslání podrobných informací o nalezeném problému. Potom můžete odeslat zprávu bez opuštění ide.

Nahlášení problému prostřednictvím nástroje **Nahlásit problém** je snadné a pohodlné z ide. Můžete k němu přistupovat z záhlaví výběrem ikony **Odeslat zpětnou vazbu** vedle vyhledávacího pole **Snadné spuštění.** Nebo ji najdete na řádku nabídek v **nápovědě** > **Odeslat zpětnou vazbu** > **Nahlásit problém**.

Pokud se rozhodnete problém nahlásit, nejprve vyhledejte podobné problémy v komunitě vývojářů. V případě, že váš problém byl hlášen dříve, přehlasujte zprávu a přidejte komentáře s dalšími podrobnostmi. Pokud podobný problém nevidíte, zvolte tlačítko **Nahlásit nový problém** v dolní části dialogového okna Zpětná vazba sady Visual Studio a podle pokynů nahlaste problém.

### <a name="use-the-visual-studio-developer-community-pages"></a>Použití stránek komunity pro vývojáře sady Visual Studio

Stránky Visual Studio Developer Community představují další pohodlný způsob, jak hlásit problémy a najít řešení pro Visual Studio a kompilátor, nástroje a knihovny Jazyka C++. Existují konkrétní stránky komunity pro vývojáře pro [Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html), Visual Studio [pro Mac](https://developercommunity.visualstudio.com/spaces/41/index.html), [.NET](https://developercommunity.visualstudio.com/spaces/61/index.html), [C++](https://developercommunity.visualstudio.com/spaces/62/index.html), [Azure DevOps Services](https://developercommunity.visualstudio.com/spaces/21/index.html)a [TFS](https://developercommunity.visualstudio.com/spaces/22/index.html).

Pod záložkami komunity, v horní části každé stránky, je vyhledávací pole. Můžete ji použít k vyhledání příspěvků, které nahlašují podobné problémy jako vy. Můžete najít řešení nebo jiné užitečné informace týkající se vašeho problému je již k dispozici. Pokud někdo nahlásil stejný problém dříve, pak upvote a komentovat tuto zprávu, spíše než vytvořit novou zprávu o problému. Chcete-li komentovat, hlasovat nebo nahlásit nový problém, můžete být požádáni o přihlášení k účtu sady Visual Studio. Při prvním přihlášení budete muset souhlasit s tím, že aplikaci Komunita vývojářů poskytnete přístup k vašemu profilu.

Pro problémy s kompilátorem Jazyka C++, propojovacím programem a dalšími nástroji a knihovnami použijte stránku [C++.](https://developercommunity.visualstudio.com/spaces/62/index.html) Pokud problém vyhledáte a nebyl nahlášen dříve, zvolte vedle vyhledávacího pole tlačítko **Nahlásit problém.** Můžete zahrnout svůj repro kód a příkazový řádek, snímky obrazovky, odkazy na související diskuse a další informace, které považujete za relevantní a užitečné.

> [!TIP]
> Pro jiné druhy problémů, které můžete najít v sadě Visual Studio, které nesouvisejí se sadou nástrojů C++ (například problémy s uzlem, přerušené funkce ide nebo obecné selhání), použijte nástroj **Nahlásit problém** v ide. To je nejlepší volba, vzhledem k jeho možnosti snímek obrazovky a jeho schopnost zaznamenávat akce ui, které vedou k problému, který jste našli. Tyto druhy chyb lze také vyhledat na webu [komunity vývojářů.](https://developercommunity.visualstudio.com/) Další informace naleznete v [tématu Jak nahlásit problém s visual studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).

### <a name="reports-and-privacy"></a>Zprávy a ochrana osobních údajů

**Všechny informace v sestavách a všechny komentáře a odpovědi jsou ve výchozím nastavení veřejně viditelné**. Za normálních okolností je to výhoda, protože umožňuje celé komunitě zobrazit problémy, řešení a řešení, která našli jiní uživatelé. Pokud se však obáváte zveřejnění vašich dat nebo identity z důvodu ochrany osobních údajů nebo duševního vlastnictví, máte možnosti.

Pokud máte obavy o odhalení své identity, [vytvořte si nový účet Microsoft,](https://signup.live.com/) který nezveřejňuje žádné podrobnosti o vás. Tento účet slouží k vytvoření sestavy.

**Neuvázejte do názvu nebo obsahu původní sestavy, která je veřejná, nic, co chcete zachovat jako soukromou.** Místo toho řekněte, že budete posílat podrobnosti soukromě v samostatném komentáři. Chcete-li se ujistit, že je sestava směrována správným lidem, zahrňte do seznamu témat u sestavy problémů **cppcompiler.** Po vytvoření zprávy o problému je nyní možné určit, kdo může zobrazit vaše odpovědi a přílohy.

#### <a name="to-create-a-problem-report-for-private-information"></a>Vytvoření sestavy problémů pro soukromé informace

1. V sestavě, kterou jste vytvořili, zvolte **Přidat komentář** a vytvořte si soukromý popis problému.

1. V editoru odpovědí použijte ovládací prvek rozevírací seznam pod tlačítky **Odeslat** a **Storno** a určete cílovou skupinu pro vaši odpověď. Tyto soukromé odpovědi a všechny obrázky, odkazy nebo kód, které do nich zahrnete, uvidí pouze lidé, které zadáte. Zvolte **Zobrazitelné moderátory a původní plakát,** abyste omezili viditelnost na zaměstnance microsoftu a na sebe.

1. Přidejte popis a další informace, obrázky a přílohy souborů potřebné pro reprodukci. Chcete-li tyto informace odeslat soukromě, zvolte tlačítko **Odeslat.**

   K dispozici je limit 2 GB na připojené soubory a maximálně 10 souborů. U všech větších nahrávek požádejte o adresu URL pro nahrání v soukromém komentáři.

Všechny odpovědi v rámci tohoto komentáře mají stejnou omezenou viditelnost, jakou jste zadali. Platí to i v případě, že ovládací prvek rozevíracího kódu u odpovědí nezobrazuje správně stav omezené viditelnosti.

Chcete-li zachovat soukromí a zachovat vaše citlivé informace mimo veřejné zobrazení, buďte opatrní. Udržujte veškerou interakci se společností Microsoft s odpověďmi pod omezeným komentářem. Odpovědi na jiné komentáře mohou způsobit náhodné zveřejnění citlivých informací.

## <a name="how-to-report-a-c-documentation-issue"></a>Jak nahlásit problém s dokumentací jazyka C++

Problémy s GitHubem používáme ke sledování problémů hlášených v naší dokumentaci. Teď můžete vytvářet problémy GitHubu přímo ze stránky obsahu, která vám umožní mnohem bohatší mašle se autory a produktovými týmy. Pokud se zobrazí problém s dokumentem, ukázka chybného kódu, matoucí vysvětlení, kritické opomenutí nebo dokonce jen překlep, můžete nám snadno dát vědět. Přejděte do dolní části stránky a vyberte **Přihlásit se a sdělit nám zpětnou vazbu k dokumentaci**. Budete si muset vytvořit účet GitHub, pokud ho ještě nemáte. Když máte účet GitHub, můžete vidět všechny naše problémy s dokumentací a jejich stav. Také dostanete oznámení, když jsou provedeny změny pro problém, který jste nahlásili. Další informace naleznete [v tématu Nový systém zpětné vazby se blíží k docs.microsoft.com](/teamblog/a-new-feedback-system-is-coming-to-docs).

Při použití tlačítka zpětné vazby dokumentace vytvoříte na GitHubu problém s dokumentací. Problém je automaticky vyplněn některými informacemi o stránce, na které jste problém vytvořili. Tak víme, kde se problém nachází, takže tyto informace neupravujte. Stačí připojit podrobnosti o tom, co je špatně, a pokud chcete, navrhovanou opravu. [Naše C++ dokumenty jsou open source](https://github.com/MicrosoftDocs/cpp-docs/), takže pokud byste chtěli odeslat opravu sami, můžete. Další informace o tom, jak můžete přispět do naší dokumentace, najdete v našem [průvodci přispíváním](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md) na GitHubu.
