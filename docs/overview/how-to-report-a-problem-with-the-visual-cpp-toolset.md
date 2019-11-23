---
title: Nahlášení problému pomocí sady nástrojů Microsoftu C++
description: Jak vytvořit sestavu dobrého problému a reprodukci informace pro sadu nástrojů Microsoftu C++
ms.date: 09/24/2019
ms.technology: cpp-ide
author: corob-msft
ms.author: corob
ms.openlocfilehash: 350e902501aca5cbe2b4022ec1f977719844644b
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685705"
---
# <a name="how-to-report-a-problem-with-the-microsoft-c-toolset-or-documentation"></a>Nahlášení problému pomocí sady nástrojů nebo dokumentace C++ Microsoftu

Pokud najdete problémy v kompilátoru Microsoft C++ (MSVC), linkeru nebo jiných nástrojích a knihovnách, chceme o nich znát. Pokud je problém v naší dokumentaci, chceme o tom také ví.

## <a name="how-to-report-a-c-toolset-issue"></a>Jak ohlásit problém sady C++ nástrojů

Nejlepším způsobem, jak nám sdělit informace o problému, je poslat nám zprávu, která obsahuje popis problému, který jste zjistili. Měl by obsahovat všechny podrobnosti o tom, jak sestavíte program. A měl by obsahovat *reprodukci*, kompletní testovací případ, který můžeme použít k reprodukování problému na našich vlastních počítačích. Tyto informace nám umožní rychle ověřit, že problém existuje v našem kódu a není místní pro vaše prostředí. Pomáhá nám určit, jestli má vliv na jiné verze kompilátoru, a diagnostikovat jeho příčinu.

V následujících částech najdete informace o tom, co je dobré v sestavě. Popisujeme, jak vygenerovat reprodukci pro druh problému, který jste našli, a jak odeslat sestavu do produktového týmu. Vaše sestavy jsou důležité pro nás a další vývojáře, jako jste vy. Děkujeme, že nám pomáháte C++vylepšit Microsoft!

## <a name="how-to-prepare-your-report"></a>Příprava sestavy

Je důležité vytvořit vysoce kvalitní zprávu, protože pro nás je obtížné reprodukování problému, který jste našli, bez úplných informací. Lepší je vaše sestava, což je efektivnější, abychom mohli problém znovu vytvořit a diagnostikovat.

Zpráva by měla obsahovat minimálně:

- Úplné informace o verzi sady nástrojů, kterou používáte.

- Úplný příkazový řádek CL. exe použitý k sestavení kódu.

- Podrobný popis problému, který jste zjistili.

- Reprodukci: úplný, zjednodušený, samostatně obsažený příklad zdrojového kódu, který demonstruje problém.

Přečtěte si další informace o konkrétních informacích, které potřebujeme a kde si je můžete najít, a o tom, jak vytvořit dobrý reprodukci.

### <a name="the-toolset-version"></a>Verze sady nástrojů

Potřebujeme úplné informace o verzi a cílovou architekturu sady nástrojů, která tento problém způsobuje. To je proto, abychom mohli reprodukci testovat na stejné sadě nástrojů na našich počítačích. Pokud můžeme reprodukování problému, tyto informace nám také poskytují výchozí bod pro zjištění, které další verze sady nástrojů mají stejný problém.

#### <a name="to-report-the-full-version-of-your-compiler"></a>Nahlášení plné verze kompilátoru

1. Otevřete **Developer Command Prompt** , který odpovídá verzi sady Visual Studio a architektuře konfigurace použité k sestavení projektu. Například Pokud sestavíte pomocí sady Visual Studio 2017 na platformě x64 pro cíle x64, vyberte **x64 Native Tools Command Prompt pro VS 2017**. Další informace najdete v tématu [zástupce příkazového řádku pro vývojáře](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts).

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **CL/BV**.

Výstup by měl vypadat nějak takto:

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

Zkopírujte celý výstup do sestavy a vložte ho.

### <a name="the-command-line"></a>Příkazový řádek

Potřebujeme přes příkazový řádek, CL. exe a všechny jeho argumenty, které se používají k sestavení kódu. To je proto, že je můžeme sestavit přesně stejným způsobem na počítačích. Je důležité, protože problém, který jste našli, může existovat jenom při sestavování s určitým argumentem nebo kombinací argumentů.

Nejlepším místem, kde najdete tyto informace, je protokol buildu hned poté, co se setkáte s problémem. Zajišťuje, že příkazový řádek obsahuje přesně stejné argumenty, které by mohly přispět k problému.

#### <a name="to-report-the-contents-of-the-command-line"></a>Nahlášení obsahu příkazového řádku

