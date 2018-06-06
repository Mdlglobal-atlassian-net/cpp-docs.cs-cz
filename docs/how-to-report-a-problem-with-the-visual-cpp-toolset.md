---
title: Postup nahlásit problém s sady nástrojů Visual C++ | Microsoft Docs
ms.date: 5/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0044a0da7b1ac4ad052eb120ccfb1f7425d2c0e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34336335"
---
# <a name="how-to-report-a-problem-with-the-visual-c-toolset-or-documentation"></a>Jak vytvářet sestavu o problém s Visual C++ nástrojů nebo dokumentace

Pokud narazíte na potíže s Microsoft Visual C++ compiler, linkeru, nebo jiných nástrojů a knihovny, chceme vědět o nich. Pokud se potíže v naší dokumentaci, chceme, příliš seznámit.

## <a name="how-to-report-a-c-toolset-issue"></a>Jak vytvářet sestavu problémem nástrojů C++

Nejlepší způsob a dejte nám vědět o problému, je pošlete nám sestavu, která obsahuje popis problému byla zjištěna, podrobnosti o jak sestavujete vašeho programu a *zkopírujte*, můžeme použít pro reprodukci dokončení testovacího případu problém na vlastní počítače. Tyto informace umožňují nám rychle ověřte, zda problém existuje v našem kódu a není místní pro vaše prostředí a zjistit, zda ovlivňuje jiných verzích kompilátor a diagnostikovat jeho příčinu.

V následujících částech vám přečíst si o díky užitečnou sestavu, jak vygenerovat zkopírujte pro druh problém, který jste si našli a odesílat sestavy produktový tým. Sestavy jsou důležité pro nás a ostatní vývojáři mohou. Děkujeme vám za pomoc při vylepšení Visual C++.

## <a name="how-to-prepare-your-report"></a>Postup přípravy sestavy

Vytváření vysoce kvalitní sestavy je důležité, protože je velmi obtížné reprodukci problému, který jste se setkali na vlastní počítače bez úplné informace. Tím lepší je sestavy, čím efektivně jsme se může znovu vytvořte a diagnostikovat problém.

Minimálně musí obsahovat sestavy

- Úplné informací o verzi sady nástrojů, které používáte.

- Úplné cl.exe příkazovým řádkem použitým k vytvoření vašeho kódu.

- Podrobný popis problému, který jste se setkali.

- Zkopírujte: Příklad dokončení, zjednodušené, úplný a samostatný zdrojového kódu, který ukazuje problém.

Přečtěte si další informace o konkrétní informace potřebujeme a kde můžete najít a postup vytvoření dobrý zkopírujte.

### <a name="the-toolset-version"></a>Sada nástrojů verze

Potřebujeme informace plnou verzi a architekturu cílové sady nástrojů, který způsobuje, že problém, jsme mohli otestovat vaši zkopírujte proti stejné sady nástrojů na našem počítače. Pokud jsme lze problém reprodukovat, tyto informace nám také poskytuje výchozí bod pro zkoumání jaké další verze sady nástrojů vykazuje stejný problém.

#### <a name="to-report-the-full-version-of-the-compiler-youre-using"></a>K sestavě na plnou verzi, kterou používáte kompilátoru