1. Vyhledejte soubor **CL. Command. 1. tlog** a otevřete ho. Ve výchozím nastavení je tento soubor umístěný ve složce Dokumenty v \\\\projektech sady Visual Studio\\pro *řešení*\\*ProjectName*\\*Konfigurace*\\*ProjectName*. tlog\\CL. Command. 1. tlog nebo ve složce uživatele v části \\source\\*úložiště\\* . tlog\\CL. Command. 1. tlog.\\\\\\ Může být v jiném umístění, pokud používáte jiný systém sestavení, nebo pokud jste změnili výchozí umístění projektu.

   V tomto souboru najdete názvy souborů zdrojového kódu následovaný argumenty příkazového řádku, které se používají pro jejich zkompilování, a to každou na samostatné řádky.

1. Vyhledejte řádek, který obsahuje název souboru se zdrojovým kódem, ve kterém k problému dochází. Řádek pod ním obsahuje odpovídající argumenty příkazu CL. exe.

Zkopírujte a vložte celý příkazový řádek do sestavy.

### <a name="a-description-of-the-problem"></a>Popis problému

Potřebujeme podrobný popis problému, který jste našli. To vám umožní ověřit, že se na našem počítači zobrazuje stejný efekt. V některých případech je to také užitečné, abychom věděli, co jste se snažili dosáhnout, a co byste měli k tomu očekávat.

Dobrý popis poskytuje **přesné chybové zprávy** , které jsou uvedeny v sadě nástrojů, nebo přesné chování za běhu, které vidíte. Tyto informace potřebujeme, abychom ověřili, že problém jsme reprodukovali správně. Zahrnout **všechny** výstupy kompilátoru, nikoli jenom poslední chybovou zprávu. Musíme Zobrazit vše, co vedlo k problému, který jste nahlásili. Pokud můžete problém duplikovat pomocí kompilátoru příkazového řádku, je preferovaný výstup kompilátoru. Rozhraní IDE a jiné systémy sestavení mohou filtrovat chybové zprávy, které vidíte, nebo zachytit pouze první řádek chybové zprávy.

Pokud je problém, že kompilátor přijímá neplatný kód a negeneruje diagnostiku, zahrňte ho do sestavy.

Chcete-li ohlásit problém s chováním za běhu, zahrňte **přesnou kopii** toho, co program vytiskne a co očekáváte. V ideálním případě jej vložíte do samotného příkazu OUTPUT, například `printf("This should be 5: %d\n", actual_result);`. Pokud dojde k chybě nebo zablokování programu, je třeba uvést také.

Přidejte další podrobnosti, které vám můžou pomáhat s diagnostikou zjištěného problému, jako je například jakákoli práce, kterou jste si vyzkoušeli. Zkuste neopakovat informace, které se nacházejí jinde v sestavě.

### <a name="the-repro"></a>Reprodukci

*Reprodukci* je úplný, samostatně zahrnutý příklad zdrojového kódu. Reproducibly ukazuje problém, který jste nalezli, a proto název. Potřebujeme reprodukci, abychom mohli reprodukování chyby na počítačích. Kód by měl být dostačující pro vytvoření základního spustitelného souboru, který se zkompiluje a spustí. Nebo, který se zkompiluje a spustí, pokud není pro problém *, který jste* našli. Reprodukci není fragment kódu. Měl by mít kompletní funkce a třídy a musí obsahovat všechny nezbytné direktivy #include, a to i pro standardní hlavičky.

#### <a name="what-makes-a-good-repro"></a>Co je dobré reprodukci

Dobrý reprodukci je:

- **Poskytuje.** Reprofesionály by měly být co nejmenší, ale pořád předvádí přesně zjištěné potíže. V případě potřeby nemusíte mít složité ani reálné. Potřebují pouze zobrazit kód, který odpovídá standardu nebo dokumentované implementaci kompilátoru. Pro chybějící diagnostiku by měl váš reprodukci zobrazovat kód, který není vyhovující. Jednoduché pro profesionály, které obsahují dostatečný kód k předvedení problému, je nejlepší. Pokud můžete kód odstranit nebo zjednodušit a ponechat si ho v souladu s tím, že se problém nezměnil, udělejte to. Nemusíte vkládat čítače s příklady kódu, který funguje.

- **Samostatně obsažený.** Respecialisté by se měli vyhnout zbytečným závislostem. Pokud můžete reprodukování problému bez knihoven třetích stran, udělejte to. Pokud můžete problém reprodukován bez jakéhokoli kódu knihovny kromě jednoduchých výstupních příkazů (například `puts("this shouldn't compile");`, `std::cout << value;`a `printf("%d\n", value);`), pak to udělejte. Je ideální, pokud může být příklad zhuštěný pouze do jednoho souboru zdrojového kódu bez odkazů na záhlaví uživatele. Snížení množství kódu, který je třeba vzít v úvahu, protože je možné, že je možný Přispěvatel k problému, je mimořádně užitečné pro nás.

- **Na nejnovější verzi kompilátoru.** Pokud je to možné, měli byste použít nejnovější aktualizaci na nejnovější verzi sady nástrojů. Nebo použijte nejnovější předprodejní verzi další aktualizace nebo další hlavní verzi. Problémy, které můžete najít ve starších verzích sady nástrojů, se často opravily v novějších verzích. Opravy jsou pro starší verze ve výjimečných případech nepřenosné.

- V případě potřeby **zaškrtněte u ostatních kompilátorů** . Pokud je to možné, C++ měly by se přesměrovat i pro profesionály, které zahrnují přenos přes jiný kompilátor. C++ Standard nakonec určuje správnost programu a žádný kompilátor není ideální. Pokud však Clang a RSZ přijměte váš kód bez diagnostiky a MSVC ne, pravděpodobně jste v našem kompilátoru zjistili chybu. (Další možnosti zahrnují rozdíly v chování systému UNIX a Windows nebo různé úrovně implementace C++ standardů atd.) Když všechny kompilátory odmítnou váš kód, je pravděpodobnější, že váš kód není správný. Zobrazení různých chybových zpráv vám může pomáhat s diagnostikou problému sami.

   Můžete najít seznamy online kompilátorů k otestování kódu proti v [online C++ kompilátorech](https://isocpp.org/blog/2013/01/online-c-compilers) na webu ISO C++ nebo tento [seznam online C++ kompilátorů](https://arnemertz.github.io/online-compilers/) na GitHubu. Mezi konkrétní příklady patří [Wandbox](https://wandbox.org/), [Průzkumník kompilátoru](https://godbolt.org/)a [Coliru](https://coliru.stacked-crooked.com/).

   > [!NOTE]
   > Online weby kompilátoru nejsou přidružené k Microsoftu. Mnoho online webů kompilátoru je spuštěno jako osobní projekty. Některé z těchto webů můžou být při čtení nedostupné, ale hledání by mělo najít jiné, co můžete použít.

Problémy v kompilátoru, linkeru a v knihovnách se obvykle zobrazují v konkrétním ohledu. Typ problému, který vyhledáte, určí, jaký druh reprodukci byste měli zahrnout do sestavy. Bez vhodného reprodukci nemusíme nic prozkoumat. Tady je několik druhů problémů, které se mohou zobrazit. Obsahujeme pokyny, jak vygenerovat druh reprodukci, který byste měli použít k nahlášení každého druhu problému.

#### <a name="frontend-parser-crash"></a>Došlo k chybě front-endu (analyzátor)

Během fáze analýzy kompilátoru dojde k selhání front-endu. Kompilátor obvykle generuje [závažnou chybu C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md)a odkazuje na soubor zdrojového kódu a číslo řádku, na kterém došlo k chybě. Často zmiňuje soubor s názvem msc1. cpp, ale tento detail můžete ignorovat.

Pro tento typ havárie poskytněte [předzpracovaný reprodukci](#preprocessed-repros).

Tady je příklad výstupu kompilátoru pro tento druh havárie:

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

Během fáze generování kódu kompilátoru dojde k selhání back-endu. Kompilátor obvykle generuje [závažnou chybu C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md)a nemusí odkazovat na soubor zdrojového kódu a číslo řádku přidružené k problému. Často zmiňuje soubor kompilátor\\UTC\\src\\P2\\Main. c, ale tento detail můžete ignorovat.

Pro tento typ havárie zadejte [odkaz reprodukci](#link-repros) , pokud používáte generování kódu při propojování (LTCG), který je povolen argumentem příkazového řádku **/GL** pro CL. exe. Pokud ne, místo toho zadejte [předzpracovaný reprodukci](#preprocessed-repros) .

Tady je příklad výstupu kompilátoru pro selhání back-endu, ve kterém se LTCG nepoužívá. Pokud váš výstup kompilátoru vypadá jako následující, měli byste poskytnout [předzpracovaný reprodukci](#preprocessed-repros).

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

Pokud se řádek, který začíná s **interní chybou kompilátoru** , zmiňuje. exe, spíše než CL. exe, je povolený LTCG. V tomto případě zadejte [odkaz reprodukci](#link-repros) . Pokud není jasné, zda byl LTCG povolen z chybové zprávy kompilátoru, Projděte si argumenty příkazového řádku. Zkopírovali jste je z protokolu sestavení v předchozím kroku pro argument příkazového řádku **/GL** .

#### <a name="linker-crash"></a>Chyba linkeru

Během fáze propojení dojde k selhání linkeru po spuštění kompilátoru. Obvykle linker generuje [chybu linkerů LNK1000 nástrojů linkeru](../error-messages/tool-errors/linker-tools-error-lnk1000.md).

> [!NOTE]
> Pokud výstup zmiňuje C1001 nebo zahrnuje generování kódu při propojování, uveďte místo toho [chybu back-endu (generování kódu)](#backend-code-generation-crash) .

Pro tento druh havárie zadejte [odkaz reprodukci](#link-repros).

Tady je příklad výstupu kompilátoru pro tento druh havárie:

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

Pokud je povoleno přírůstkové propojování a dojde k selhání pouze po úspěšném počátečním propojení, tedy pouze po prvním úplném odkazu, na kterém je založen pozdější přírůstkový odkaz, poskytuje také kopii objektu (obj) a knihovny (. lib), které odpovídají zdroji. soubory upravené po dokončení počátečního propojení.

#### <a name="bad-code-generation"></a>Chybné generování kódu

Chybné generování kódu je zřídka. K tomu dochází, když kompilátor omylem generuje nesprávný kód, který způsobí, že dojde k chybě vaší aplikace za běhu. Místo toho by měl generovat správný kód nebo zjistit problém v době kompilace. Pokud se domníváte, že problém, který jste nalezli, způsobuje chybné generování kódu, považovat sestavu za [chybu back-endu (generování kódu)](#backend-code-generation-crash).

Pro tento typ havárie zadejte [odkaz reprodukci](#link-repros) , pokud používáte argument příkazového řádku **/GL** pro CL. exe. Poskytněte [předzpracovaný reprodukci](#preprocessed-repros) , pokud ne.

## <a name="how-to-generate-a-repro"></a>Jak vygenerovat reprodukci

Abychom vám pomohli sledovat zdroj problému, je [dobrý reprodukci](#what-makes-a-good-repro) důležitý. Předtím, než provedete některý z kroků uvedených níže pro konkrétní druhy respecialistů, se pokuste použít zhuštění kódu, který demonstruje problém co nejvíce. Zkuste eliminovat nebo minimalizovat závislosti, požadované hlavičky a knihovny. Omezte možnosti kompilátoru a použité Definice preprocesoru, pokud je to možné.

Níže jsou uvedeny pokyny pro generování různých druhů respecialistů, které použijete k hlášení různých druhů problémů.

### <a name="preprocessed-repros"></a>Předzpracované předané profesionály

*Předzpracovaný reprodukci* je jeden zdrojový soubor, který demonstruje problém. Vygeneruje se z výstupu preprocesoru jazyka C. Chcete-li vytvořit jednu, použijte možnost kompilátoru **/p** v původním zdrojovém souboru reprodukci. Tato možnost zařadí zahrnuté hlavičky pro odebrání závislostí na dalších zdrojovém souboru a hlavičkových souborech. Tato možnost také řeší makra, #ifdef podmíněné hodnoty a další příkazy preprocesoru, které by mohly být závislé na vašem místním prostředí.

> [!NOTE]
> Předem zpracovávané postupy pro problémy, které by mohly být výsledkem chyb v naší implementaci standardní knihovny, nejsou tak užitečné, protože je často potřeba nahradit naše nejnovější, průběžnou implementací, abyste zjistili, jestli jsme problém vyřešili. V takovém případě neprovádějte předzpracování reprodukci a pokud nemůžete snížit problém do jediného zdrojového souboru, zabalit kód do souboru. zip nebo podobný nebo zvažte použití projektu IDE reprodukci. Další informace najdete v tématu [Další specialisty](#other-repros).

#### <a name="to-preprocess-a-source-code-file"></a>Postup předběžného zpracování souboru zdrojového kódu

1. Zachyťte argumenty příkazového řádku, které se používají k sestavení reprodukci, jak je popsáno v tématu [k nahlášení obsahu příkazového řádku](#to-report-the-contents-of-the-command-line).

1. Otevřete **Developer Command Prompt** , který odpovídá verzi sady Visual Studio a architektuře konfigurace použité k sestavení projektu.

1. Přejděte do adresáře, který obsahuje váš projekt reprodukci.

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **CL/p** *argumenty* *filename. cpp*. Pro *argumenty*použijte seznam argumentů, které jste si poznamenali výše. *filename. cpp* je název zdrojového souboru reprodukci. Tento příkaz provede replikaci příkazového řádku, který jste použili pro reprodukci, ale zastaví kompilaci po průchodu preprocesoru. Pak zapíše předzpracovaný zdrojový kód do *souboru filename. i*.

Pokud předzpracováváte soubor zdrojového kódu C++/CX nebo používáte funkci C++ modulů, je nutné provést některé další kroky. Další informace najdete v následujících částech.

Po vygenerování předzpracovaného souboru je vhodné zajistit, aby při kompilování předzpracovaného souboru byly problémy i nadále profesionálované.

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>Chcete-li potvrdit, že předzpracovaný soubor stále zpracovává chybu

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **CL** *argumenty* **/TP** *název_souboru. i* řekněte CL. exe, aby se soubor předzpracovaného souboru zkompiluje jako C++ zdrojový soubor. *Argumenty* jsou stejné jako výše zachycené argumenty, ale byly odebrány všechny argumenty **/d** a **/i** . To je proto, že již byly zahrnuty do předzpracovaného souboru. *filename. i* je název předzpracovaného souboru.

1. Potvrďte, že je problém reprodukován.

Nakonec připojte předzpracovaný *soubor reprodukci filename*. i k sestavě.

### <a name="preprocessed-ccx-winrtuwp-code-repros"></a>Předzpracované předané kódy pro platformu C++/CX WINRT/UWP

Pokud používáte C++/CX k sestavení spustitelného souboru, je nutné provést několik kroků navíc potřebných k vytvoření a ověření předzpracovaného reprodukci.

#### <a name="to-preprocess-ccx-source-code"></a>Pro předzpracování C++zdrojového kódu/CX

1. Vytvořte předzpracovaný zdrojový soubor, jak je popsáno v tématu [k předzpracování souboru zdrojového kódu](#to-preprocess-a-source-code-file).

1. Vyhledejte ve vygenerovaném souboru _filename_. i soubor pro direktivy **#using** .

1. Vytvořte seznam všech odkazovaných souborů. Ponechte všechny soubory Windows\*. winmd, soubory Platform. winmd a mscorlib. dll.

Příprava na ověření, že předzpracovaný soubor stále reprodukuje problém,

1. Vytvořte nový adresář pro předzpracovaný soubor a zkopírujte ho do nového adresáře.

1. Zkopírujte soubory. winmd ze seznamu **#using** do nového adresáře.

1. V novém adresáři vytvořte prázdný soubor vccorlib. h.

1. Úpravou předzpracovaného souboru odeberte všechny direktivy **#using** pro knihovnu mscorlib. dll.

1. Upravte soubor předzpracovaného tak, aby se změnily všechny absolutní cesty pouze na úplné názvy souborů pro zkopírované soubory. winmd.

Potvrďte, že předzpracovaný soubor stále reprodukuje problém, jak je uvedeno výše.

### <a name="preprocessed-c-modules-repros"></a>Předané C++ moduly předběžného zpracování

Pokud používáte funkci modulů C++ kompilátoru, je nutné provést několik různých kroků k vytvoření a ověření předzpracovaného reprodukci.

#### <a name="to-preprocess-a-source-code-file-that-uses-a-module"></a>Postup předběžného zpracování souboru zdrojového kódu, který používá modul

1. Zachyťte argumenty příkazového řádku, které se používají k sestavení reprodukci, jak je popsáno v tématu [k nahlášení obsahu příkazového řádku](#to-report-the-contents-of-the-command-line).

1. Otevřete **Developer Command Prompt** , který odpovídá verzi sady Visual Studio a architektuře konfigurace použité k sestavení projektu.

1. Přejděte do adresáře, který obsahuje váš projekt reprodukci.

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **CL/p** *argumenty* *filename. cpp*. *Argumenty* jsou výše zachycené argumenty a *filename. cpp* je název zdrojového souboru, který modul spotřebovává.

1. Přejděte do adresáře, který obsahuje projekt reprodukci, který vytvořil rozhraní modulu (výstup. IFC).

1. Zachyťte argumenty příkazového řádku, které se používají k sestavení rozhraní modulu.

1. V okně konzoly příkazového řádku pro vývojáře zadejte příkaz **CL/p** *argumenty* *Module. IXX*. *Argumenty* jsou výše zachycené argumenty a *modul. IXX* je název souboru, který vytváří rozhraní modulu.

Po vygenerování předzpracovaných souborů je vhodné se ujistit, že problém přetrvává při použití předzpracovaného souboru.

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>Chcete-li potvrdit, že předzpracovaný soubor stále zpracovává chybu

1. V okně konzoly pro vývojáře přejděte zpět do adresáře, který obsahuje váš projekt reprodukci.

1. Zadáním příkazu **CL** *argumenty* **/TP** *název_souboru*. i výše můžete zkompilovat předzpracovaný soubor, jako by šlo o C++ zdrojový soubor.

1. Ověřte, zda je problém stále reprodukován předzpracovaným souborem.

Nakonec připojte předzpracované soubory reprodukci (*filename*. i a *Module*. i) spolu s výstupem. ifc do vaší sestavy.

### <a name="link-repros"></a>Odkazy na odborníky

*Odkaz reprodukci* je linkerem generovaným obsahem adresáře, který je zadaný buď pomocí **odkazu\_** proměnné prostředí reprodukci, nebo jako argument pro možnost linkeru [/LINKREPRO](../build/reference/linkrepro.md) . Obsahuje artefakty sestavení, které souhrnně ukazují problém, ke kterému dochází v době propojování. Mezi příklady patří selhání back-endu zahrnující generování kódu při propojování (LTCG) nebo chyba linkeru. Tyto artefakty sestavení jsou ty, které jsou potřeba jako vstup linkeru, takže je možné problém reprodukovat. Reprodukci propojení lze snadno vytvořit pomocí této proměnné prostředí. Umožňuje integrovanou možnost reprodukci generování linkeru.

#### <a name="to-generate-a-link-repro-using-the-link_repro-environment-variable"></a>Vygenerování propojení reprodukci pomocí proměnné prostředí link_repro

1. Zachyťte argumenty příkazového řádku, které se používají k sestavení reprodukci, jak je popsáno v tématu [k nahlášení obsahu příkazového řádku](#to-report-the-contents-of-the-command-line).

1. Otevřete **Developer Command Prompt** , který odpovídá verzi sady Visual Studio a architektuře konfigurace použité k sestavení projektu.

1. V okně konzoly příkazového řádku pro vývojáře přejděte do adresáře, který obsahuje váš projekt reprodukci.

1. Zadáním **mkdir linkrepro** vytvořte adresář s názvem *linkrepro* pro odkaz reprodukci. K zachycení jiného reprodukci propojení můžete použít jiný název.

1. Zadejte **odkaz sady příkazů\_reprodukci = linkrepro** pro nastavení proměnné prostředí **propojení\_reprodukci** na vytvořený adresář. Pokud je vaše sestavení spuštěno z jiného adresáře, stejně jako u složitějších projektů, pak nastavte **odkaz\_reprodukci** na úplnou cestu k adresáři reprodukci propojení.

1. Chcete-li vytvořit projekt reprodukci v aplikaci Visual Studio, zadejte v okně konzoly příkazového řádku pro vývojáře příkaz **devenv**. Zajišťuje, aby byla hodnota proměnné prostředí **link\_reprodukci** viditelná pro sadu Visual Studio. Chcete-li sestavit projekt na příkazovém řádku, použijte argumenty příkazového řádku zaznamenané výše pro duplikaci sestavení reprodukci.

1. Sestavte projekt reprodukci a potvrďte, že došlo k očekávanému problému.

1. Zavřete Visual Studio, pokud jste ho použili k sestavení.

1. V okně konzoly příkazového řádku pro vývojáře zadejte **odkaz sady příkazů\_reprodukci =** , který vymaže proměnnou prostředí **reprodukci propojení\_** .

Nakonec zabalit reprodukci komprimací celého adresáře linkrepro do souboru ZIP nebo podobným způsobem a připojit ho k sestavě.

Možnost linkeru **/LINKREPRO** má stejný účinek jako proměnná prostředí **Link\_reprodukci** . Pomocí možnosti [/LINKREPROTARGET](../build/reference/linkreprotarget.md) můžete zadat název, který se má filtrovat pro vygenerovaný reprodukci propojení. Chcete-li použít **/LINKREPROTARGET**, musíte také zadat možnost linkeru **/out** .

#### <a name="to-generate-a-link-repro-using-the-linkrepro-option"></a>Vygenerování propojení reprodukci pomocí možnosti/LINKREPRO

1. Vytvořte adresář pro uložení odkazu reprodukci. Odkazujeme na úplnou cestu k adresáři, kterou vytvoříte jako _adresářovou cestu_. Použijte dvojité uvozovky kolem cesty, pokud obsahuje mezery.

1. Přidejte příkaz **/LINKREPRO:** _Directory-Path_ do příkazového řádku linkeru. V aplikaci Visual Studio otevřete dialogové okno **stránky vlastností** projektu. Vyberte **Vlastnosti konfigurace** > stránka vlastností **příkazového řádku** > **linkeru** . Pak do pole **Další možnosti** zadejte možnost **/LINKREPRO:** _Directory-Path_ . Kliknutím na **tlačítko OK** uložte změny.

1. Sestavte projekt reprodukci a potvrďte, že došlo k očekávanému problému.

Nakonec zabalit reprodukci komprimací celého adresáře _– cesta_ reprodukci adresáře do souboru. zip nebo podobným způsobem a připojte ho k sestavě.

### <a name="other-repros"></a>Další specialisty

Pokud nemůžete tento problém snížit na jeden zdrojový soubor nebo předzpracovaný reprodukci a problém nevyžaduje reprodukci propojení, můžeme prozkoumat projekt IDE. Všechny pokyny, jak vytvořit dobrý reprodukci, jsou stále platné: kód by měl být minimální a samostatně obsažený. K tomuto problému by mělo dojít v našich nejnovějších nástrojích, a pokud je to důležité, neměli byste je vidět v ostatních kompilátorech.

Vytvořte reprodukci jako minimální projekt IDE a pak ho zabalite komprimací celé adresářové struktury do souboru. zip nebo podobným způsobem a připojte ho k sestavě.

## <a name="ways-to-send-your-report"></a>Způsoby, jak odeslat sestavu

Máte k dispozici několik dobrých způsobů, jak nám získat sestavu. Můžete použít [Nástroj pro nahlášení problému](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017), který je součástí sady Visual Studio, nebo stránky [komunity vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/) . V dolní části této stránky je také tlačítko pro **zpětnou vazbu k produktu** . Volba závisí na tom, jestli chcete použít integrované nástroje v integrovaném vývojovém prostředí k zachycení snímků obrazovky a uspořádání sestavy. Pokud nechcete, můžete přímo použít web komunity vývojářů.

> [!NOTE]
> Microsoft respektuje vaše osobní údaje, bez ohledu na to, jak sestavu odesíláte. Společnost Microsoft se zavazuje, že bude dodržovat všechny předpisy a předpisy pro ochranu osobních údajů. Informace o tom, jak se zachází s daty, která nám pošlete, najdete v tématu [prohlášení o zásadách ochrany osobních údajů společnosti Microsoft](https://privacy.microsoft.com/privacystatement).

### <a name="use-the-report-a-problem-tool"></a>Použití nástroje nahlásit problém

Nástroj **ohlásit problém** v aplikaci Visual Studio je způsob, jak můžou uživatelé sady Visual Studio nahlásit problémy s několika kliknutími. Pro odeslání podrobných informací o problému, který jste našli, se zobrazí jednoduchý formulář. Sestavu pak můžete odeslat, aniž byste museli opustit integrované vývojové prostředí.

Nahlášení problému prostřednictvím nástroje **ohlásit problém** je snadno a pohodlné z rozhraní IDE. K němu máte přístup z záhlaví výběrem ikony pro **odeslání zpětné vazby** vedle vyhledávacího pole snadné **spuštění** . Nebo ho můžete najít na řádku nabídek v **nápovědě** > **Odeslat názor** > **nahlásit problém**.

Pokud se rozhodnete nahlásit problém, nejprve vyhledejte podobné problémy komunitou vývojářů. V případě, že byl problém ohlášen dříve, prohlaste sestavu a přidejte komentáře s dalšími konkrétními specifickými. Pokud se podobný problém nezobrazuje, v dolní části dialogového okna pro zpětnou vazbu sady Visual Studio klikněte na tlačítko **ohlásit nový problém** a podle pokynů nahlaste svůj problém.

### <a name="use-the-visual-studio-developer-community-pages"></a>Použití stránek komunity vývojářů sady Visual Studio

Stránky komunity vývojářů sady Visual Studio představují další pohodlný způsob, jak ohlásit problémy a vyhledat řešení pro Visual Studio C++ a kompilátor, nástroje a knihovny. Pro [Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html), [Visual Studio pro Mac](https://developercommunity.visualstudio.com/spaces/41/index.html), [.NET](https://developercommunity.visualstudio.com/spaces/61/index.html), [C++](https://developercommunity.visualstudio.com/spaces/62/index.html), [Azure DevOps Services](https://developercommunity.visualstudio.com/spaces/21/index.html)a [TFS](https://developercommunity.visualstudio.com/spaces/22/index.html)jsou k dispozici konkrétní stránky komunity pro vývojáře.

Pod kartami komunity v horní části každé stránky je vyhledávací pole. Můžete ji použít k vyhledání příspěvků, které nahlásí problémy podobné vašemu. Můžete najít řešení nebo jiné užitečné informace, které se týkají vašeho problému, je již k dispozici. Pokud někdo nahlásil stejný problém dřív, potom v této sestavě znovu nahlaste a zakomentujte místo vytvoření nové sestavy problému. Pokud chcete komentovat, hlasovat nebo nahlásit nový problém, může se vám zobrazit výzva, abyste se přihlásili k účtu aplikace Visual Studio. Při prvním přihlášení budete muset souhlasit s tím, že aplikaci komunity vývojářů poskytne přístup k vašemu profilu.

Pro problémy s C++ kompilátorem, linkerem a dalšími nástroji a knihovnami použijte [C++](https://developercommunity.visualstudio.com/spaces/62/index.html) stránku. Pokud vyhledáte svůj problém a ještě nebyl ohlášen, klikněte na tlačítko **nahlásit problém** vedle vyhledávacího pole. Můžete zahrnout svůj kód reprodukci a příkazový řádek, snímky obrazovky, odkazy na související diskuze a další důležité informace, které považujete za užitečné.

> [!TIP]
> Pro jiné druhy problémů, které můžete najít v sadě Visual Studio, které se netýkají C++ sady nástrojů (například problémy uživatelského rozhraní, poškozené funkce IDE nebo obecné havárie), použijte nástroj **ohlásit problém** v integrovaném vývojovém prostředí (IDE). To je nejlepší volba, která je způsobená možnostmi snímku obrazovky a její možností zaznamenávat akce uživatelského rozhraní, které vedou k problému, který jste našli. Tyto druhy chyb lze také vyhledat na webu [komunity vývojářů](https://developercommunity.visualstudio.com/) . Další informace najdete v tématu [postup nahlášení problému se sadou Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).

### <a name="reports-and-privacy"></a>Sestavy a ochrana osobních údajů

**Všechny informace v sestavách a komentáře a odpovědi jsou ve výchozím nastavení veřejně viditelné**. Obvykle se jedná o výhodu, protože umožňuje celé komunitě zobrazit problémy, řešení a alternativní řešení nalezené ostatními uživateli. Pokud jste si ale jisti, že vaše data nebo identita jsou veřejné, z důvodů ochrany osobních údajů nebo duševního vlastnictví máte možnosti.

Pokud máte obavy o odhalení vaší identity, [vytvořte novou účet Microsoft](https://signup.live.com/) , která nezveřejňuje žádné podrobnosti. Pomocí tohoto účtu můžete vytvořit sestavu.

**Neumísťujte nic, co chcete zachovat soukromě v názvu nebo obsahu počáteční sestavy, která je veřejná.** Místo toho řekněme, že v samostatném komentáři odešlete podrobnosti soukromě. Abyste se ujistili, že je sestava směrována na správné lidi, přidejte do seznamu témat sestavy problému **cppcompiler** . Po vytvoření sestavy problému je teď možné určit, kdo může zobrazit vaše odpovědi a přílohy.

#### <a name="to-create-a-problem-report-for-private-information"></a>Vytvoření sestavy problému pro soukromé informace

1. V sestavě, kterou jste vytvořili, vyberte **Přidat komentář** a vytvořte tak soukromý popis problému.

1. V editoru odpovědí použijte ovládací prvek rozevíracího seznamu pod tlačítky **Odeslat** a **Storno** a určete cílovou skupinu pro vaši odpověď. Tyto soukromé odpovědi a všechny obrázky, odkazy nebo kód, které do nich zahrnete, můžou zobrazit jenom lidé, které zadáte. Vyberte **zobrazitelné moderátory a původní plakát** , abyste omezili přehlednost na zaměstnance Microsoftu a sami.

1. Přidejte popis a další informace, obrázky a přiložené soubory, které jsou potřeba pro reprodukci. Kliknutím na tlačítko **Odeslat** odešlete tyto informace soukromě.

   Pro připojené soubory existuje omezení na 2 GB a maximálně 10 souborů. V případě větších nahrávání si vyžádejte svůj privátní komentář k adrese URL pro odeslání.

Všechny odpovědi v rámci tohoto komentáře mají stejnou viditelnost, kterou jste zadali. Je true i v případě, že ovládací prvek DropDown na odpovědích nezobrazuje správně stav omezené viditelnosti.

Pokud chcete zachovat vaše osobní údaje a chránit vaše citlivé informace, buďte opatrní. Ponechte veškerou interakci s Microsoftem na odpovědi v rámci omezeného komentáře. Odpovědi na jiné komentáře mohou způsobit náhodné zveřejnění citlivých informací.

## <a name="how-to-report-a-c-documentation-issue"></a>Jak ohlásit problém s C++ dokumentací

K sledování problémů hlášených v naší dokumentaci využíváme problémy GitHubu. Problémy s GitHubem teď můžete vytvářet přímo na stránce obsahu, což vám umožní pracovat s moduly pro vytváření a produktovým týmem mnohem bohatším způsobem. Pokud se vám zobrazí problém s dokumentem, chybnou ukázkou kódu, nenáročné vysvětlení, kritická vynechání nebo dokonce jenom překlep, můžete nám snadno sdělit. Posuňte se do dolní části stránky a vyberte možnost **Přihlásit se a sdělte nám svůj názor na dokumentaci**. Pokud ještě nemáte účet GitHub, budete ho muset vytvořit. Pokud máte účet GitHubu, uvidíte všechny problémy s dokumentací a jejich stav. Zobrazí se také oznámení o změnách zaznamenaného problému. Další informace najdete v tématu [Nový systém zpětné vazby přichází do docs.Microsoft.com](/teamblog/a-new-feedback-system-is-coming-to-docs).

Když použijete tlačítko pro odeslání názoru k dokumentaci, vytvoříte problém dokumentace na GitHubu. Problém se automaticky vyplní informacemi o stránce, na které jste tento problém vytvořili. To znamená, jak ví, kde se problém nachází, proto tyto informace neupravujte. Stačí připojit podrobnosti o tom, co je špatně, a pokud chcete, navrhovanou opravu. [Naše C++ dokumenty jsou Open Source](https://github.com/MicrosoftDocs/cpp-docs/), takže pokud chcete opravu odeslat sami, můžete. Další informace o tom, jak můžete přispívat k naší dokumentaci, najdete v [Průvodci přispívajícím](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md) na GitHubu.