1. Otevřete **příkazový řádek vývojáře** odpovídající verze a konfigurace architektura sady Visual Studio používanou pro sestavení projektu. Například pokud vytvoříte pomocí Visual Studio 2017 na x64 pro x64 cíle, zvolte **x64 nativní nástroje příkazového řádku pro VS 2017**. Další informace najdete v tématu [zástupce příkazového řádku vývojáře](build/building-on-the-command-line.md#developer-command-prompt-shortcuts).

1. V okně konzoly vývojáře příkazového řádku zadejte příkaz **cl /Bv**.

Výstup by měl vypadat podobně jako tento:

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

Zkopírujte a vložte na celou výstupu do sestavy.

### <a name="the-command-line"></a>Příkazový řádek

Potřebujeme přesný příkazového řádku (cl.exe a všechny její argumenty) sloužící k vytvoření kódu, takže jsme můžete vytvořit úplně stejně, jako na našem počítače. To je důležité, protože problému, který byla zjištěna může existovat pouze při sestavení s argumentem nebo kombinace argumentů.

Nejlepší místo k najít tyto informace se v protokolu sestavení ihned po se problém. Tím se zajistí, že příkazový řádek obsahuje přesně stejné argumenty, které mohou způsobovat tento problém.

#### <a name="to-report-the-contents-of-the-command-line"></a>Tak, aby odesílaly obsah příkazového řádku

1. Vyhledejte **CL.command.1.tlog** souborů a otevřete ji. Ve výchozím nastavení, tento soubor je umístěný ve složce Dokumenty v \\Visual Studio *verze*\\projekty\\*název řešení SolutionName* \\ *ProjectName*\\*konfigurace*\\*ProjectName*.tlog\\CL.command.1.tlog, nebo ve složce uživatele v části \\Zdroj\\úložiště\\*název řešení SolutionName*\\*ProjectName*\\*konfigurace* \\ *ProjectName*.tlog\\CL.command.1.tlog. Pokud používáte jiné systém sestavení, nebo pokud jste změnili výchozí umístění pro svůj projekt může být v jiném umístění.

   Uvnitř tohoto souboru najdete v ní názvy soubory zdrojového kódu, za nímž následuje argumenty příkazového řádku používá ke kompilaci je každý na samostatné řádky.

1. Vyhledejte řádek, který obsahuje název souboru zdrojového kódu, kde k problému dochází; na řádku pod ním obsahuje odpovídající cl.exe argumenty příkazu.

Zkopírujte a vložte celý příkazového řádku do sestavy.

### <a name="a-description-of-the-problem"></a>Popis problému

Potřebujeme podrobný popis problému, který jste došlo tak, aby bylo možné ověřit, že vidíte stejného efektu na našem počítačích; jeho také někdy užitečné pro nám vědět, co jste se pokoušeli provést a co jste očekávali.

Zadejte prosím **přesnou chybové zprávy** poskytují sadu nástrojů nebo přesnou modul runtime chování zobrazí. Potřebujeme tyto informace k ověření, že jsme jste správně reprodukovat problém. Uveďte **všechny** kompilátoru výstup, nikoli pouze poslední chybová zpráva. Musíme vidět všechny objekty, které vedly k problému, které ohlásíte. Pokud tento problém můžete duplikovat pomocí příkazového řádku kompilátoru, je tento výstup kompilátoru upřednostňované; prostředí IDE a dalšími systémy sestavení může filtrovat chybové zprávy, které najdete v článku, nebo jenom zaznamenat první řádek chybovou zprávu.

Pokud tento problém je, že kompilátor přijme neplatný kód a negeneruje Diagnostika, je potřeba počítat to v sestavě.

Chcete-li nahlásit problém chování za běhu, zahrňte **přesnou kopie** program vytiskne a co byste měli vidět. V ideálním případě by tato vložené v výstup příkazu samostatně, například `printf("This should be 5: %d\n", actual_result);`. Pokud dojde k chybě programu, nebo přestane reagovat, zmínili, také.

Přidáte další podrobnosti, které nám mohou pomoci diagnostikovat problém, který se vyskytl, například všechny postupy, které může našli. Vyhněte se opakují. informace o nacházejí jinde v sestavě.

### <a name="the-repro"></a>Postup

Zkopírujte je příklad dokončení, úplný a samostatný zdrojového kódu, který reprodukovaně ukazuje jste zaznamenaném problému (proto název). Potřebujeme zkopírujte tak, aby jsme chybu reprodukovat na našem počítače. Kód by mělo být dostatečné samostatně k vytvoření jednoduché spustitelný soubor, který se zkompiluje a spouští nebo které by zkompilování a spuštění v opačném případě pro problém, který jste si našli. Zkopírujte není fragmentu kódu; měl by mít dokončení funkce a třídy a obsahují všechny nezbytné # direktivy i pro hlavičky standardních include.

#### <a name="what-makes-a-good-repro"></a>Čím je dobré zkopírujte

Je dobré postup:

- **Minimální.** Repros by měl být co nejmenší ještě stále ukazují přesně problému, který jste se setkali. Repros nemusí být komplexní nebo realistické; Stačí, když se zobrazí kód, který vyhovuje standardní nebo implementace zdokumentovaných kompilátoru nebo v případě chybějící diagnostiky, kód, který není vyhovující. Je jednoduché, k bodu repros, které obsahují přesně akorát kód k předvedení problém. Pokud můžete eliminovat nebo zjednodušit kód a zůstanou vyhovující a také ponechat beze změny problém, proveďte tuto operaci, tak. Nemusíte zahrnovat kontrolní příklady kódu, který funguje.

- **Úplný a samostatný.** Repros byste neměli nepotřebné závislosti. Pokud můžete reprodukujte problém bez knihovny třetích stran, prosím učiňte. Pokud jste reprodukování problému bez jakékoli kódu knihovna kromě jednoduché výstupní příkazy (například `puts("this shouldn't compile");`, `std::cout << value;`, a `printf("%d\n", value);` jsou v pořádku), proveďte tuto akci. Je ideální v příkladu můžete vyjádřit do souboru kódu jednoho zdroje, bez ohledu na všechny uživatele hlavičky. Snižuje množství kód, který se musí vzít v úvahu jako Přispěvatel možné tento problém je pro nás enormously užitečné.

- **Na nejnovější verzi kompilátoru.** Repros měli použít nejnovější aktualizace na nejnovější verzi sady nástrojů nebo nejnovější předprodejní verzi na další aktualizaci nebo další hlavní verzí, kdykoli je to možné. Velmi často bylo opraveno problémy, ke kterým může dojít v starší verze sady nástrojů v novější verzi. Opravy jsou přeneseny zpět ke starším verzím pouze ve výjimečných případech.

- **Kontrolovat další kompilátory** podle potřeby. Repros, které zahrnují přenosné C++ – kód by měl ověřit chování pro jiné kompilátory Pokud je to možné. Standardní konečném důsledku určuje správnost program a žádné kompilátoru je ideální, ale když Clang a RSZ přijmout kódu bez Diagnostika a MSVC neexistuje, je pravděpodobné, že zvažujete chybou v našem kompilátoru. (Další možnosti zahrnují rozdíly v chování systému Unix a Windows nebo různé úrovně implementace standardy C++ a tak dále.) Na druhé straně Pokud všechny kompilátory odmítnout kódu, je pravděpodobné, že váš kód je nesprávný. Zobrazuje různé chybové zprávy mohou pomoci problém diagnostikovat sami.

   Můžete najít seznam online kompilátory k testování kódu proti v [Online C++ kompilátory](https://isocpp.org/blog/2013/01/online-c-compilers) na webu ISO C++, nebo se kurátorované [seznamu z Online C++ kompilátory](https://arnemertz.github.io/online-compilers/) na Githubu. Mezi některé konkrétní příklady patří [Wandbox](https://wandbox.org/), [kompilátoru Explorer](https://godbolt.org/), a [Coliru](http://coliru.stacked-crooked.com/).

   > [!NOTE]
   > Online kompilátoru weby nejsou ve skupině se společností Microsoft. Mnohé weby online kompilátoru jsou spouštěny jako osobní projekty a některé z těchto lokalit nemusí být k dispozici, když si přečíst toto, ale hledání by měl zjistit ostatní, které můžete použít.

Problémy v kompilátoru, linkeru a v knihovnách, zpravidla sami zobrazit zejména způsoby. Druh problému, které zaznamenáte určí, jaký druh zkopírujte by měla obsahovat v sestavě. Bez odpovídající postup máme nic k prozkoumání. Tady jsou některé druhy problémů, které se může zobrazit a pokyny pro generování druhy repros, že měli byste použít k hlášení jednotlivé typy problémů.

#### <a name="frontend-parser-crash"></a>Havárie front-endu (Analyzátor)

Front-endu havárií dojde během analýzy fáze kompilátoru. Obvykle bude emitování kompilátor [závažná chyba C1001](error-messages/compiler-errors-1/fatal-error-c1001.md) a odkazovat na zdrojový kód souborové služby a řádku číslo na kterém se stala chyba; ho bude často zmínili msc1.cpp souboru, ale můžete ignorovat této jsou podrobně popsané.

Pro tento typ havárie, zadejte [zpracované zkopírujte](#preprocessed-repros).

Tady je příklad výstupu kompilátoru pro tento typ havárie:

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

#### <a name="backend-code-generation-crash"></a>Havárie back-end (vytváření kódu)

Back-end havárií, ke kterým došlo během kód generování fáze kompilátoru. Obvykle bude emitování kompilátor [závažná chyba C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)a nemusí odkazovat souboru se zdrojovým kódem a související s problémem, číslo řádku, ho bude často zmínili souboru kompilátoru\\utc\\src\\p2\\main.c, ale můžete ignorovat tuto podrobností.

Pro tento typ havárie, zadejte [zkopírujte odkaz](#link-repros) ve povolené Pokud používáte generování kódu v době propojování (LTCG), **/GL** argument příkazového řádku k cl.exe. Pokud ne, zadejte [zpracované zkopírujte](#preprocessed-repros) místo.

Tady je příklad výstupu kompilátoru pro back-end havárií, ve kterém LTCG nepoužívá. Pokud bude mít tento tvar výstupu kompilátoru by měl poskytovat [zpracované zkopírujte](#preprocessed-repros).

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

Pokud na řádku, který začíná řetězcem **vnitřní chyba KOMPILÁTORU** uvádí link.exe, nikoli cl.exe, LTCG byl povolen a měl by poskytnout [zkopírujte odkaz](#link-repros). Pokud jeho není jasné, zda LTCG byla povolena z kompilátoru chybovou zprávu, budete muset prozkoumat argumenty příkazového řádku, které jste zkopírovali z buildu protokolu v předchozím kroku pro **/GL** argument příkazového řádku.

#### <a name="linker-crash"></a>Havárie linkeru

Linkeru havárií, ke kterým došlo během fází propojení, po spuštění kompilátoru. Obvykle bude emitování linkeru [chyba Linkerů LNK1000](error-messages/tool-errors/linker-tools-error-lnk1000.md).

> [!NOTE]
> Pokud výstup uvádí C1001 nebo zahrnuje vytvoření kódu v době odkaz, podívejte se na [back-end (vytváření kódu) havárií](#backend-code-generation-crash) místo pro další informace.

Pro tento typ havárie, zadejte [zkopírujte odkaz](#link-repros).

Tady je příklad výstupu kompilátoru pro tento typ havárie.

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

Pokud je povolená přírůstkové propojování a až po úspěšném počáteční odkaz, došlo k havárii (tedy až po první úplné propojení na kterých je založena následné přírůstkové propojování) zadejte také kopie objektu (.obj) a soubory knihovny (LIB), které odpovídají zdrojové soubory, které byly upraveny po dokončení počáteční odkaz.

#### <a name="bad-code-generation"></a>Generování chybného kódu

Generování chybného kódu je taková situace vzácná, ale nastane, když kompilátor omylem generuje nesprávný kód, který způsobí, že vaše aplikace a havárií na modulu runtime, nikoli zjišťování potíže při kompilaci. Pokud si myslíte, problém se setkáváte s výsledky v generování chybného kódu, považovat za sestavy stejné [back-end (vytváření kódu) havárií](#backend-code-generation-crash).

Pro tento typ havárie zadejte [zkopírujte odkaz](#link-repros) ve povolené Pokud používáte generování kódu v době propojování (LTCG), **/GL** argument příkazového řádku k cl.exe. Zadejte prosím [zpracované zkopírujte](#preprocessed-repros) není-li.

## <a name="how-to-generate-a-repro"></a>Jak vygenerovat zkopírujte

Abychom sledovat zdroj problému, [dobrý zkopírujte](#what-makes-a-good-repro) je životně důležité. Před provedením kroků uvedených níže pro specifické druhy repros, zkuste zmenšit velikost mezi kód, který ukazuje, co nejvíce problém. Pokuste se vyloučit nebo minimalizovat závislosti, požadované hlavičky a knihovny a omezit – možnosti kompilátoru a definice preprocesoru použít, pokud je to možné.

Níže jsou uvedeny pokyny pro generování různé druhy repros, který budete používat pro sestavy různé druhy problémů.

### <a name="preprocessed-repros"></a>Předběžně zpracované repros

A *zpracované zkopírujte* je jeden zdrojový soubor, který ukazuje na problém, vytvořen z výstupu preprocesoru jazyka C pomocí **/P** – možnost kompilátoru na původní zdrojový soubor zkopírujte. Tato inlines zahrnuté hlavičky odebrání závislostí na další zdroje a soubory hlaviček a také řeší makra, #ifdefs a jinými preprocesoru příkazy, které může závisí na vašem místním prostředí.

> [!NOTE]
> Předběžně zpracované repros nejsou jako vhodný pro problémy, které může být výsledkem chyby v našich implementace standardní knihovny, protože jsme se často mají být nahrazeny naše nejnovější, probíhá implementace zobrazíte, zda již vyřešili jsme problém. V takovém případě nebudete předzpracování postup, a pokud nelze zmenšit tyto potíže k jeden zdrojový soubor, balíček kódu do souboru .zip nebo podobné, nebo zvažte použití projektu zkopírujte IDE. Další informace najdete v tématu [jiných repros](#other-repros).

#### <a name="to-preprocess-a-source-code-file"></a>Chcete-li předběžné zpracování souboru zdrojového kódu

1. Zaznamenat argumenty příkazového řádku, který je použit k vytvoření postup, jak je popsáno v [tak, aby odesílaly obsah příkazového řádku](#to-report-the-contents-of-the-command-line).

1. Otevřete **příkazový řádek vývojáře** odpovídající verze a konfigurace architektura sady Visual Studio používanou pro sestavení projektu.

1. Přejděte do adresáře, který obsahuje postup projektu.

1. V okně konzoly vývojáře příkazového řádku zadejte příkaz **cl /P** *argumenty* *filename.cpp*, kde *argumenty* je Seznam argumentů zachytit výše, a *filename.cpp* je název souboru zkopírujte zdroje. Tento příkaz replikuje příkazovým řádkem použitým pro postup, ale zastaví kompilace po průchodu preprocesoru a výstupy předběžně zpracované zdrojový kód a *filename*. i.

Pokud se předběžné zpracování C + +/ CX souboru se zdrojovým kódem, nebo můžete používáte funkci moduly C++, nejsou potřeba některé další kroky. Další informace najdete v tématu v níže uvedených částech.

Po vygenerování můžete předběžně zpracované souboru, je vhodné Ujistěte se, že stále repros problém pomocí předběžně zpracované souboru.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Potvrďte, že chyba stále repros předběžně zpracované souborem

1. V okně konzoly vývojáře příkazového řádku zadejte příkaz **cl** *argumenty* **/TP** *filename*.i říct cl.exe zkompilovat předběžně zpracované souboru jako C++ zdrojového souboru, kde *argumenty* je seznam argumentů zachytit výše, ale s žádným **/D** a **/I** argumenty odebrat, (protože budou již byly zahrnuty v předběžně zpracované souboru); a kde *filename*.i je název souboru předběžně zpracované.

1. Zkontrolujte, zda je problém reprodukovat.

Nakonec připojit předběžně zpracované zkopírujte *filename*.i do sestavy.

### <a name="preprocessed-ccx-winrtuwp-code-repros"></a>Zpracované C + +/ CX WinRT/UWP repros kódu

Pokud používáte C + +/ CX Sestavit vaše spustitelný soubor, nejsou některé další kroky potřebné k vytvoření a ověření předběžně zpracované zkopírujte.

#### <a name="to-preprocess-ccx-source-code"></a>Chcete-li předběžné zpracování C + +/ CX zdrojového kódu

1. Vytvoření předběžně zpracované zdrojového souboru, jak je popsáno v [pro předběžné zpracování souboru zdrojového kódu](#to-preprocess-a-source-code-file).

1. Hledání vygenerovaného _filename_.i souboru **#using** direktivy.

1. Zkontrolujte seznam všechny odkazované soubory. Vynechte oknech\*.winmd soubory, soubory platform.winmd a mscorlib.dll.

Abyste mohli ověřit, že soubor předběžně zpracované se stále shoduje s problém,

1. Vytvořte nový adresář pro předběžně zpracované soubor a zkopírujte jej do nového adresáře.

1. Zkopírujte soubory .winmd z vaší **#using** seznamu do nového adresáře.

1. Vytvořte soubor prázdný vccorlib.h v adresáři nové.

1. Upravte předběžně zpracované soubor odstraňte přitom všechny **#using** direktivy pro mscorlib.dll.

1. Upravte soubor předběžně zpracované změnit jakékoli absolutní cesty na právě úplné názvy souborů pro soubory zkopírovaný .winmd.

Potvrďte, že soubor předběžně zpracované se stále shoduje s problému, jak je uvedeno výše.

### <a name="preprocessed-c-modules-repros"></a>Předběžně zpracované repros moduly C++

Pokud používáte funkci moduly C++ compiler, nejsou některé jiné kroky potřebné k vytvoření a ověření předběžně zpracované zkopírujte.

#### <a name="to-preprocess-a-source-code-file-that-uses-a-module"></a>Předběžné zpracování souboru se zdrojovým kódem, který používá modul

1. Zaznamenat argumenty příkazového řádku, který je použit k vytvoření postup, jak je popsáno v [tak, aby odesílaly obsah příkazového řádku](#to-report-the-contents-of-the-command-line).

1. Otevřete **příkazový řádek vývojáře** odpovídající verze a konfigurace architektura sady Visual Studio používanou pro sestavení projektu.

1. Přejděte do adresáře, který obsahuje postup projektu.

1. V okně konzoly vývojáře příkazového řádku zadejte příkaz **cl /P** *argumenty* *filename.cpp*, kde *argumenty* je Seznam argumentů zachytit výše, a *filename.cpp* je název zdrojového souboru, který využívá modul.

1. Přejděte do adresáře, který obsahuje postup projekt, který vytvořené rozhraní modulu (.ifc výstup).

1. Zaznamenejte argumenty příkazového řádku, který je použit k vytvoření vaše rozhraní modulu.

1. V okně konzoly vývojáře příkazového řádku zadejte příkaz **cl /P** *argumenty* *modulename.ixx*, kde *argumenty* je Seznam argumentů zachytit výše, a *modulename.ixx* je název souboru, který vytvoří rozhraní modulu.

Po vygenerování můžete předběžně zpracované soubory, je vhodné zajistit stále repros problém pomocí předběžně zpracované souboru.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Potvrďte, že chyba stále repros předběžně zpracované souborem

1. V okně konzoly vývojáře změňte zpět na adresář, který obsahuje postup projektu.

1. Zadejte příkaz **cl** *argumenty* **/TP** *filename*.i, jak je uvedeno výše pro kompilaci předběžně zpracované souboru, jako by šlo C++ zdrojového souboru.

1. Potvrďte, že problém je stále opakuje předběžně zpracované souborem.

Nakonec připojit předběžně zpracované zkopírujte soubory (*filename*.i a *modulename*.i) společně s výstupem .ifc do sestavy.

### <a name="link-repros"></a>Odkaz repros

A *odkaz zkopírujte* je obsah generované linkeru adresář zadaný **odkaz\_zkopírujte** proměnné prostředí. Obsahuje artefaktů sestavení, která souhrnně ukazují problém, který nastane během odkaz, například back-end havárie zahrnující generování kódu v době propojování (LTCG) nebo linkeru havárií. Toto sestavení artefaktů jsou ty, které jsou potřebné jako vstup, aby lze problém reprodukovat linkeru. Zkopírujte odkaz můžete snadno vytvořit pomocí této proměnné prostředí, chcete-li povolit funkci generování předdefinované zkopírujte aplikace linkeru.

#### <a name="to-generate-a-link-repro"></a>Ke generování odkazu zkopírujte

1. Zaznamenat argumenty příkazového řádku, který je použit k vytvoření postup, jak je popsáno v [tak, aby odesílaly obsah příkazového řádku](#to-report-the-contents-of-the-command-line).

1. Otevřete **příkazový řádek vývojáře** odpovídající verze a konfigurace architektura sady Visual Studio používanou pro sestavení projektu.

1. V okně konzoly příkazového řádku vývojáře změňte adresář, který obsahuje postup projektu.

1. Zadejte **mkdir linkrepro** vytvořit adresář pro zkopírujte odkaz.

1. Zadejte příkaz **sadu odkaz\_zkopírujte = linkrepro** nastavit **odkaz\_zkopírujte** proměnnou prostředí k adresáři, který jste právě vytvořili.

1. Pro sestavení projektu postup v sadě Visual Studio, v okně konzoly příkazového řádku vývojáře, zadejte příkaz **devenv**. To zajistí, že hodnota **odkaz\_zkopírujte** proměnná prostředí je viditelná pro Visual Studio. Pro sestavení projektu na příkazovém řádku, použijte argumenty příkazového řádku zachytit výše duplicitní zkopírujte sestavení.

1. Sestavení projektu zkopírujte a potvrďte, že došlo k očekávané problému.

1. Pokud jste použili k provedení sestavení, zavřete Visual Studio.

1. V okně konzoly vývojáře příkazového řádku zadejte příkaz **sadu odkaz\_zkopírujte =** zrušte **odkaz\_zkopírujte** proměnné prostředí.

Nakonec balíček nepodařilo komprimací celý linkrepro adresáře do souboru .zip nebo podobné a jeho připojení k sestavě.

### <a name="other-repros"></a>Další repros

Pokud problém nelze zmenšit na jeden zdrojový soubor nebo předběžně zpracované zkopírujte a zkopírujte odkaz nevyžaduje žádný problém, jsme prozkoumat projektu IDE. Všechny pokyny o tom, jak vytvořit dobrý zkopírujte stále platí; Kód by měl být minimální a samostatná, problém by měl nastat v našem nejnovější nástroje a pokud je to relevantní, problém by neměl vidět v jiných kompilátory.

Vytvořte vaše zkopírujte jako minimální IDE projekt, pak balíček komprimací celou strukturu adresáře do souboru .zip nebo podobné a jeho připojení k sestavě.

## <a name="ways-to-send-your-report"></a>Způsoby odeslání sestavy

Existuje několik dobrý způsoby, jak získat sestavy do us. Můžete použít předdefinované sady Visual Studio [nahlásit problém nástroj](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017), nebo [Visual Studio Community vývojáře](https://developercommunity.visualstudio.com/) stránky. Získáte také přímo na stránkách k jednotlivým komunity vývojářů výběrem **názor produkt** tlačítko v dolní části této stránky. Výběr závisí na, zda chcete pomocí nástrojů integrovaných v prostředí IDE pro snímání obrazovky a uspořádání sestavy pro příspěvků na stránkách komunity vývojářů, nebo pokud chcete používat přímo na webu.

> [!NOTE]
> Bez ohledu na to, jak odeslat sestavy společnost Microsoft respektuje vaše soukromí. Společnost Microsoft se zavazuje dodržování všechny data o ochraně osobních údajů zákony a nařízení. Informace o tom, jak jsme považovat data, která můžete nám poslat najdete v tématu [Microsoft Visual Studio rodiny ochrany osobních údajů produktu](https://www.visualstudio.com/dn948229).

### <a name="use-the-report-a-problem-tool"></a>Pomocí sestavy nástroj problém

**Nahlásit problém** nástroj v sadě Visual Studio je způsob, jak uživatelům v sadě Visual Studio sestavy celou řadu problémů s několika kliknutí. Poskytuje jednoduché formulář, který můžete použít k určení podrobné informace o problému byla zjištěna a pak odeslat sestavy, aniž byste opustili prostředí IDE.

Vytváření sestav váš problém prostřednictvím **nahlásit problém** nástroj je snadný a pohodlný z prostředí IDE. Můžete k němu přístup ze záhlaví výběrem **odeslat zpětnou vazbu** ikonu vedle **Snadné spuštění** vyhledávací pole, nebo můžete najít v řádku nabídek v **pomoci**  >  **Odeslat názor** > **nahlásit problém**.

Když zvolíte-li nahlásit problém, nejprve vyhledejte komunity vývojářů pro podobné problémy. Pokud váš problém byla nahlášena před, upvote tématu a přidejte komentář s další podrobnosti. Pokud nevidíte podobný problém, vyberte **problém nové sestavy** tlačítko v dolní části zpětnou vazbu Visual Studio dialogové okno a postupujte podle kroků zprávu o problému.

### <a name="use-the-visual-studio-developer-community-pages"></a>Pomocí stránky komunity vývojářů Visual Studio

Visual Studio Community vývojáře stránky jsou jiné pohodlný způsob, jak odesílat zprávy o problémech a najděte řešení pro Visual Studio, C++ kompilátoru, nástroje a knihovny. [Visual Studio otázky](https://developercommunity.visualstudio.com/spaces/8/index.html) stránky je tam, kde k hlášení problémů s IDE nebo instalace. Pro problémy s používáním C++ kompilátoru, linkeru a další nástroje a knihovny, [C++ otázky](https://developercommunity.visualstudio.com/spaces/62/index.html) stránky.

Do komunity vývojářů je informační zpráva v horní části každé stránce vyhledávací pole, které můžete použít k vyhledání příspěvcích nebo témata, která odesílat zprávy o problémech, které vám podobnou. Můžete zjistit, že řešení a další užitečné informace týkající se váš problém již k dispozici v existující téma. Pokud někdo ohlásil ke stejnému problému před, upvote a komentáře v tomto tématu místo vytvoření nové sestavy problém.

Pokud váš problém nebyla hlášena před, vyberte **nahlásit problém** tlačítko vedle do vyhledávacího pole na stránce komunity vývojářů. Můžete být vyzváni k přihlášení k účtu sady Visual Studio a vyjádřete umožnit přístup k aplikaci komunity vývojářů k profilu. Pokud jste přihlášeni, přejdete přímo na stránku kde můžete nahlásit problém. Můžete zahrnout kódu zkopírujte a příkazového řádku, snímky obrazovky, odkazy na související diskusí a další informace, které si myslíte, že je relevantní a užitečné.

> [!TIP]
> Pro jiné druhy problémů může dojít v sadě Visual Studio, které nesouvisí se sada nástrojů (například uživatelského rozhraní problémy, porušený funkce IDE nebo dojde k obecné chybě), **nahlásit problém nástroj** může být obzvláště dobrý choice datu splatnosti k jeho snímek obrazovky jste možnosti a jeho schopnosti záznamu akcí uživatelského rozhraní, které vést k problému došlo. Tyto druhy chyby mohou být zaznamenány také na [komunity vývojářů](https://developercommunity.visualstudio.com/) lokality.

### <a name="reports-and-privacy"></a>Sestavy a ochrana osobních údajů

Ve výchozím nastavení **všechny informace v sestavách a všechny komentáře a odpovědi jsou veřejně viditelný**. Za normálních okolností jde výhody, protože umožňuje celé komunitě zobrazíte problémy, řešení a řešení, které jiní uživatelé našli. Pokud máte obavy o tom, jak veřejné, ochrany osobních údajů nebo duševní vlastnictví důvodů data nebo identity, ale máte možnosti.

Pokud máte obavy o odhalil svoji identitu, [vytvořit nový účet Microsoft](https://signup.live.com/) nezveřejňuje všechny podrobnosti o vás. Tento účet použijte pro vytvoření sestavy. 

**Nevkládejte nic, co chcete v názvu nebo obsah počáteční sestavy, který je veřejný soukromé.** Místo toho Všimněte si, že chcete odeslat podrobnosti soukromě v samostatných komentář. Pokud chcete mít jistotu, že sestavy se přesměruje příslušní lidé, obsahovat **cppcompiler** v seznamu témat sestavy problém. Po vytvoření sestavy problém je nyní možné určit, kdo může zobrazit odpovědi a přílohy.

#### <a name="to-create-a-problem-report-for-private-information"></a>Vytvoření sestavy problém pro soukromé informace

1. V sestavě, které jste vytvořili, zvolte **, přidejte komentář** k vytvoření vaší privátní popis problému.

1. v editoru odpovědět, použijte níže ovládací prvek rozevírací seznam **odeslání** a **zrušit** tlačítka k určení cílové skupiny v odpovědi. Tyto privátní odpovědi a všechny bitové kopie, odkazů nebo kód, který je v nich zahrnuta, můžete zobrazit pouze uživatelé, které zadáte. Zvolte **Viewable moderátorů a původní plakáty** omezit viditelnost zaměstnancům společnosti Microsoft a sami.

1. Přidejte popis a žádné jiné informace, Image a potřebné pro vaše zkopírujte přiložených souborů. Vyberte **odeslání** tlačítko soukromě odesílat výše uvedené informace.

   Všimněte si, že je 2GB omezení na připojené soubory a maximálně 10 souborů. Pro všechny větší nahrávání požádejte o adresu URL pro odeslání v privátní komentáře.

Všechny odpovědi v rámci tohoto komentáře mít stejné viditelnost s omezeným přístupem, které jste zadali. To platí i v případě, že ovládací prvek rozevírací seznam v odpovědi nezobrazuje stav zobrazení s omezeným přístupem správně.

Chcete-li udržovat vaše osobní údaje a zachovat vaše citlivé informace z veřejné zobrazení, Postarejte se prosím na odpovědi v rámci této omezené komentář zachovat veškerou interakci s Microsoft. Odpovědi na jiné připomínky může vést k omylem prozrazeny citlivé informace.

## <a name="how-to-report-a-c-documentation-issue"></a>Jak vytvářet sestavu problémem dokumentaci jazyka C++

Problémy GitHub používáme sledovat problémy hlášené v dokumentaci. Nyní můžete vytvořit Githubu problémy přímo ze stránky obsahu, která vám umožní komunikovat způsobem mnohem širší s zapisovače a týmy pro produkt. Pokud se problém s dokumentem, ukázku chybného kódu, matoucí vysvětlení, kritické vynechání nebo i právě překlepem, které můžete snadno dejte nám vědět. Přejděte do dolní části stránky a vyberte **Přihlaste se k dokumentaci váš názor**. Budete potřebovat pro vytvoření účtu GitHub, pokud již nemáte, ale až to uděláte, můžete zobrazit všechny problémy v naší dokumentaci, jejich stav a získat oznámení při změně pro problém, se kterým jste ohlásil. Další informace najdete v tématu [A nové zpětné vazby systému pochází k docs.microsoft.com](/teamblog/a-new-feedback-system-is-coming-to-docs).

Když vytvoříte problém dokumentaci na Githubu pomocí tlačítka dokumentace zpětnou vazbu, problém automaticky vyplněno některé informace o stránku, kterou jste vytvořili problém, abychom věděli, kde se nachází problém. Nemáte upravte prosím tyto informace. Podrobnosti o tom, co je pokazilo a podle potřeby navrhované opravu právě připojte. [Dokumentaci je open source](https://github.com/MicrosoftDocs/cpp-docs/), takže pokud chcete ve skutečnosti proveďte opravu a navrhnout sami, můžete to udělat. Další informace o tom, jak můžete přispívat do naší dokumentaci najdete v tématu naše [Contributing průvodce](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md) na Githubu.

